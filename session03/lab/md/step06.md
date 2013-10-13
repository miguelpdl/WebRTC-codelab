## Get and share ICE candidates: network information.

Edit that script element of the HTML docucment to add JS for [ICE candidates](http://www.html5rocks.com/en/tutorials/webrtc/basics/#ice) which are needed for a networking framework which assists with connecting peers, such as two video chat clients we have in this session. Initially, ICE tries to connect peers directly, with the lowest possible latency, via UDP. In this process, servers have a single task: to enable a peer behind a NAT to find out its public address and port.

~~~

function gotLocalIceCandidate(event){
  if (event.candidate) {
    remotePeerConnection.addIceCandidate(new RTCIceCandidate(event.candidate));
    trace("Local ICE candidate: \n" + event.candidate.candidate);
  }
}

function gotRemoteIceCandidate(event){
  if (event.candidate) {
    localPeerConnection.addIceCandidate(new RTCIceCandidate(event.candidate));
    trace("Remote ICE candidate: \n " + event.candidate.candidate);
  }
}

~~~