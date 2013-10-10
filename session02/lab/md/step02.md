##Enable the WebRTC API getUserMedia()

1. Add a [video element](http://www.w3.org/wiki/HTML/Elements/video) to your page.

~~~
<video id="FIGURE_IT_OUT"></video>
~~~


2. Add the following JavaScript to the script element on your page, to enable getUserMedia() to set the source of the video from the web cam:

~~~
        navigator.getUserMedia = navigator.getUserMedia ||
          navigator.webkitGetUserMedia || navigator.mozGetUserMedia;

        var constraints = {video: true};

        function successCallback(localMediaStream) {
          window.stream = localMediaStream; // stream available to console
          var video = document.querySelector("video");
          video.src = window.URL.createObjectURL(localMediaStream);
          video.play();
        }

        function errorCallback(error){
          console.log("navigator.getUserMedia error: ", error);
        }

        navigator.getUserMedia(constraints, successCallback, errorCallback);
~~~

3. View your page from _localhost_.

### Explanation

'getUserMedia' is called like this:

~~~
    navigator.getUserMedia(constraints, successCallback, errorCallback);
~~~

The constraints argument allows us to specify the media to get, in this case video only:

~~~
    var constraints = {"video": true}
~~~

If successful, the video stream from the webcam is set as the source of the video element:

~~~
    function successCallback(localMediaStream) {
      window.stream = localMediaStream; // stream available to console
      var video = document.querySelector("video");
      video.src = window.URL.createObjectURL(localMediaStream);
      video.play();
    }
~~~