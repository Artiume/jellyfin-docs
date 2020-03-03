---
uid: codecs
title: Codec Compatibility
---

 # [Codec Tables](https://en.wikipedia.org/wiki/List_of_codecs "Wikipedia's list of all codecs")
 
The goal is to Direct Play all media. This means the container, video, audio and subtitles are all compatible with the client. Direct Stream will occur if the audio, container or subtitles happen to not be supported. Subtitles can be tricky because they can cause Direct Stream (subtitles are remuxed) or video transcoding (burning in subtitles) to occur. If the video codec is unsupported, this will result in video transcoding. This is the most intensive CPU component of transcoding. Decoding is less intensive than encoding.

## [Video Compatibility](https://en.wikipedia.org/wiki/Comparison_of_video_container_formats "Wikipedia's video codec tables")

[Breakdown of video codecs.](https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Video_codecs)

||Chrome|Firefox|Safari|Android|iOS|AndroidTV|[Roku](https://developer.roku.com/docs/specs/streaming.md)|Kodi|[MPV Shim](https://jellyfin.org/docs/general/clients/index.html#jellyfin-mpv-shim)|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|[MPEG-4 Part 2/SP](https://en.wikipedia.org/wiki/DivX)|❌|❌|❌|❌||❌||✅|✅|
|[MPEG-4 Part 2/ASP](https://en.wikipedia.org/wiki/MPEG-4_Part_2#Advanced_Simple_Profile_(ASP))|❌|❌|❌|❌||❌||✅|✅|
|[H.264 8Bit](https://caniuse.com/#feat=mpeg4 "H264 Browser Support Reference")|✅|✅|✅|✅||✅||✅|✅|
|[H.264 10Bit](https://caniuse.com/#feat=mpeg4 "H264 Browser Support Reference")|✅|❌|❌|✅||✅||✅|✅|
|[H.265](https://caniuse.com/#feat=hevc "HEVC Browser Support Reference")|❌|❌|❌<sup>1</sup>|🔶<sup>2</sup>||❌||✅|✅|
|[VP9](https://caniuse.com/#search=vp9 "V9 Browser Support Reference")|✅|✅|❌|||||||

<sup>1</sup>HEVC support is potentially available by offloading to the operating system, but this has not been tested.

<sup>2</sup>Android playback is currently broken. Client reports that HEVC is supported and attempts to Direct Stream.

[Format Cheetsheet:](https://en.wikipedia.org/wiki/MPEG-4#MPEG-4_Parts)

|[MPEG-2<br>Part 2](https://en.wikipedia.org/wiki/H.262/MPEG-2_Part_2)|[MPEG-4<br>Part-2](https://en.wikipedia.org/wiki/MPEG-4_Part_2)<sup>1</sup>|[MPEG-4<br>Part-10](https://en.wikipedia.org/wiki/Advanced_Video_Coding)|[MPEG-4<br>Part-14](https://en.wikipedia.org/wiki/MPEG-4_Part_14)|[MPEG-H<br>Part 2](https://en.wikipedia.org/wiki/High_Efficiency_Video_Coding)|
|:---:|:---:|:---:|:---:|:---:|
|H.262|MPEG4 SP/ASP|H.264|MP4 Container<sup>2</sup>|H.265|
|MPEG-2 Video|DivX|MPEG-4 AVC||HEVC|
|DVD-Video|DX50||||

<sup>1</sup>[MPEG-4 Part-2 vs Part-10](https://www.afterdawn.com/glossary/term.cfm/mpeg_4_part_10)

<sup>2</sup>[MPEG-4 Part 17: MP4TT Subtitles](https://en.wikipedia.org/wiki/MPEG-4_Part_17)

## [Audio Compatibility](https://en.wikipedia.org/wiki/Comparison_of_video_container_formats#Audio_coding_formats_support "Wikipedia's audio codec tables")

If the audio codec is unsupported or incompatible (such as playing a 5.1 channel stream on a stereo device), the audio codec must be transcoded. This is not nearly as intensive as video coding.

||Chrome|Firefox|Safari|Android|AndroidTV|iOS|Roku|Kodi|MPV Shim|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|FLAC|✅|❌|✅|✅||||✅|✅|
|MP3|🔶<sup>1</sup>|🔶|✅|✅||||✅|✅|
|AAC|✅|✅|✅|✅||||✅|✅|
|AC3|✅|❌|✅|✅||||✅|✅|
|EAC3<sup>2</sup>|✅|✅|✅|✅||||✅|✅|
|VORBIS<sup>3</sup>|✅|✅|✅|✅||||✅|✅|
|DTS<sup>4</sup>|❌|❌|❌|✅||||✅|✅|

[Format Cheetsheet:](https://en.wikipedia.org/wiki/Moving_Picture_Experts_Group#External_links)

|[MPEG-1](https://en.wikipedia.org/wiki/MPEG-1)|[MPEG-2](https://en.wikipedia.org/wiki/MPEG-2)|
|:---:|:---:|
|[MP2 (layer 2)](https://en.wikipedia.org/wiki/MPEG-1_Audio_Layer_II)|[AAC (Part 7)](https://en.wikipedia.org/wiki/Advanced_Audio_Coding)|
|[MP3 (layer 3)](https://en.wikipedia.org/wiki/MP3)||

<sup>1</sup>MP3 Mono is incorrectly reported as unsupported and will transcode to AAC.

<sup>2</sup>Only EAC3 2.0 has been tested.

<sup>3</sup>OGG containers are not supported and will cause VORBIS to convert.

<sup>4</sup>Only DTS Mono has been tested.

## [Subtitle Compatibility](https://en.wikipedia.org/wiki/Comparison_of_video_container_formats#Subtitle/caption_formats_support "Wikipedia's subtitle codec tables")

Subtiles can be a subtle issue for transcoding. Containers have a limited number of subtitles that are supported. If subtitles need to be transcoded, it will happen one of two ways. They can be converted into another supported format (text-based subtitles) or burned into the video (image/lossless based and ASS based) due to the subtitles transcoding not being supported. This is the most intenstive method of transcoding due to two transcodings happening at once; applying the subtitle layer on top of the video layer.

||Format|TS|MP4|MKV|AVI|
|:---:|:---:|:---:|:---:|:---:|:---:|
|[SubRip Text (SRT)](https://en.wikipedia.org/wiki/SubRip)|Text|❌|🔶|✅|🔶|
|[WebVTT (VTT)](https://en.wikipedia.org/wiki/WebVTT)|Text|❌<sup>1</sup>|❌<sup>1</sup>|✅|🔶|
|ASS/SSA<sup>1</sup>|Formatted Text|❌|❌|✅|🔶|
|VobSub|Picture|❌|✅|✅|🔶|
|DVB-SUB [(SUB + IDX](https://forum.videohelp.com/threads/261451-Difference-between-SUB-and-IDX-file)|Picture|✅|❌|✅|❌|
|MP4TT/TXTT|XML|❌|✅|❌|❌|
|PGSSUB|Picture|❌|❌|✅|❌|

<sup>1</sup>VTT are supported in an [HLS Stream](https://helpx.adobe.com/adobe-media-server/dev/webvtt-subtitles-captions.html).

<sup>2</sup>ASS Subtitles are only supported by MKV files. MKV files aren't supported by Firefox. They will always inherently be burned into the video. This is not a limitation of Jellyfin.

## [Container Compatibility](https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Containers)

If the container is unsupported, this will result in remuxing. The video and audio codec will remain intact, but wrapped in a supported container. This is the least intensive process. Most video containers will be remuxed to use the HLS streaming protocol and TS containers. Remuxing shouldn't be a concern even for an RPi3.

||Chrome|Firefox|Safari|Android|AndroidTV|Kodi|Roku|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|[MP4](https://en.wikipedia.org/wiki/MPEG-4_Part_14)<sup>1</sup>|✅|✅|✅|✅|✅|✅|✅|
|[MKV](https://en.wikipedia.org/wiki/Matroska)<sup>2, 3</sup>|✅|❌||✅|✅|✅||
|[WebM](https://en.wikipedia.org/wiki/WebM)<sup>3</sup>|✅|✅||||✅||
|[TS](https://en.wikipedia.org/wiki/MPEG_transport_stream)<sup>4</sup>|✅|✅|✅|✅|✅|✅|✅|
|[OGG](https://en.wikipedia.org/wiki/Ogg)|❌|❌|❌|❌|❌|❌|❌|

<sup>1</sup>MP4 containers are one of the few containers that will not remux.

<sup>2</sup>MKV containers can hold nearly any codec, but are not compatible with streaming in Firefox and will remux.

<sup>3</sup>MKV containers are improperly labeled as WebM in Firefox during playback.

<sup>4</sup>TS is one of the primary containers for streaming for Jellyfin. 

# Codec Tests:

## Web
### Video
h264 CB, 8bit

    Stream #0:0(eng): Video: h264 (Constrained Baseline), yuv420p(tv, bt709, progressive), 1280x720 [SAR 1:1 DAR 16:9], 23.98 fps, 23.98 tbr, 1k tbn, 47.95 tbc (default)


h264 high, 8bit

    Stream #0:0: Video: h264 (High), yuv420p(progressive), 640x480, SAR 1:1 DAR 4:3, 23.98 fps, 23.98 tbr, 1k tbn, 47.95 tbc (default)


MPEG4, XVID, Advanced Simple Profile, Level5

    Stream #0:0: Video: mpeg4 (Advanced Simple Profile) (XVID / 0x44495658), yuv420p, 608x336 [SAR 1:1 DAR 38:21], 1121 kb/s, 25 fps, 25 tbr, 25 tbn, 25 tbc


### Audio
AC3 5.1 ch > aac 2.0 ch 
    
    Stream #0:1(eng): Audio: ac3, 48000 Hz, 5.1(side), fltp, 640 kb/s (default) > Stream #0:1: Audio: aac (LC), 48000 Hz, stereo, fltp, 384 kb/s (default)

aac 2.0 ch
    
    Stream #0:1(jpn): Audio: aac (LC), 48000 Hz, stereo, fltp (default)

AC3 stereo

    Stream #0:1: Audio: ac3 ([0] [0][0] / 0x2000), 48000 Hz, stereo, fltp, 224 kb/s
    
    
    
    
---

    *Allow video playback that requires conversion without re-encoding* was disabled. Played avi (MPEG4, XVID, Advanced Simple Profile, Level5) with ac3 ([0] [0][0] / 0x2000), 48000 Hz, stereo, fltp, 224 kb/s
    Played another video with transcoding disabled, h264, aac 2 ch, mkv (webm). It converted to hls with ts as well.

[hls @ 0x55925f432c40] Opening '/ram_transcode/bd75624fda66ef5ed43d1e6a19de11a6240.ts' for writing
frame=  641 fps=0.0 q=-1.0 Lsize=N/A time=00:24:03.00 bitrate=N/A speed=9.43e+04x    

hls + ac3 > aac conversion

frame=  575 fps=0.0 q=-1.0 size=N/A time=00:00:53.10 bitrate=N/A speed= 106x   

## Notes

### Codecs


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
