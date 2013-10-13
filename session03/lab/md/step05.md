## Add JS for the Peer Connection

Edit that script element of the HTML docucment to add JS that will get and share local and remote descriptions: metadata about local media in [SDP](http://tools.ietf.org/html/rfc2327) format, and will sort out the Hangup Button.

~~~

function gotLocalDescription(description){
  localPeerConnection.setLocalDescription(description);
  trace("Offer from localPeerConnection: \n" + description.sdp);
  remotePeerConnection.setRemoteDescription(description);
  remotePeerConnection.createAnswer(gotRemoteDescription);
}

function gotRemoteDescription(description){
  remotePeerConnection.setLocalDescription(description);
  trace("Answer from remotePeerConnection: \n" + description.sdp);
  localPeerConnection.setRemoteDescription(description);
}

function hangup() {
  trace("Ending call");
  localPeerConnection.close();
  remotePeerConnection.close();
  localPeerConnection = null;
  remotePeerConnection = null;
  hangupButton.disabled = true;
  callButton.disabled = false;
}

function gotRemoteStream(event){
  remoteVideo.src = URL.createObjectURL(event.stream);
  trace("Received remote stream");
}


~~~

 A deeper dive on this SDP stuff can be read in [An Offer/Answer Model with the Session Description Protocol (SDP)](http://tools.ietf.org/html/rfc3264).