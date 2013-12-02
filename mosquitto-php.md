''mosquitto-php'' let you use the Mosquitto MQTT library with PHP.

See https://github.com/mgdm/Mosquitto-PHP for the full API documentation.

# Publishing to a topic

	:::php
	<?php
	
	define('BROKER', 'localhost');
	define('PORT', 1883);
	define('CLIENT_ID', "pubclient_" + getmypid());
	
	$client = new Mosquitto\Client(CLIENT_ID);
	$client->connect(BROKER, PORT, 60);
	
	while ($client->loop() == 0) {
		$message = "Test message at " . date("Y-m-d H:i:s");
		$client->publish('test/foo/bar', $message, 0, false);
		$client->loop();
		sleep(1);
	}


# Subscribing to a topic

All the callbacks here are actual functions, though they can be closures, methods, etc.

	:::php
	<?php
	define('BROKER', 'localhost');
	define('PORT', 1883);
	define('CLIENT_ID', "pubclient_" + getmypid());
	
	$client = new Mosquitto\Client(CLIENT_ID);
	$client->onConnect('connect');
	$client->onDisconnect('disconnect');
	$client->onSubscribe('subscribe');
	$client->onMessage('message');
	$client->connect(BROKER, PORT, 60);
	$client->subscribe('#', 1); // Subscribe to all messages
	
	$client->loopForever();
	
	function connect($r) {
		echo "Received response code {$r}\n";
	}
	
	function subscribe() {
		echo "Subscribed to a topic\n";
	}
	
	function message($message) {
		printf("Got a message on topic %s with payload:\n%s\n", $message->topic, $message->payload);
	}
	
	function disconnect() {
		echo "Disconnected cleanly\n";
	}

