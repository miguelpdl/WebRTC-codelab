#Programming Environment

The programming environment is mainly going to be [node.js](http://nodejs.org/download/) which uses JavaScript and a programming model that is event driven in nature, especially the way it handles I/O, and is great in creating concurrent server applications.

![StackOverflow](http://www.hanselman.com/blog/content/binary/WindowsLiveWriter/Hans.NETMVCJeffAtwoodandhistechnicalteam_1349C/stackoverflow-logo-250_3.png) say 

1. Web development in a dynamic language (JavaScript) on a VM that is incredibly fast (V8). It is much faster than Ruby, Python, or Perl.

2. Ability to handle thousands of concurrent connections with minimal overhead on a single process.

3. JavaScript is perfect for event loops with first class function objects and closures. People already know how to use it this way having used it in the browser to respond to user initiated events.

4. A lot of people already know JavaScript, even people who do not claim to be programmers. It is arguably the most popular programming language.

5. Using JavaScript on a web server as well as the browser reduces the impedance mismatch between the two programming environments which can communicate data structures via JSON that work the same on both sides of the equation. Duplicate form validation code can be shared between server and client, etc.

For this code lab we will prgramme against version V0.10.20

Will also have to install the modules [socket.io](http://socket.io) and [node-static](https://npmjs.org/package/node-static). There is an easy way to install these via the command line tool npm, which is available once node.js has been installed on your machine. 

~~~
$ npm install socket.io
~~~
[Socket.io](https://npmjs.org/package/socket.io) makes [WebSockets](http://www.websocket.org/), as such full-duplex single socket connection over which messages can be sent between client and server available in all browsers. It also enhances WebSockets by providing built-in multiplexing, horizontal scalability, automatic JSON encoding/decoding, and more.

~~~
$ npm install node-static
~~~ 

 [node-static](https://npmjs.org/package/node-static) is a simple, RFC2616 compliant HTTP static-file streaming module, with built-in caching for nodejs.

For bonus points later in the code lab it might worth looking at some nodejs hosting providers. Free trials and easy deployment options for Node are available on several hosting sites including [nodejitsu](http://www.nodejitsu.com), [heroku](http://www.heroku.com) and [nodester](http://www.nodester.com).
