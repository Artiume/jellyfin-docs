---
uid: codecs
title: Codec Compatibility
---

 # [Codec Tables](https://en.wikipedia.org/wiki/List_of_codecs "Wikipedia's list of all codecs")
## [Video Compatibility](https://en.wikipedia.org/wiki/Comparison_of_video_container_formats "Wikipedia's video codec tables")

If the video codec is unsupported, this will result in transcoding. This is the most intensive CPU component of transcoding. Decoding is less intensive than encoding.

||WebOS|Android|AndroidTV|Kodi|Roku|
|:---:|:---:|:---:|:---:|:---:|:---:|
|[H.262/Xvid](https://en.wikipedia.org/wiki/MPEG-4_Part_2)|✅|✅|✅|✅|✅|
|[H.262/DivX](https://en.wikipedia.org/wiki/DivX)|✅|✅|✅|✅|✅|
|[H.264/AVC](https://caniuse.com/#feat=mpeg4 "H264 Browser Support Reference")|✅|✅|✅|✅|✅|
|[H.265/HEVC](https://caniuse.com/#feat=hevc "HEVC Browser Support Reference")|❌<sup>1</sup>|🔶<sup>2</sup>|❌|✅|❌|

<sup>1</sup>HEVC support is potentially possible by offloading to the OS. *untested*

<sup>2</sup>Android playback is currently broken. Client reports that HEVC is supported and attempts to Directstream it.

## [Audio Compatibility](https://en.wikipedia.org/wiki/Comparison_of_video_container_formats#Audio_coding_formats_support "Wikipedia's audio codec tables")

If the audio codec is unsupported or incompatible (such as playing a 5.1 channel stream on a stereo device), the audio codec must be transcoded. This is not nearly as intensive as video coding.

||WebOS|Android|AndroidTV|Kodi|Roku
|:---:|:---:|:---:|:---:|:---:|:---:
|MP3|🔶<sup>1</sup>|✅|✅|✅|✅
|AAC|✅|✅|✅|✅|✅
|AC3|✅|✅|✅|✅|✅
|EAC3|✅|✅|✅|✅|✅
|VORBIS|❌|✅|✅|✅|✅


<sup>1</sup>MP3 Mono is incorrectly reported as unsupported.

## [Subtitle Compatibility](https://en.wikipedia.org/wiki/Comparison_of_video_container_formats#Subtitle/caption_formats_support "Wikipedia's subtitle codec tables")

Subtiles can be a subtle issue for transcoding. Containers have a limited number of subtitles that are supported. If subtitles need to be transcoded, it will happen one of two ways. They can be converted into another supported format (text-based subtitles) or burned into the video (image/lossless based and ASS based) due to the subtitles transcoding not being supported. This is the most intenstive method of transcoding due to two transcodings happening at once; applying the subtitle layer on top of the video layer. 

## [Container Compatibility](https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Containers)

If the container is unsupported, this will result in remuxing. The video and audio codec will remain intact, but wrapped in a container that is supported. This is the least intensive process. Most video containers will be remuxed to use the hls streaming protocol and ts containers. Remuxing shouldn't be a concern even for a Rpi3.

||WebOS|Android|AndroidTV|Kodi|Roku
|:---:|:---:|:---:|:---:|:---:|:---:
|[mp4](https://en.wikipedia.org/wiki/MPEG-4_Part_14)|✅|✅|✅|✅|✅
|[MKV](https://en.wikipedia.org/wiki/Matroska)<sup>1, 2</sup>|❌|🔶|🔶|🔶|🔶
|[ts](https://en.wikipedia.org/wiki/MPEG_transport_stream)|✅|✅|✅|✅|✅


<sup>1</sup>MKV containers can hold nearly any codec. *support not verified, initial testing is showing that all containers convert to ts using hls streaming protocol* Mp4 successfully streamed using http protocol instead of hls protocol and did not remux.

<sup>2</sup>webm containers that have file extension mkv are marked as mkv on the media info page, and properly labeled as webm during playback. 


    *Allow video playback that requires conversion without re-encoding* was disabled. Played avi (MPEG4, XVID, Advanced Simple Profile, Level5) with ac3 ([0] [0][0] / 0x2000), 48000 Hz, stereo, fltp, 224 kb/s
    Played another video with transcoding disabled, h264, aac 2 ch, mkv (webm). It converted to hls with ts as well.

[hls @ 0x55925f432c40] Opening '/ram_transcode/bd75624fda66ef5ed43d1e6a19de11a6240.ts' for writing
frame=  641 fps=0.0 q=-1.0 Lsize=N/A time=00:24:03.00 bitrate=N/A speed=9.43e+04x    

hls + ac3 > aac conversion

frame=  575 fps=0.0 q=-1.0 size=N/A time=00:00:53.10 bitrate=N/A speed= 106x    


# Codec Tests:

## WebOS
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
    
    
## Notes

### Codecs
[Chomra Subsampling](https://trac.ffmpeg.org/wiki/Chroma%20Subsampling)

https://www.projectorcentral.com/chroma-subsampling-explained.htm

Bit depth 8 bit, 
Pixel format yuv420p

https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta

https://forum.odroid.com/viewtopic.php?t=21215

https://answers.launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta

https://web.archive.org/web/20160615194616/http://www.mp4ra.org/codecs.html

https://en.wikipedia.org/wiki/Moving_Picture_Experts_Group#Standards

https://trac.ffmpeg.org/wiki/Encode/AAC

https://www.velleman.eu/downloads/3/h264_vs_mpeg4_en.pdf

https://stackoverflow.com/questions/22710099/ffmpeg-create-blank-screen-with-text-video#22719247

https://www.reddit.com/r/Monitors/comments/94r0r6/question_8bit_frc_yuv420_vs_8bit_rgb/

https://superuser.com/questions/1281836/what-does-matroska-have-which-webm-doesnt-that-made-the-differentiation-necess

https://avidemux.org/smif/index.php?topic=17197.0

https://en.wikipedia.org/wiki/Digital_container_format

http://mp4ra.org/#/

https://www.matroska.org/technical/specs/subtitles/ssa.html

https://en.wikipedia.org/wiki/List_of_open-source_codecs

https://en.wikipedia.org/wiki/Comparison_of_audio_coding_formats

https://github.com/MPEGGroup/isobmff

https://trac.ffmpeg.org/wiki/Encode/H.264#FAQ

### Streaming

https://help.encoding.com/knowledge-base/article/correct-mime-types-for-serving-video-files/

https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types

https://www.iana.org/assignments/media-types/media-types.xhtml#video

https://web.archive.org/web/20190427210855/https://simpleiptv.net/?page_id=473

https://mux.com/blog/the-community-gave-us-low-latency-live-streaming-then-apple-took-it-away/

https://www.lifewire.com/m3u8-file-2621956

https://stackoverflow.com/questions/56700705/how-to-enable-lhls-in-ffmpeg-4-1

https://blogs.akamai.com/2018/10/best-practices-for-ultra-low-latency-streaming-using-chunked-encoded-and-chunk-transferred-cmaf.html

https://blog.jonlu.ca/posts/illegal-streams

https://en.wikipedia.org/wiki/MPEG_transport_stream

https://www.reddit.com/r/IPTV/comments/avdqbq/hls_m3u8_vs_mpegts_ts_which_do_you_find_better/

https://www.wowza.com/blog/what-is-cmaf

https://github.com/video-dev/hlsjs-rfcs/blob/a6e7cc44294b83a7dba8c4f45df6d80c4bd13955/proposals/0001-lhls.md

https://github.com/MediaBrowser/Emby/pull/2276
