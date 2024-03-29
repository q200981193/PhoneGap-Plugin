# TB Object

TB Object lets you initialize the OpenTok API and set up exception event handling.

## Methods

[TB.addEventListener()](#addEventListener)  
[TB.initPublisher()](#initPublisher)  
[TB.initSession()](#initSession)  



<a id="addEventListener"></a>
### TB.addEventListener(type:String, listener:Function)

Example Code:  
```javascript
TB.addEventListener( 'exception', function(e){
  console.log( e.message );
});
```

Registers a method as an event listener for a specific event. The TB class dispatches exception events, defined by the
[ExceptionEvent](ExceptionEvent.md) object.

#### Parameters

**type** (String) — This string identifying the type of event. The TB object can only dispatch one type of event: an exception event. The only type of event the TB object dispatches is an 'exception' event.

**listener** (Function) — The function to be invoked when the TB object dispatches the event. An [ExceptionEvent](ExceptionEvent.md) object is passed into this function.


<a id="initPublisher"></a>
### TB.initPublisher( apiKey:String [, replaceElementId:String] [, properties:Object] )

Example Code:  
```javascript
var publisher = TB.initPublisher( '1127', 'myPublisherDiv', {name:"HelloWorld"} );
```

Initializes and returns a Publisher object. You can use this Publisher object to test the microphone and camera attached to the Publisher, and then pass this Publisher object to Session.publish() to publish a stream to a session.

You can only create one publisher object. Calling TB.initPublisher() more than once will fail silently.

#### Parameters

**apikey** (String) — The API key that TokBox provided you when you registered for the OpenTok API.
**replaceElementId** (String) - Optional. The id attribute of the existing DOM element that the Publisher video replaces. If you do not specify a replaceElementId, the application appends a new DOM element to the HTML body. 

**properties** (Object) — Optional. This is an optional object that contains the following properties (each of which are optional):

* **cameraName** (String) - The preferred camera position. When setting this property, if the change is possible, the publisher will use the camera with the specified position.  
Valid Inputs: 'Front' or 'Back'
* **height** (Number) — The desired height, in pixels, of the displayed Publisher video stream (default: 198). 
* **width** (Number) — The desired width, in pixels, of the displayed Publisher video stream (default: 264). 
* **name** (String) — A string that will be associated with this publisher’s stream. This string is displayed at the bottom of publisher videos and at the bottom of subscriber videos associated with the published stream. If you do not specify a value, the name is set to the device name.
* **publishAudio** (Boolean) — Whether to publish audio.
* **publishVideo** (Boolean) — Whether to publish video.


#### Return

**Publisher** ( [Publisher](publisher.md) ) — A Publisher object.


<a id="initSession"></a>
### TB.initSession(sessionId:String)

Example Code:  
```javascript
var session = TB.initSession( "1_mx..." )
```

Initializes and returns the local session object for a specified session ID.  
You connect to the session using the `connect()` method of the Session object returned by the `TB.initSession()` method. `TB.initSession()` does not initiate communications with the cloud, it simply initializes the Session object that you can use to connect (and to perform other operations once connected).

#### Parameters

**sessionId** (String) — Use the [Session ID](http://www.tokbox.com/opentok/api/tools/js/documentation/overview/session_creation.html) generated by your server that represents the session to which you are planning to connect.

#### Returns

**Session** ( [Session](session.md) ) - The session object through which all further interactions with the session will occur.


