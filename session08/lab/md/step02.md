## Create the client web app.

Now lets add the SimpleWebRTC library script details.

~~~
<script>
var webrtc = new SimpleWebRTC({
        localVideoEl: 'localVideo',
        remoteVideosEl: 'remoteVideo',
        autoRequestMedia: true
});

webrtc.on('readyToCall', function () {
        webrtc.joinRoom('My room name');
});
</script>
~~~