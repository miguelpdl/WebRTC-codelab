## HTML5 document with two text areas and associated buttons

1. To start off this session, create a new HTML document, and add  with two text areas and associated buttons for the lab.

Call it wcl-session04.html

~~~
<!DOCTYPE html>
<html>

<head>

<meta name="keywords" content="JavaScript, WebRTC" />
<meta name="description" content="WebRTC codelab" />
<meta name="viewport" content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1">

<title>WebRTC codelab: Session 04</title>

<style>
</style>

</head>

<body>

        <textarea id="dataChannelSend" disabled placeholder="Press Start, enter some text, then press Send."></textarea>
        <textarea id="dataChannelReceive" disabled></textarea>

  <div id="buttons">
    <button id="startButton">Start</button>
    <button id="sendButton">Send</button>
    <button id="closeButton">Stop</button>
  </div>

</body>

</html>
~~~
