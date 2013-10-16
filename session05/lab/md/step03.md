## Create the client web app.

Create a directory _js_ and create a new file _main.js_ as we are going to create the client side web app for

~~~
<script src="js/main.js"></script>
~~~

In the file _main.js_ add

~~~
var isInitiator;

room = prompt("Enter room name:");

var socket = io.connect();

if (room !== "") {
  console.log('Joining room ' + room);
  socket.emit('create or join', room);
}

socket.on('full', function (room){
  console.log('Room ' + room + ' is full');
});

socket.on('empty', function (room){
  isInitiator = true;
  console.log('Room ' + room + ' is empty');
});

socket.on('join', function (room){
  console.log('Making request to join room ' + room);
  console.log('You are the initiator!');
});

socket.on('log', function (array){
  console.log.apply(console, array);
});
~~~



