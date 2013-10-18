## Create the client web page

Now create a new client web app, and lets start by creating a new HTML5 document call it _wcl-session08.html_.

Add the client library in the head of the document.

~~~
<!DOCTYPE html>
<html>
<head>
<script src="http://simplewebrtc.com/latest.js"></script>
</head>

<body>

<div id="localVideo" muted></div>
<div id="remoteVideo"></div>

</body>

</html>
~~~