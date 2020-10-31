# NoSQL, Cassandra - Getting Starting
## DAW-MP02-UF4 - Exercici de Bases de dades objectes-relacionals
Instala una distribució de Linux basada en Debian. 

[Afegeix els repositoris i les claus](http://wiki.apache.org/cassandra/DebianPackaging):

```bash
#repositoris a insertar:
deb http://www.apache.org/dist/cassandra/debian 11x main
deb-src http://www.apache.org/dist/cassandra/debian 11x main
#claus
gpg --keyserver pgp.mit.edu --recv-keys F758CE318D77295D
gpg --export --armor F758CE318D77295D | sudo apt-key add -
gpg --keyserver pgp.mit.edu --recv-keys 2B5C1B00
gpg --export --armor 2B5C1B00 | sudo apt-key add -
#instalació
sudo apt-get update
sudo apt-get install cassandra
```

Comprova que [el teu node funciona](https://wiki.apache.org/cassandra/GettingStarted):

    nodetool -h <la_teva_ip> ring

Crea un [key space](https://wiki.apache.org/cassandra/GettingStarted):

```python
cqlsh -3
```

    CREATE KEYSPACE mykeyspace WITH strategy_class = 'SimpleStrategy'
    AND strategy_options:replication_factor='1';    
    USE mykeyspace;
    
Crea la base de dades [music service](http://www.datastax.com/documentation/cql/3.0/cql/ddl/ddl_music_service_c.html)

```sql
CREATE TABLE songs (
  id uuid PRIMARY KEY,
  title text,
  album text,
  artist text,
  data blob
 );

CREATE TABLE playlists (
  id_song_in_playlist uuid,
  id_play_list uuid,
  song_order int,
  song_id uuid,
  title text,
  album text,
  artist text,
  PRIMARY KEY  (id_song_in_playlist ) );

INSERT INTO playlists (id_song_in_playlist, id_play_list, 
                       song_order, song_id, title, artist, album)
  VALUES (f51b72a6-cb7f-11e3-93aa-001f16f451d3,
          62c36092-82a1-3a00-93d1-46196ee77204, 1,
          a3e64f8f-bd44-4f28-b8d9-6938726e34d4, 'La Grange', 
          'ZZ Top', 'Tres Hombres');

INSERT INTO playlists (id_song_in_playlist, id_play_list, 
                       song_order, song_id, title, artist, album)
  VALUES (060a54ba-cb80-11e3-93aa-001f16f451d3,
          62c36092-82a1-3a00-93d1-46196ee77204, 2,
          8a172618-b121-4136-bb10-f665cfc469eb, 'Moving in Stereo', 
          'Fu Manchu', 'We Must Obey');

INSERT INTO playlists (id_song_in_playlist, id_play_list, 
                       song_order, song_id, title, artist, album)
  VALUES (10942bcc-cb80-11e3-93aa-001f16f451d3,
          62c36092-82a1-3a00-93d1-46196ee77204, 3,
          2b09185b-fb5a-4734-9b56-49077de9edbf, 'Outside Woman Blues', 
          'Back Door Slam', 'Roll Away');

SELECT * FROM playlists;

CREATE INDEX ON playlists(artist );

SELECT * FROM playlists WHERE artist = 'Fu Manchu';
```


**Exercicis**

 * Un cop instalat Cassandra a la teva màquina crea un keyspace de l'exemple i les taules.
 * Inserta les dades a les taules.
 * Prova a fer les dues seleccions sense crear l'index, què passa? Per què?
 * Crea l'idex i torna a fer les seleccions.
 * Per què executem `cqlsh -3` i no simplement `cqlsh` ?
 

---

#FpInfor #Daw #DawMp02 #DawMp02Uf04

---

###### Autor: daniel herrera 2014.04.23 13:44:41
###### Editat per: daniel herrera 2014.04.24 07:14:39
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
