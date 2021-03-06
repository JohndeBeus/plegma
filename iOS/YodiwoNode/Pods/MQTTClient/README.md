MQTT-Client-Framework
=====================

an Objective-C native MQTT Framework http://mqtt.org

### Tested with

* mosquitto
* paho
* rabbitmq
* hivemq
* rsmb
* mosca
* vernemq
* emqtt
* moquette
* ActiveMQ
* Apollo
* CloudMQTT
* aws

### Howto

Add MQTTClient.framework from the dist directory to your IOS project,
use the dynamic library created in the MQTTFramework target,
or use the CocoaPod MQTTClient

[Documentation](MQTTClient/dist/documentation/html/index.html)

### Usage

Create a new client and connect to a broker:

```objective-c

\@interface MyDelegate : ... MQTTSessionDelegate>
...

MQTTSession *session = [[MQTTSession alloc]initWithClientId:@"client_id"]

// Set delegate appropriately to receive various events
// Set MQTTSessionDelegate // See MQTTSession.h for information on various handlers
// you can subscribe to.

[session setDelegate:self];

[session connectAndWaitToHost:@"host" port:1883 usingSSL:NO];

```

Subscribe to a topic:

```objective-c
[session subscribeToTopic:topic atLevel:MQTTQosLevelAtLeastOnce];
```

Add the following to receive messages for the subscribed topics
```objective-c
 - (void)newMessage:(MQTTSession *)session data:(NSData *)data onTopic:(NSString *)topic qos:(MQTTQosLevel)qos retained:(BOOL)retained mid:(unsigned int)mid
{

}
```

Publish a message to a topic:

```objective-c
[session publishAndWaitData:data
	                onTopic:@"topic"
	                 retain:NO
				        qos:MQTTQosLevelAtLeastOnce]
```

#### Framework

Framework build using instructions and scripts by Jeff Verkoeyen https://github.com/jverkoey/iOS-Framework

#### docs

Documentation generated with doxygen http://doxygen.org

#### Comparison MQTT Clients for iOS (incomplete)

|Wrapper|---|----|MQTTKit  |Marquette|Moscapsule|Musqueteer|MQTT-Client|MqttSDK|CocoaMQTT|
|-------|---|----|---------|---------|----------|----------|-----------|-------|---------|
|       |   |    |Obj-C    |Obj-C    |Swift     |Obj-C     |Obj-C      |Obj-C  |Swift    |
|Library|IBM|Paho|Mosquitto|Mosquitto|Mosquitto |Mosquitto |native     |native |native   |
