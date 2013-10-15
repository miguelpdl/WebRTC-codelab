## Add Javascript to handle Start, Send and Stop Buttons

Edit that script element of the HTML document to add JS that will handle the Start Button.

~~~
function trace(text) {
  console.log((performance.now() / 1000).toFixed(3) + ": " + text);
}

function createConnection() {
  var servers = null;
  window.localPeerConnection = new webkitRTCPeerConnection(servers,
    {optional: [{RtpDataChannels: true}]});
  trace('Created local peer connection object localPeerConnection');

  try {
    // Reliable Data Channels not yet supported in Chrome
    sendChannel = localPeerConnection.createDataChannel("sendDataChannel",
      {reliable: false});
    trace('Created send data channel');
  } catch (e) {
    alert('Failed to create data channel. ' +
          'You need Chrome M25 or later with RtpDataChannel enabled');
    trace('createDataChannel() failed with exception: ' + e.message);
  }
  localPeerConnection.onicecandidate = gotLocalCandidate;
  sendChannel.onopen = handleSendChannelStateChange;
  sendChannel.onclose = handleSendChannelStateChange;

  window.remotePeerConnection = new webkitRTCPeerConnection(servers,
    {optional: [{RtpDataChannels: true}]});
  trace('Created remote peer connection object remotePeerConnection');

  remotePeerConnection.onicecandidate = gotRemoteIceCandidate;
  remotePeerConnection.ondatachannel = gotReceiveChannel;

  localPeerConnection.createOffer(gotLocalDescription);
  startButton.disabled = true;
  closeButton.disabled = false;
}

~~~

The syntax of RTCDataChannel is deliberately similar to WebSocket, with a `send()` method and a `message` event.

Notice the use of constraints.


2. Now edit that script element of the HTML docucment to add JS that will handle the Send Button

~~~
function sendData() {
  var data = document.getElementById("dataChannelSend").value;
  sendChannel.send(data);
  trace('Sent data: ' + data);
}
~~~

3. Edit that script element of the HTML docucment to add JS that will handle the Close Button

~~~
function closeDataChannels() {
  trace('Closing data channels');
  sendChannel.close();
  trace('Closed data channel with label: ' + sendChannel.label);
  receiveChannel.close();
  trace('Closed data channel with label: ' + receiveChannel.label);
  localPeerConnection.close();
  remotePeerConnection.close();
  localPeerConnection = null;
  remotePeerConnection = null;
  trace('Closed peer connections');
  startButton.disabled = false;
  sendButton.disabled = true;
  closeButton.disabled = true;
  dataChannelSend.value = "";
  dataChannelReceive.value = "";
  dataChannelSend.disabled = true;
  dataChannelSend.placeholder = "Press Start, enter some text, then press Send.";
}
~~~