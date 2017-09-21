---
title: (HABTM) has_and_belongs_to_many Bug in Ruby On Rails
id: 238
categories:
  - 不斷開發
date: 2007-08-08 23:28:00
tags:
---

Once the HABTM relation was made, for example:

    class Song &lt; ActiveRecord::Base
      has_and_belongs_to_many :artists
    end
    `</pre>
    The operation shown below is valid:
    <pre>`song.artists &lt;&lt; Artist.new(:name =&gt; 'Barbra Streisand')
    `</pre>
    But this may make a BIG problem:
    <pre>`song.artists &lt;&lt; Artist.find(:name =&gt; 'Barbra Streisand')

    Mysql::Error: Duplicate entry '1' for key 1: INSERT INTO artists_songs (`artist_id`, `id`, `song_id`) VALUES (1, 1, 3)
    `</pre>
    The `id` field should be "autoincrement". Why pass a Fixnum to it? That is the question. I find out that when we push(&lt;&lt;) an artist to a song, whole the attributes on this artist will  be expanded as arguments of the SQL query. And then duplicate :id to :artist_id.

    Hum, it sounds great. There is no problem. _But_ the :id key-value pair is still. That means **we will establish a HABTM relation with a given key**. So we sometimes get error from here. Try the tricky way:
    <pre>`class Song &lt; ActiveRecord::Base
      has_and_belongs_to_many :artists,
      :insert_sql =&gt; 'INSERT INTO `artists_songs` ( `song_id`, `artist_id` )
                      VALUES (#{id}, #{record.id})'
    end

How awful the code!