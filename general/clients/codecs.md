
https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta

https://stackoverflow.com/questions/50971187/can-i-build-chromium-with-ffmpeg-to-support-all-video-formats

https://forum.odroid.com/viewtopic.php?t=21215

https://answers.launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta

https://web.archive.org/web/20160615194616/http://www.mp4ra.org/codecs.html

https://en.wikipedia.org/wiki/Moving_Picture_Experts_Group#Standards

https://trac.ffmpeg.org/wiki/Encode/AAC

https://trac.ffmpeg.org/wiki/Encode/VP9

https://sites.google.com/a/webmproject.org/wiki/ffmpeg/vp9-encoding-guide

https://superuser.com/questions/1211786/why-is-encoding-vp8-9-so-slow-compared-to-h-264

https://superuser.com/questions/1281836/what-does-matroska-have-which-webm-doesnt-that-made-the-differentiation-necess

https://avidemux.org/smif/index.php?topic=17197.0

https://developer.roku.com/docs/specs/streaming.md

https://trac.ffmpeg.org/ticket/7037

https://www.lifewire.com/bdmv-file-2619830

### Misc

`
Job running: EAE_ROOT='/tmp/pms-2a0316ba-f4cf-4759-af8c-d676a199e92d/EasyAudioEncoder' FFMPEG_EXTERNAL_LIBS='/config/Library/Application\ Support/Plex\ Media\ Server/Codecs/8bf330d-2818-linux-x86_64/' XDG_CACHE_HOME='/config/Library/Application Support/Plex Media Server/Cache' XDG_DATA_HOME='/usr/lib/plexmediaserver/Resources' X_PLEX_TOKEN='xxxxxxxxxxxxxxxxxxxx' '/usr/lib/plexmediaserver/Plex Transcoder' '-codec:0' 'h264' '-noaccurate_seek' '-analyzeduration' '20000000' '-probesize' '20000000' '-i' '/yourcomputer/data/unionfs/media/anime/Another/Season 1/Another - S01E01 - Rough Sketch HDTV-720p.mkv' '-map' '0:0' '-metadata:s:0' 'language=jpn' '-codec:0' 'copy' '-map' '0:1' '-metadata:s:1' 'language=eng' '-codec:1' 'copy' '-f' 'dash' '-seg_duration' '5' '-init_seg_name' 'init-stream$RepresentationID$.m4s' '-media_seg_name' 'chunk-stream$RepresentationID$-$Number%05d$.m4s' '-window_size' '5' '-delete_removed' 'false' '-skip_to_segment' '1' '-time_delta' '0.0625' '-manifest_name' 'http://127.0.0.1:32400/video/:/transcode/session/whrtmao0hvjo0120h21kz6cb/d5b670a4-a535-490f-881e-dcbba86b8f82/manifest' '-avoid_negative_ts' 'disabled' '-map_metadata' '-1' '-map_chapters' '-1' 'dash' '-start_at_zero' '-copyts' '-vsync' 'cfr' '-y' '-nostats' '-loglevel' 'quiet' '-loglevel_plex' 'error' '-progressurl' 'http://127.0.0.1:32400/video/:/transcode/session/whrtmao0hvjo0120h21kz6cb/d5b670a4-a535-490f-881e-dcbba86b8f82/progress'
`

`
/usr/local/bin/ffmpeg -fflags +genpts -f matroska,webm -i file:"/media/anime/Another/Season 1/Another - S01E01 - Rough Sketch HDTV-720p.mkv" -map_metadata -1 -map_chapters -1 -threads 0 -map 0:0 -map 0:1 -map -0:s -codec:v:0 copy -bsf:v h264_mp4toannexb -copyts -vsync -1 -codec:a:0 copy -f hls -max_delay 5000000 -avoid_negative_ts disabled -start_at_zero -hls_time 6 -individual_header_trailer 0 -hls_segment_type mpegts -start_number 0 -hls_segment_filename "/ram_transcode/cba664b5090123ed25d706c5aae18e45%d.ts" -hls_playlist_type vod -hls_list_size 0 -y "/ram_transcode/cba664b5090123ed25d706c5aae18e45.m3u8"
`

---

`
/usr/local/bin/ffmpeg '-codec:0' 'h264' '-noaccurate_seek' '-analyzeduration' '20000000' '-probesize' '20000000' '-i' '/yourcomputer/data/unionfs/media/anime/Another/Season 1/Another - S01E01 - Rough Sketch HDTV-720p.mkv' '-map' '0:0' '-metadata:s:0' 'language=jpn' '-codec:0' 'copy' '-map' '0:1' '-metadata:s:1' 'language=eng' '-codec:1' 'copy' '-f' 'dash' '-seg_duration' '5' '-init_seg_name' 'init-stream$RepresentationID$.m4s' '-media_seg_name' 'chunk-stream$RepresentationID$-$Number%05d$.m4s' '-window_size' '5' 'false'  '1' '-time_delta' '0.0625' '-manifest_name' 'http://127.0.0.1:32400/video/:/transcode/session/whrtmao0hvjo0120h21kz6cb/d5b670a4-a535-490f-881e-dcbba86b8f82/manifest' '-avoid_negative_ts' 'disabled' '-map_metadata' '-1' '-map_chapters' '-1' 'dash' '-start_at_zero' '-copyts' '-vsync' 'cfr' '-y' '-progressurl' 'http://127.0.0.1:32400/video/:/transcode/session/whrtmao0hvjo0120h21kz6cb/d5b670a4-a535-490f-881e-dcbba86b8f82/progress'
`

Removed: '-nostats' '-loglevel' 'quiet' '-loglevel_plex' '-delete_removed' '-skip_to_segment'

`
/usr/local/bin/ffmpeg -fflags +genpts -f matroska,webm -i file:"/media/anime/Another/Season 1/Another - S01E01 - Rough Sketch HDTV-720p.mkv" -map_metadata -1 -map_chapters -1 -threads 0 -map 0:0 -map 0:1 -map -0:s -codec:v:0 copy -bsf:v h264_mp4toannexb -copyts -vsync -1 -codec:a:0 copy -f hls -max_delay 5000000 -avoid_negative_ts disabled -start_at_zero -hls_time 6 -individual_header_trailer 0 -hls_segment_type mpegts -start_number 0 -hls_segment_filename "/ram_transcode/cba664b5090123ed25d706c5aae18e45%d.ts" -hls_playlist_type vod -hls_list_size 0 -y "/ram_transcode/cba664b5090123ed25d706c5aae18e45.m3u8"
`

---

`
/usr/local/bin/ffmpeg -re -i file:"/media/samples/jellyfish-3-mbps-hd-h264.mkv" -map 0 -map 0 -c:a libmp3lame -c:v libx264 -b:v:0 800k -b:v:1 300k -s:v:1 320x170 -profile:v:1 baseline -profile:v:0 main -bf 1 -keyint_min 120 -g 120 -sc_threshold 0 -b_strategy 0 -ar:a:1 22050 -use_timeline 1 -use_template 1 -window_size 5 -adaptation_sets "id=0,streams=v id=1,streams=a" -f dash /ram_transcode/cba664b5090123ed25d706c5aae18e45dfdfddf.mpd
`

---

`
"D:\Programs\Jellyfin\Server\ffmpeg.exe" "-f matroska,webm -ss 00:02:24.104 -i file:\"[filepath]\" -threads 0 -v quiet -vframes 1 -vf \"scale=600:trunc(600/dar/2)*2,thumbnail=24\" -f image2 \"C:\ProgramData\Jellyfin\Server\cache\temp\c19484bb-0355-4f92-837e-122f56eb9e40.jpg\""
`
