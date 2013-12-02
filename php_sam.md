# SAM - Simple Asynchronous Messaging library for PHP

PHP_SAM is a PHP library which allows the usage of a number of different simple asynchronous messaging systems simply from PHP, one of which is MQTT.

This library is not only useful for building web applications, but can be a nice alternative to the Perl API for writing local shell scripts for those who like to write code that other people can understand.

{{youtube>jI-0b6XMM5E?medium}}
## Installation

SAM can be installed using PECL, however this has been reported to be unsuccessful in many situations. The cause of most problems when installing the library is compiling the C extensions used for protocols other than MQTT. The MQTT functionality requires only the PHP files which can just be downloaded and added to the PHP include directory.

Download links can be found [here](http://project-sam.awardspace.com/downloads.htm)

## Usage

To include the library:

''require(`<PHP-SAM folder name>`/php_sam.php');''

### Sending Messages

Once this has been included it is a trivial process to connect and send a message. This example shows how to get the average CPU usage over the last minute and send it over MQTT on the topic CPU (note you'll need to remove the space in the shell exec command if you copy and paste this code):

`<file php cpu_publish.php>`
require('SAM/php_sam.php');

//create a new connection object
$conn = new SAMConnection();

//start initialise the connection
$conn->connect(SAM_MQTT, array(SAM_HOST => `<Broker IP>`,
                                 SAM_PORT => 1883));

//while the connection exists
        while($conn)
        {
           //get the cpu usage using a shell command
           $cmd = "cat /proc/loadavg";
           
           $rawCpu=shell_exec ($cmd);

            $result=preg_match("/^\d+.\d+/", $rawCpu, $cpu);
            //if successful then send message
             if($result==1)
             {
                //create a new MQTT message with the output of the shell command as the body
                $msgCpu = new SAMMessage("$cpu[0]");

                //send the message on the topic cpu
                $conn->send('topic://cpu', $msgCpu);

                // print sent to the terminal
                echo "sent";

                //wait for a minute
                sleep(60);
            }
        }
`</file>`

### Receiving Messages

Subscribing to topics is a similarly simple process. In this example we will receive the messages sent by the above example and print them to the terminal:

`<file php cpu_subscribe.php>`
require('SAM/php_sam.php');

//create a new connection object
$conn = new SAMConnection();

//start initialise the connection
$conn->connect(SAM_MQTT, array(SAM_HOST => `<Broker IP>`,
                                 SAM_PORT => 1883));

//subscribe to topic cpu
    $subUp = $conn->subscribe('topic://cpu') OR die('could not subscribe');

//print confirmation to terminal
 echo "subscribed";

while($conn)
{
       //receive latest message on topic $subUp
       $msgUp = $conn->receive($subUp);

       //if there is a message
      if (!$msgUp->body=="")
      {
          //echo message to terminal
          echo $msgUp->body;
      }

      //wait 1s
      sleep(1);
}
`</file>`


