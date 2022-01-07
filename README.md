# plexwho
A Linux command-line shell script that lists current Plex media streams, users and a few details as pulled from Tautulli's API. 


## Example Output:
```
   User         Plat Vres  Sres  TT Mbps ST Progress        Title
   ------------ ---- ----- ----- -- ---- -- --------------- -----
   neil.pye     Roku 1080p 1080p 01 3.71 pa 0:27:38/2:08:15 Basic Instinct
   Mike         Play 4k    1080p 11 6.41 pl 1:25:02/2:28:56 Dune
   ricksrevolut iOS  480p  480p  00 1.18 pl 0:46:08/1:44:16 An Audience with Sir Cliff Richard
   vyvbasterd   Chro 720p  720p  00 1.05 pl 0:03:31/0:27:25 The Good Life - Silly, But It's Fun...
```
### Meaning:
```
       User: Plex username (truncated if over 12 characters)
       Plat: User's Plex client (truncated to 4 characters)
       Vres: Resolution of the video file being played
       Sres: Resolution of the video stream
         TT: Transcoded and Throttled (11 if both, 01 if throttled, 00 if none)
       Mbps: Stream bandwidth (in Mbps, obviously)
         ST: Current status playing (pl) or paused (pa)
   Progress: Current position in media vs total duration of media
      Title: The full title of the media
```
## Installation:
```
plexwho is intended to run on a Linux box with a bash shell.
Typically drop this script into /usr/local/bin
It has the following prerequisits:
   
     * tautulli: plexwho does not contact the Plex server directly, it uses tautulli
       to grab the information about each stream session (https://tautulli.com/)
     * curl: This is used to query the tautulli API (https://curl.se/)
     * jq: parses the data returned from tautulli (https://stedolan.github.io/jq/)
     * bc: for doing a bit of floating point math
     * tr: for cleaning up some text strings (part of coreutils)

You can print debug output with 'plexwho -d'
You can view the "license" with 'plexwho -l'
```
