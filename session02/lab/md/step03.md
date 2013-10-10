## Bonus points

1. Inspect the stream object from the console.
2. What does `stream.getVideoTracks()` return?
   Have a look at the [W3C specs for getUserMedia()](http://www.w3.org/TR/mediacapture-streams/#methods) to see why this is returned.
3. Try calling `stream.stop()`.
   Have a look at the [W3C specs for getUserMedia()](http://www.w3.org/TR/mediacapture-streams/#methods-1) to see why this worked.
4. Look at the constraints object: what happens when you change it to `{audio: true, video: true}`?
5. What size is the video element?  How can you get the video's natural size from JavaScript? Use the Chrome Dev Tools to check. Use CSS to make the video full width. How would you ensure the video is no higher than the viewport?
6. Try adding CSS filters to the video element (more ideas [here](http://html5-demos.appspot.com/static/css/filters/index.html)).
7. Try changing constraints: see the sample at [simpl.info/getusermedia/constraints](https://simpl.info/getusermedia/constraints/).

For example:

~~~
    video {
      filter: hue-rotate(180deg) saturate(200%);
      -moz-filter: hue-rotate(180deg) saturate(200%);
      -webkit-filter: hue-rotate(180deg) saturate(200%);
    }
~~~
