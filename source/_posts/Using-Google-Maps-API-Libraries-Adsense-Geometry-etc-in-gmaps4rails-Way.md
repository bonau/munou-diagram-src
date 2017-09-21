---
title: 'Using Google Maps API Libraries (Adsense, Geometry, etc.) in gmaps4rails Way!'
tags: []
date: 2012-01-12 22:41:00
---

<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-rAETIAOI_iM/Tw7wh6vLyII/AAAAAAAADnU/o1ZqLOdx9aw/s640/%25E8%259E%25A2%25E5%25B9%2595%25E6%2588%25AA%25E5%259C%2596%25E5%25AD%2598%25E7%2582%25BA+2012-01-12+22%253A37%253A27.png)](http://2.bp.blogspot.com/-rAETIAOI_iM/Tw7wh6vLyII/AAAAAAAADnU/o1ZqLOdx9aw/s1600/%25E8%259E%25A2%25E5%25B9%2595%25E6%2588%25AA%25E5%259C%2596%25E5%25AD%2598%25E7%2582%25BA+2012-01-12+22%253A37%253A27.png)</div>
Google Maps API has it&#8217;s&nbsp;[official AdSense Library](http://code.google.com/intl/zh-TW/apis/maps/documentation/javascript/advertising.html), which allow you to add advertisement in your own map view easily. By using gmaps4rails, the recently popular map service library in RubyOnRails, some problems occurred if we write the javascript tag mention on the&nbsp;Google Maps API&nbsp;document. Why? because the google maps api version gmaps4rails used is not the newest version. Using the newest js library result in conflict between different versions of Google Maps API.

To avoid this, we can simply put {&nbsp;:libraries =&gt; [:adsense] } in :map_options, for example:

<pre>@google_maps_html = gmaps( :map_options =&gt; {</pre><pre>    :detect_location =&gt; true,
    <span style="color: #990000;">**:libraries =&gt; [:adsense],**</span>
    :center_on_user =&gt; true,
    :zoom =&gt; 15,
    :auto_zoom =&gt; false,
    :auto_adjust =&gt; true,
    :disableDefaultUI =&gt; true },
    :markers =&gt; { :data =&gt; @json })</pre><span style="font-family: monospace;"><span style="white-space: pre;">&nbsp;</span></span><div>And in our view, put javascript like this **<span style="color: #990000;">in the window load callback</span>**:

<pre>
  Gmaps.map.callback = function() {
    var adUnitDiv = document.createElement('div');
    var adUnitOptions = {
    format: google.maps.adsense.AdFormat.HALF_BANNER,
    position: google.maps.ControlPosition.TOP_CENTER,
    publisherId: '_<span style="background-color: white; color: #666666;">your publisher id</span>_',
    <span style="color: #990000;">**map: this.map,**</span>
    visible: true</pre><pre>  };
  var adUnit = new google.maps.adsense.AdUnit(adUnitDiv, adUnitOptions);
</pre>
&nbsp; &nbsp; &nbsp;
The :libraries key seems not appear on the&nbsp;[Google-Maps-for-Rails wiki](https://github.com/apneadiving/Google-Maps-for-Rails/wiki/). But after trace the source code, we don&#8217;t have to modify the plugin but just use it. Force working with the newest Google Maps API with gmaps4rails is not recommended.&nbsp;</div><div class="blogger-post-footer">![](https://blogger.googleusercontent.com/tracker/7273332692755259172-2277722151436231612?l=polar-dev.blogspot.com)</div>