# Server Security Considerations

## File Permissions

Attention should be paid to the permissions of the various configuration and data files for the broker.  

Permissions should be restrictive enough to prevent unauthorized users from viewing or modifying these files.

This is especially true for broker implementations that store the passwords in clear text files.

## Process Ownership

If the broker must be started by the root user (not normally the case) then the broker should be configured to shed these privileges and run as a low privileged user.

## Network Considerations

### Value of Privileged Ports

If you are running MQTT on a server that is multi-user, you may wish to select a port numbered < 1024 (privileged port).  This precludes non-root users from binding to the port and spoofing your service.

### Selective Binding

Consider only binding your MQTT service to the specific interfaces that you require.  For example, bind your broker to 192.168.1.10 and 10.2.1.12 instead of 0.0.0.0.  This prevents unplanned access in situations where interfaces are later added.

If you are using a tunneling system for network encryption for all user - you may wish to only bind to the loopback address (127.0.0.1) to further increase security.

### Port Obfuscation

The MQTT "well known" ports 1883 and 8883 can be changed in order to obfuscate the connection.  This is not a very secure solution.  However, it can serve to add a bit of obscurity that may help avoid automated, opportunistic attacks such as worms.  If this technique is used, a port above 1024 should be selected so that it does not require elevated privileges to bind to the port selected.

### TCP Wrappers

TCP wrappers may be used by some implementations on some operating systems to control the stations that can connect to the broker.


