# Assignment

## SQL Exercises

1. Count how many tracks belong to the MediaType "Protected MPEG-4 video file".

SELECT count(media_type_id) FROM tracks WHERE media_type_id IN (SELECT id FROM media_types WHERE name='Protected MPEG-4 video file');

=> 214

2. Find the least expensive Track that has the Genre "Electronica/Dance".

SELECT min(unit_price) FROM tracks WHERE genre_id IN (SELECT id FROM genres WHERE name='Electronica/Dance');

SELECT name FROM tracks WHERE unit_price=0.99 AND genre_id=15 LIMIT 1;


3. Find the all the Artists whose names start with A.

SELECT name FROM artists WHERE name like 'A%';

4. Find all the Tracks that belong to the first Playlist.

SELECT name FROM tracks WHERE id IN (SELECT track_id FROM playlists_tracks WHERE playlist_id=1);

## Ruby Exercises

1. Count how many tracks belong to the "Hip Hop/Rap" genre

genre_id = Genre.where(name: 'Hip Hop/Rap')
Track.where(genre_id: genre_id).count

=> 30

2. Find the most expensive Track that has the MediaType "MPEG audio file".

media_type_id = MediaType.where(name: 'MPEG audio _file')
Track.where(media_type_id: media_type_id).order(:unit_price).first

3. Find the 2 oldest Artists.

Artist.order("created_at ASC").limit(2)

4. Find all the Tracks that belong to the 2 most recent Playlist.

ids = Playlist.order("created_at DESC").limit(2)
Track.where(id: ids)


