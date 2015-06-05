## Node server application

The Node server application in this step has two tasks.

- To act as a messaging intermediary.
- To manage WebRTC video chat 'rooms'.

 This simple WebRTC application will only permit a maximum of two peers to share a room.

Create a file called _server.js_ and add some variables we need for this session.

~~~
var static = require('node-static');
var http = require('http');
var file = new(static.Server)();

var app = http.createServer(function (req, res) {
  file.serve(req, res);
}).listen(2013);

var io = require('socket.io').listen(app);
~~~

Now in the same _server.js_ file add the base messaging intermediary functions.

~~~
io.sockets.on('connection', function (socket){

  // convenience function to log server messages on the client
        function log(){
                var array = [">>> Message from server: "];
          for (var i = 0; i < arguments.length; i++) {
                array.push(arguments[i]);
          }
            socket.emit('log', array);
        }

        socket.on('message', function (message) {
                log('Got message:', message);
    // for a real app, would be room only (not broadcast)
                socket.broadcast.emit('message', message);
        });

~~~

Next on a "create or join" we must manage the WebRTC video chat 'rooms', so add the methods to handle this.

~~~
       socket.on('create or join', function (room) {
                var clients = io.sockets.adapter.rooms[room]; 
				var numClients = (typeof clients !== 'undefined') ? 
				Object.keys(clients).length : 0;

                log('Room ' + room + ' has ' + numClients + ' client(s)');
                log('Request to create or join room ' + room);

                if (numClients === 0){
                        socket.join(room);
                        socket.emit('created', room);
                } else if (numClients === 1) {
                        io.sockets.in(room).emit('join', room);
                        socket.join(room);
                        socket.emit('joined', room);
                } else { // max two clients
                        socket.emit('full', room);
                }
                socket.emit('emit(): client ' + socket.id + ' joined room ' + room);
                socket.broadcast.emit('broadcast(): client ' + socket.id + ' joined room ' + room);

        });

});
~~~
