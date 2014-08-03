## HTML5 Video + Audio Recording Angular Module

This project is using webRTC's getUserMedia() spec to record audio and video both in the client side
and upload as chunks to the server, current project support latest versions of Opera and Chrome and 
hoping to provide support for Firefox in near future.


###Usage 

linking script files 

```html
<script type="text/javascript" src="angularjs.min.js"></script>
<script type="text/javascript" src="js/modules/vaRecorder/ngCamRecorder.js"></script>
<script type="text/javascript" src="js/App.js"></script>

<script type="text/javascript" src="js/modules/vaRecorder/recorder.js"></script>
<script type="text/javascript" src="js/modules/vaRecorder/whammy.js"></script>
<script type="text/javascript" src="js/modules/vaRecorder/VIRecorder.js"></script>
```

Initializing 

```html

<html ng-app="testapp"> 
<head>
	<title></title>
	<link rel="stylesheet" type="text/css" href="js/modules/vaRecorder/css/virecorder.css">
</head>
<body ng-controller="testcontroller">	
		
		<!-- here is how you use the module it -->
		<ngcamcecorder configuration="camconfiguration"></ngcamcecorder>
		

		<button ng-click = "camconfiguration.init()" >Recroding init</button>
		<img ng-src="{{camconfiguration.output.recordingthumb}}" />

		
		<script type="text/javascript" src="angularjs.min.js"></script>
		<script type="text/javascript" src="js/modules/vaRecorder/ngCamRecorder.js"></script>
		<script type="text/javascript" src="js/App.js"></script>

		<script type="text/javascript" src="js/modules/vaRecorder/recorder.js"></script>
		<script type="text/javascript" src="js/modules/vaRecorder/whammy.js"></script>
		<script type="text/javascript" src="js/modules/vaRecorder/VIRecorder.js"></script>
</body>
</html>
```



###Here is App.js

```html
var mainapp = angular.module("testapp" , ['ngCamRecorder']);

mainapp.controller("testcontroller" , function ($scope) {

    var configuration  = {
            init : $scope.initiateRecord,
            recConf:{   
                recorvideodsize : 0.4, 
                webpquality     : 0.7, 
                framerate       : 15,  
                videoWidth      : 500,
                videoHeight     : 375,            
            },

            recfuncConf :{
                showbuton : 2000,
                url : "http://localhost/ngCam/js/modules/vaRecorder/php/fileupload.php",
                chunksize : 1048576,
                recordingtime : 17,
                requestparam : "filename",
                videoname : "video.webm",
                audioname : "audio.wav", 
            },

            output :{
                recordingthumb : null,
               	recordinguploaded : function(){
               		alert("uploaded");
               	}
            },

            recordingerror : function(){
            	alert("browser not compatible");
            }      
    }
	$scope.camconfiguration = configuration;
});


```

![Example](http://imalhasaranga.com/wp-content/uploads/2014/08/recorder.png "Example, how it look")

###Server Side Code
I have used php but you can use any server side language


###More

Basic Component is [Html5_Video_Audio_Recorder](https://github.com/imalhasaranga/Html5_Video_Audio_Recorder

####This project is an experiment, and this will work Only for Chrome, Opera so all are invited to contribute....
