# Cloud Music Player (335)

Cloud Music Player for Distributed Systems Coursework. Just a README for now.

## Usage

### Web Interface

The web interface can be used by visiting [http://shell1.doc.ic.ac.uk:53231/Coursework/](http://shell1.doc.ic.ac.uk:53234/Coursework/)

### API

#### Get Playlists
Returns all the available playlists

<table>
  <tr>
    <td>Method</td>
    <td colspan=2>GET</td>
  </tr>
  <tr>
    <td>Endpoint</td>
    <td colspan=2>MusicManagementService?action=get-playlists</td>
  </tr>
  <tr>
    <td>
      Example Call
    </td>
    <td colspan=2>
    <code>
    curl -X GET "http://shell1.doc.ic.ac.uk:53231/CourseWork/MusicManagementService?action=get-playlists"
    </code>
    </td>
  </tr>
  <tr>
    <td>Response</td>
    <td colspan=2>
    <code>
    {"playlists":["ph-test"]}
    </code>
    </td>
  </tr>
</table>


#### Create Playlist
Creates a playlist with the given name

<table>
  <tr>
    <td>Method</td>
    <td colspan=2>POST</td>
  </tr>
  <tr>
    <td>Endpoint</td>
    <td colspan=2>MusicManagementService?action=create-playlist</td>
  </tr>
  <tr>
    <td>URL Params</td>
    <td><code>playlist-name</code> </td>
    <td>The name of the playlist to create</td>
  </tr>
  <tr>
    <td>
      Example Call
    </td>
    <td colspan=2>
    <code>
    curl -X POST "http://shell1.doc.ic.ac.uk:53231/CourseWork/MusicManagementService?action=create-playlist&playlist-name=ph-npl"
    </code>
    </td>
  </tr>
  <tr>
    <td>Response</td>
    <td colspan=2>
    <code>
    {"result":"Playlist Created"}
    </code>
    <br/>
    Or, if an error occurred (duplicates etc), returns HTTP response code <code>400 Bad Request</code> and response content:
    <br/>
    <code>
    {"result":"Playlist Couldn't be Created"}
    </code>
    </td>
  </tr>
</table>


#### Delete Playlist
Deletes a playlist and all it's music

<table>
  <tr>
    <td>Method</td>
    <td colspan=2>DELETE</td>
  </tr>
  <tr>
    <td>Endpoint</td>
    <td colspan=2>MusicManagementService?action=delete-playlist</td>
  </tr>
  <tr>
    <td>URL Params</td>
    <td><code>playlist-name</code> </td>
    <td>The name of the playlist to delete</td>
  </tr>
  <tr>
    <td>
      Example Call
    </td>
    <td colspan=2>
    <code>
    curl -X DELETE "http://shell1.doc.ic.ac.uk:53231/CourseWork/MusicManagementService?action=delete-playlist&playlist-name=ph-npl"
    </code>
    </td>
  </tr>
  <tr>
    <td>Response</td>
    <td colspan=2>
    <code>
    {"result":"Playlist Deleted"}
    </code>
    <br/>
    Or, if the playlist doesn't exist, a <code>400 Bad Request</code> and response:
    <br/>
    <code>
    {"result":"Playlist Couldn't be Found"}
    </code>
    </td>
  </tr>
</table>

#### Get Tracks
Creates a playlist with the given name

<table>
  <tr>
    <td>Method</td>
    <td colspan=2>GET</td>
  </tr>
  <tr>
    <td>Endpoint</td>
    <td colspan=2>MusicManagementService?action=get-tracks</td>
  </tr>
  <tr>
    <td>URL Params</td>
    <td><code>playlist-name</code> </td>
    <td>The name of the playlist to get tracks from</td>
  </tr>
  <tr>
    <td>
      Example Call
    </td>
    <td colspan=2>
    <code>
    curl -X GET "http://shell1.doc.ic.ac.uk:53231/CourseWork/MusicManagementService?action=get-tracks&playlist-name=ph-test"
    </code>
    </td>
  </tr>
  <tr>
    <td>Response</td>
    <td colspan=2>
    <code>
    {"tracks":["sample.mp3"]}
    </code>
    <br/>
    Or, if the playlist doesn't exist, a <code>400 Bad Request</code> and response:
    <br/>
    <code>
    {"result":"Playlist Couldn't be Found"}
    </code>
    </td>
  </tr>
</table>


#### Delete Track in Playlist
Deletes a track in a specified playlist

<table>
  <tr>
    <td>Method</td>
    <td colspan=2>DELETE</td>
  </tr>
  <tr>
    <td>Endpoint</td>
    <td colspan=2>MusicManagementService?action=delete-track</td>
  </tr>
  <tr>
    <td rowspan=2>URL Params</td>
    <td><code>playlist-name</code> </td>
    <td>The name of the playlist the tracks belong to</td>
  </tr>
  <tr>
    <td><code>file-name</code> </td>
    <td>The name of the track file</td>
  </tr>
  <tr>
    <td>
      Example Call
    </td>
    <td colspan=2>
    <code>
    curl -X DELETE "http://shell1.doc.ic.ac.uk:53231/CourseWork/MusicManagementService?action=get-tracks&playlist-name=ph-test&file-name=sample.mp3"
    </code>
    </td>
  </tr>
  <tr>
    <td>Response</td>
    <td colspan=2>
    <code>
    {"result":"Deleted Music File"}
    </code>
    <br/>
    Or, if the playlist doesn't exist, a <code>400 Bad Request</code> and response:
    <br/>
    <code>
    {"result":"Playlist Couldn't be Found"}
    </code>
    </td>
  </tr>
</table>


## Deployment

[Original CSG Guide](http://www.doc.ic.ac.uk/csg-old/java/servlets/personaltomcat/)

On a lab machine: `mktomcat6 TOMCAT_TARGET_DIR`
Change the port by editing `conf/server.xml`, changing the value in the *Connector* tag but not in the *Server* tag.

1. `cp WAR_FILE TOMCAT_TARGET_DIR/webapps`
2. `cd TOMCAT_TARGET_DIR`
3. `tomcat6 start`