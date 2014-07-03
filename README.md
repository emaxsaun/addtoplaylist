JW Player Add to Playlist
==========

This is a small example for use with the JW Player. It allows playlist items to be added to a playlist, while trying to work around the limitation of the player having to reload when a new item is added with a near work-around.

### [Demo](http://www.pluginsbyethan.com/github/addtoplaylist.html)

Implementation:
==========

You need the following script above your JW Player embed instance:

<pre>
var addVideo = function(videoUrl, videoThumb, videoTitle, videoDesc){
	var playlist = jwplayer().getPlaylist();
	var newItem = {
		file: videoUrl,
		image: videoThumb,
		title: videoTitle,
		description: videoDesc
	};
	if(jwplayer().getState() != 'PLAYING'){
		playlist.push(newItem);
		jwplayer().load(playlist);
	} else {
		playlist.push(newItem);
		var curpos = jwplayer().getPosition();
		jwplayer().onPlaylist(function(){
			jwplayer().seek(curpos);
		});
		jwplayer().load(playlist).onPlaylist(function(){
			jwplayer().seek(curpos);
		});
	}
}
</pre>

Then, embed the player, with a playlist, just like normal.

<pre>
jwplayer('myElement').setup({
      playlist: [{
        file: 'http://content.bitsontherun.com/videos/3XnJSIm4-640.mp4',
        image: 'http://assets-jp.jwpsrv.com/thumbs/3XnJSIm4-640.jpg',
        title: 'Sintel Trailer',
        description: 'Sintel is a fantasy CGI movie from the Blender Open Movie Project.'
      },{
        file: 'http://content.bitsontherun.com/videos/i8oQD9zd-640.mp4',
        image: 'http://assets-jp.jwpsrv.com/thumbs/i8oQD9zd-640.jpg',
        title: 'Tears of Steel Trailer',
        description: 'A complete open pipeline was used to produce this visual effect film.'
      },{
        file: 'http://content.bitsontherun.com/videos/bkaovAYt-640.mp4',
        image: 'http://assets-jp.jwpsrv.com/thumbs/bkaovAYt-640.jpg',
        title: 'Big Buck Bunny Trailer',
        description: 'This animated film is made using free and open source software.'
      },{
        file: 'http://content.bitsontherun.com/videos/kaUXWqTZ-640.mp4',
        image: 'http://assets-jp.jwpsrv.com/thumbs/kaUXWqTZ-640.jpg',
        title: 'Elephants Dream Trailer',
        description: 'This is the worlds first open movie, made entirely with Blender.'
      }],
      width: 700,
      height: 240,
      listbar: {
        position: 'right',
        size: 280
      }
    });
</pre>

Then, after your JW Player embed instace, this is needed as well, for the buttons to add the items to the playlist:

<pre>
&lt;p&gt;Click on one of the links below to add an item to the player:&lt;/p&gt;
&lt;ul&gt;
&lt;li&gt;&lt;a href=&quot;#&quot; onclick=&quot;addVideo('http://content.bitsontherun.com/videos/yj1shGJB-60830.mp4', 'http://content.bitsontherun.com/thumbs/yj1shGJB-320.jpg', 'Sintel trailer', 'Sintel is a fantasy CGI movie from the Blender Open Movie Project.'); return false;&quot;&gt;Add the Sintel trailer to the playlist&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href=&quot;#&quot; onclick=&quot;addVideo('http://content.bitsontherun.com/videos/i8oQD9zd-kNspJqnJ.mp4', 'http://content.bitsontherun.com/thumbs/i8oQD9zd-640.jpg', 'Tears of Steel Trailer', 'A complete open pipeline was used to produce this visual effect film.'); return false;&quot;&gt;Add the Tears of Steel trailer to the playlist&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href=&quot;#&quot; onclick=&quot;addVideo('http://content.bitsontherun.com/videos/bkaovAYt-640.mp4', 'http://assets-jp.jwpsrv.com/thumbs/bkaovAYt-640.jpg', 'Big Buck Bunny Trailer', 'This animated film is made using free and open source software.'); return false;&quot;&gt;Add the Big Buck Bunny trailer to the playlist&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href=&quot;#&quot; onclick=&quot;addVideo('http://content.bitsontherun.com/videos/kaUXWqTZ-640.mp4', 'http://assets-jp.jwpsrv.com/thumbs/kaUXWqTZ-640.jpg', 'Elephants Dream Trailer', 'This animated film is made using free and open source software.'); return false;&quot;&gt;Add the Elephants Dream trailer to the playlist&lt;/a&gt;&lt;/li&gt;
&lt;/ul&gt;
</pre>

Full Example:
==========
<pre>
&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
&lt;title&gt;Add to Playlist&lt;/title&gt;
&lt;script src=&quot;http://p.jwpcdn.com/6/9/jwplayer.js&quot;&gt;&lt;/script&gt;
&lt;style type=&quot;text/css&quot;&gt;
body {
	font-family: sans-serif;
	margin: 0;
	padding: 0;
}
a {
	color:#000000;
}
ul,li {
	list-style:none;
}
&lt;/style&gt;
&lt;script type=&quot;text/javascript&quot;&gt;
var addVideo = function(videoUrl, videoThumb, videoTitle, videoDesc){
	var playlist = jwplayer().getPlaylist();
	var newItem = {
		file: videoUrl,
		image: videoThumb,
		title: videoTitle,
		description: videoDesc
	};
	if(jwplayer().getState() != &quot;PLAYING&quot;){
		playlist.push(newItem);
		jwplayer().load(playlist);
	} else {
		playlist.push(newItem);
		var curpos = jwplayer().getPosition();
		jwplayer().onPlaylist(function(){
			jwplayer().seek(curpos);
		});
		jwplayer().load(playlist).onPlaylist(function(){
			jwplayer().seek(curpos);
		});
	}
}
&lt;/script&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;div id=&quot;myElement&quot;&gt;&lt;/div&gt;
&lt;script&gt;
jwplayer(&quot;myElement&quot;).setup({
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;playlist: [{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;file: &quot;http://content.bitsontherun.com/videos/3XnJSIm4-640.mp4&quot;,
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;image: &quot;http://assets-jp.jwpsrv.com/thumbs/3XnJSIm4-640.jpg&quot;,
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;title: &quot;Sintel Trailer&quot;,
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;description: &quot;Sintel is a fantasy CGI movie from the Blender Open Movie Project.&quot;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;file: &quot;http://content.bitsontherun.com/videos/i8oQD9zd-640.mp4&quot;,
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;image: &quot;http://assets-jp.jwpsrv.com/thumbs/i8oQD9zd-640.jpg&quot;,
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;title: &quot;Tears of Steel Trailer&quot;,
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;description: &quot;A complete open pipeline was used to produce this visual effect film.&quot;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;file: &quot;http://content.bitsontherun.com/videos/bkaovAYt-640.mp4&quot;,
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;image: &quot;http://assets-jp.jwpsrv.com/thumbs/bkaovAYt-640.jpg&quot;,
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;title: &quot;Big Buck Bunny Trailer&quot;,
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;description: &quot;This animated film is made using free and open source software.&quot;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;file: &quot;http://content.bitsontherun.com/videos/kaUXWqTZ-640.mp4&quot;,
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;image: &quot;http://assets-jp.jwpsrv.com/thumbs/kaUXWqTZ-640.jpg&quot;,
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;title: &quot;Elephants Dream Trailer&quot;,
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;description: &quot;This is the worlds first open movie, made entirely with Blender.&quot;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}],
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;width: 700,
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;height: 240,
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;listbar: {
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;position: &quot;right&quot;,
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;size: 280
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}
&nbsp;&nbsp;&nbsp;&nbsp;});
&lt;/script&gt;
&lt;p&gt;Click on one of the links below to add an item to the player:&lt;/p&gt;
&lt;ul&gt;
&lt;li&gt;&lt;a href=&quot;#&quot; onclick=&quot;addVideo('http://content.bitsontherun.com/videos/yj1shGJB-60830.mp4', 'http://content.bitsontherun.com/thumbs/yj1shGJB-320.jpg', 'Sintel trailer', 'Sintel is a fantasy CGI movie from the Blender Open Movie Project.'); return false;&quot;&gt;Add the Sintel trailer to the playlist&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href=&quot;#&quot; onclick=&quot;addVideo('http://content.bitsontherun.com/videos/i8oQD9zd-kNspJqnJ.mp4', 'http://content.bitsontherun.com/thumbs/i8oQD9zd-640.jpg', 'Tears of Steel Trailer', 'A complete open pipeline was used to produce this visual effect film.'); return false;&quot;&gt;Add the Tears of Steel trailer to the playlist&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href=&quot;#&quot; onclick=&quot;addVideo('http://content.bitsontherun.com/videos/bkaovAYt-640.mp4', 'http://assets-jp.jwpsrv.com/thumbs/bkaovAYt-640.jpg', 'Big Buck Bunny Trailer', 'This animated film is made using free and open source software.'); return false;&quot;&gt;Add the Big Buck Bunny trailer to the playlist&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href=&quot;#&quot; onclick=&quot;addVideo('http://content.bitsontherun.com/videos/kaUXWqTZ-640.mp4', 'http://assets-jp.jwpsrv.com/thumbs/kaUXWqTZ-640.jpg', 'Elephants Dream Trailer', 'This animated film is made using free and open source software.'); return false;&quot;&gt;Add the Elephants Dream trailer to the playlist&lt;/a&gt;&lt;/li&gt;
&lt;/ul&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

The source code is available for this example. There is just a .html file. Publishing the html can be simply done with any text editor. Enjoy~! :)
