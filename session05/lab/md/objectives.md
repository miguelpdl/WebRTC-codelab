## Set up a signaling server and exchange messages 

RTCPeerConnection instances need to exchange metadata in order to set up and maintain a WebRTC 'call':

* Candidate (network) information.
* _Offer_ and _answer_ messages providing information about media such as resolution and codecs.

In other words, an exchange of metadata is required before peer-to-peer audio, video or data streaming can take place. This process is called _signaling_.

In the examples already completed, the 'sender' and 'receiver' RTCPeerConnection objects are on the same page, so signaling is simply a matter of passing objects between methods.

In a real world application, the sender and receiver RTCPeerConnections are not on the same page, and we need a way for them to communicate metadata.

For this, we use a signaling server: a server that can exchange messages between a WebRTC app (client) running in one browser and a client in another browser. The actual messages are stringified JavaScript objects.

**To reiterate: metadata exchange between WebRTC clients (via a signaling server) is required for RTCPeerConnection to to do audio, video and data streaming (peer to peer).**

In this session we'll build a simple Node.js signaling server, using the socket.io Node module and JavaScript library for messaging. 

Experience of [Node.js](http://nodejs.org/) and [socket.io](http://socket.io/) will be useful, but not crucial -- the messaging components are very simple. 

In this example, we will build 

- build the server (the Node app) called _server.js_
- create the client web page called _index.html_.
- create the client web app called _main.js_.
- view the client page from the url location _localhost:2013_.
- Carry out some bonus tasks for the session.
