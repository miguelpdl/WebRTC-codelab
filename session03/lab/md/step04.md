## Add JS for Local Video and Audio streams

Add to the script element of the HTML document some JS for the Start and Call buttons.

~~~
function trace(text) {
  console.log((performance.now() / 1000).toFixed(3) + ": " + text);
}

function gotStream(stream){
  trace("Received local stream");
  localVideo.src = URL.createObjectURL(stream);
  localStream = stream;
  callButton.disabled = false;
}

function start() {
  trace("Requesting local stream");
  startButton.disabled = true;
  navigator.getUserMedia = navigator.getUserMedia ||
    navigator.webkitGetUserMedia || navigator.mozGetUserMedia;
  navigator.getUserMedia({audio:true, video:true}, gotStream,
    function(error) {
      trace("navigator.getUserMedia error: ", error);
    });
}

function call() {
  callButton.disabled = true;
  hangupButton.disabled = false;
  trace("Starting call");

  if (localStream.getVideoTracks().length > 0) {
    trace('Using video device: ' + localStream.getVideoTracks()[0].label);
  }
  if (localStream.getAudioTracks().length > 0) {
    trace('Using audio device: ' + localStream.getAudioTracks()[0].label);
  }

  var servers = null;

  localPeerConnection = new webkitRTCPeerConnection(servers);
  trace("Created local peer connection object localPeerConnection");
  localPeerConnection.onicecandidate = gotLocalIceCandidate;

  remotePeerConnection = new webkitRTCPeerConnection(servers);
  trace("Created remote peer connection object remotePeerConnection");
  remotePeerConnection.onicecandidate = gotRemoteIceCandidate;
  remotePeerConnection.onaddstream = gotRemoteStream;

  localPeerConnection.addStream(localStream);
  trace("Added localStream to localPeerConnection");
  localPeerConnection.createOffer(gotLocalDescription);
}


~~~