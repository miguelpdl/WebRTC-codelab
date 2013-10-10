##Create a blank HTML5 document 

To start of this session create a bare-bones HTML document. Call it wcl-step01.html

~~~
<!DOCTYPE html>
<html>

<head>

<meta name="keywords" content="JavaScript, WebRTC" />
<meta name="description" content="WebRTC codelab" />
<meta name="viewport" content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1">

<title>WebRTC codelab: Step 1</title>

<!-- When we finish the codelab we'll move CSS and JavaScript to separate files -->

<!-- CSS will go here -->
<style>
</style>

</head>

<body>

<!-- HTML will go here -->

<!-- JavaScript will go here -->
<script>
</script>

</body>

</html>

~~~

### Serve the HTML page from a local web server

Now we want you to open that from the localhost web server running on your machine.

Let's start with the Python option, make sure you are in the same directory as the recently stored wcl-step01.html file.

~~~
python -m SimpleHTTPServer
~~~

It should say Serving HTTP on [0.0.0.0 port 8000](http://localhost:8000) and you should see a directory listing now click on wcl-step01.html.

Now let's try Apache2 on MAC OS X and Ubuntu.

Have a look at [Setting Up and Starting the Apache Web Server in OS X](http://osxdaily.com/2012/09/02/start-apache-web-server-mac-os-x).

~~~
$ cd /Applications/Utilities/ 
~~~

Check that your user apache2 conf file is in place.

~~~
$ ls /etc/apache2/users/USERNAME.conf 

//if not then create one
$ sudo vim /etc/apache2/users/USERNAME.conf 

~~~

~~~
<Directory "/Users/USERNAME/Sites/">
Options Indexes Multiviews
AllowOverride AuthConfig Limit
Order allow,deny
Allow from all
</Directory>
~~~

~~~
//Check to see if you have the Sites directory in your home folder
$ mkdir /Users/USERNAME/Sites
~~~

Make sure to edit the directory path USERNAME to the your username !

Next, the web server can be started with the following command.

~~~
$ sudo apachectl start
~~~

Launch your Chrome browser and go to [http://127.0.0.1](http://127.0.0.1) to verify the server is running, you will see an "It Works!" message. [http://localhost](http://localhost) should work too.

You can now also visit http://127.0.0.1/~USERNAME/ to see the contents of whatever is stored in the user ~/Sites/ directory. If this is a fresh install then more than likely you'll see nothing at all!

Add your newly created wcl-step01.html file to the directory /Users/USERNAME/Sites and see what pops up. Well should be blank, but View Page Source.

If you are not seeing anything, you may need to [enable Web Sharing](http://superuser.com/questions/358944/why-is-mac-os-x-lion-apache-documentroot-usr-htdocs).

For those of you working with Ubuntu 12.04 have a look at [HTTPD - Apache2 Web Server](https://help.ubuntu.com/lts/serverguide/httpd.html).