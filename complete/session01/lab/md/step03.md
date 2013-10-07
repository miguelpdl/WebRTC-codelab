#Web Server

A web server will be needed, check to see if [Apache2](http://httpd.apache.org/) is already installed

~~~
$ which httpd
~~~

You can also try

- [MAMP](http://mamp.info/en/downloads) Mac
- [XAMPP](http://apachefriends.org/en/xampp.html) Mac / PC 

If you have Python installed just run 

~~~
python -m SimpleHTTPServer
~~~

in your application directory.

If you want to stay in the nodejs environment try

- [Express.js](http://expressjs.com/) a web application framework for nodejs 

Have a look at [Understanding Express.js](http://evanhahn.com/understanding-express-js/) for more information.

For those Ruby enthusiasts there's:

- [Sinatra](http://www.sinatrarb.com/intro.html)


In order to avoid having to 'allow' the camera every time you reload the page in the browser you could start a [secure HTTPS server](http://www.piware.de/2011/01/creating-an-https-server-in-python/) but there's special bonus points if you can make that happen.