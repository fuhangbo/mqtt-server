# SSH Tunnels

One approach that can be used to secure protocols that do not have native encryption is to tunnel them over a known secure protocol.

This can be a VPN protocol like IPSec or it can be a secure general purpose protocol like HTTPS/TLS or SSH.

In this post, we will discuss tunneling MQTT over SSH in a simple and a more advanced configuration.

## What is SSH?

SSH is a great protocol that is essentially a drop-in replace for many older, insecure protocols.

For example, SSH can(should) replace telnet, FTP, rlogin, rsh, rcp, etc, etc. It's like the secure Swiss Army knife of protocols.

## Simple Configuration with Interactive Password

For the most basic implementation of SSH tunneling all you need is SSH installed on both devices.  The end with the service that you want to connect to must offer the SSH service and you need an SSH client on the end you wish to connect from.  You will also, obviously need an account on the server side.

Once you have this and have tested that the basic functionality works, we will need to set up the tunnel.  For this section we will assume that you are using the default ports for SSH (22) and MQTT (1883).  We will also need to select another port for the local tunnel endpoint - let's use 22883 (which is officially unassigned (IANA) yet, you should check your local machine first to make sure it is not in use (i.e., netstat -an)).

Now we need to enter only one command to set this up:

''ssh -f -L 22883:127.0.0.1:1883 SSHusername@MQTT -N''

'-f' means to fork into the background.

'-L' means to do a local tunnel.

'22883' is our local port number.

'127.0.0.1' is the destination host from the perspective of the tunnel destination.

'1883' is the MQTT port on the destination server.

'SSHusername' is the username that you use to login to the MQTT server's SSH service.

'MQTT' is the name or IP address of the MQTT server.

'-N' tells ssh not to run a command on the remote server.

You will be prompted for your password (for the SSH connection).

Now, if you connect to MQTT from this system using the localhost address and a port of 22883 like this:

''mosquitto_sub -h 127.0.0.1 -p 22883 -u dan -P password -t 'test/#'''

You will connect to the MQTT broker on your MQTT server - but this time over a secure (encrypted and authenticated) SSH connection.

The problem with what we have so far it that we need to be at the client to set up the tunnel - which is fine if it is our PC - but if it is a server, we probably need a solution that doesn't need an interactive password - but one that also does not sacrifice security.  This is what we will look at next.

## Configuration to Support Key-based Authentication

SSH supports a wide variety of authentication natively and many more via the PAM (plugable authentication) interface.  We are going to enable the public/private key based authentication so that we can login to our MQTT server over SSH without providing a password - or leaving a password stored in plain-text.

Since our purpose here is to make this work in an unattended manner, we will not give a passphrase for our private key - keep in mind that this can lead to security problems - do not re-use this key for other purposes/servers and apply additional server side controls.

To generate our key, on the client side, run:

''ssh-keygen''

Then accept the defaults. If you want a passphrase - this would be the time to add one. Now run:

''ssh-copy-id username@host''

This copies your key into the .ssh/authorized_keys file.

If you didn't enter a passphrase - as I mentioned before - you'll want to provide additional security on the server side.

Some of those additional server-side controls might be to lock down what logins that use this key can do.  To do this, you can go to the server and edit the .ssh/authorized_keys file adding some options to the beginning of it:

''from="192.168.1.*",no-pty,permitopen="127.0.0.1:1883",command="/bin/false" ssh-rsa AAAAB....''

This limits logins to the 192.168.1.x network, declines to assign a pty, limits the forwarding to the localhost on the MQTT port, and runs the command "/bin/false" on login.  The point here being to lock down what the passwordless key can do to those things that you want that key to do anyway (no interactive logins, no sftp logins, no tunneling to other servers, no reusing the key on other servers, etc.   The ssh/sshd man pages have more information on other settings that may be useful for enhancing your security.

Once this is all done and you are satisfied with the security - just go back and run your ssh comand from above and you will not be prompted for a password (unless you set a key passphrase).  Now you should be able to use the tunnel as before, but with no password required.

(This was originally published as a blog post: [here](http://diabolicalws.blogspot.com/2012/02/tunneling-mqtt-over-ssh.html) )
