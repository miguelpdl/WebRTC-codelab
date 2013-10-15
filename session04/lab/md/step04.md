## Add JS for the Peer Connection

We need some helper functions for those buttons created in the previous step, so edit that script element of the HTML docucment to add JS that will get and share local and remote descriptions: metadata about local media in [SDP](http://tools.ietf.org/html/rfc2327) format, and get / share ICE candidates. You should recognise these functions.

~~~
function gotLocalDescription(desc) {
  localPeerConnection.setLocalDescription(desc);
  trace('Offer from localPeerConnection \n' + desc.sdp);
  remotePeerConnection.setRemoteDescription(desc);
  remotePeerConnection.createAnswer(gotRemoteDescription);
}

function gotRemoteDescription(desc) {
  remotePeerConnection.setLocalDescription(desc);
  trace('Answer from remotePeerConnection \n' + desc.sdp);
  localPeerConnection.setRemoteDescription(desc);
}

function gotLocalCandidate(event) {
  trace('local ice callback');
  if (event.candidate) {
    remotePeerConnection.addIceCandidate(event.candidate);
    trace('Local ICE candidate: \n' + event.candidate.candidate);
  }
}

function gotRemoteIceCandidate(event) {
  trace('remote ice callback');
  if (event.candidate) {
    localPeerConnection.addIceCandidate(event.candidate);
    trace('Remote ICE candidate: \n ' + event.candidate.candidate);
  }
}
~~~
