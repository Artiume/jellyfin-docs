---
uid: codecs
title: Client Compatibility
---


# Video Codec Compatibility

If the video codec is unsupported, this will result in transcoding. This is the most intensive CPU component of transcoding. Decoding is less intensive than encoding.

||WebOS|Android|AndroidTV|Kodi|Roku
|:---:|:---:|:---:|:---:|:---:|:---:
|[H.264/AVC](https://caniuse.com/#feat=mpeg4 "H264 Browser Support Reference")|✅|✅|✅|✅|✅
|[H.265/HEVC](https://caniuse.com/#feat=hevc "HEVC Browser Support Reference")|❌<sup>1</sup>|🔶<sup>2</sup>|❌|✅|❌

<sup>1</sup>HEVC support is potentially possible by offloading to the OS. *untested*

<sup>2</sup>Android playback is currently broken. Client reports that HEVC is supported and attempts to Directstream it.

# Audio Codec Compatibility

If the audio codec is unsupported or incompatible (such as due to a 5.1 stream played on a stereo device), the audio codec must be transcoded. This is not nearly as intensive as video coding.

||WebOS|Android|AndroidTV|Kodi|Roku
|:---:|:---:|:---:|:---:|:---:|:---:
|MP3|✅|✅|✅|✅|✅

# Subtitle Compatibility

Subtiles can be a subtle issue for transcoding. Containers have a limited number of subtitles that are supported. If subtitles need to be transcoded, it will happen one of two ways. They can be converted into another supported format (text-based subtitles) or burned into the video (image/lossless based and ASS based) due to the subtitles transcoding not being supported. This is the most intenstive method of transcoding due to two transcodings happening at once; applying the subtitle layer on top of the video layer. 

# Container Compatibility

If the container is unsupported, this will result in remuxing. The video and audio codec will remain intact, but wrapped in a container that is supported. This is the least intensive process. *need to verify CPU loading compared to audio*

||WebOS|Android|AndroidTV|Kodi|Roku
|:---:|:---:|:---:|:---:|:---:|:---:
|mp4|✅|✅|✅|✅|✅
|MKV<sup>1</sup>|🔶|🔶|🔶|🔶|🔶

<sup>1</sup>MKV containers can hold nearly any codec. *verify actual support*

Notes
[Chomra Subsampling](https://trac.ffmpeg.org/wiki/Chroma%20Subsampling)
Bit depth 8 bit
Pixel format yuv420p

https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta

https://forum.odroid.com/viewtopic.php?t=21215

https://answers.launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta

https://stackoverflow.com/questions/22710099/ffmpeg-create-blank-screen-with-text-video#22719247

https://www.reddit.com/r/Monitors/comments/94r0r6/question_8bit_frc_yuv420_vs_8bit_rgb/

https://superuser.com/questions/1281836/what-does-matroska-have-which-webm-doesnt-that-made-the-differentiation-necess
