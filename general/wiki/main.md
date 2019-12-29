For Linux, QSV will use the libmfx library (MFX should be the proper term for QSV, MFX uses a modified VAAPI, see notes below). Normal VAAPI will use the libva library.  The Debian link I added shows a list of supported HW for VA-API, we could incorporate this into the guide. 

https://github.com/Intel-FFmpeg-Plugin/Intel_FFmpeg_plugins/wiki grep -rnw '/path/to/somewhere/' -e 'pattern'
"QSV transcode acceleration on Linux systems are enabled from FFMPEG 2.8 and forward"

Intel Media Driver
https://github.com/intel/media-driver

AMF is supported on Linux but x265 coding is not. 
https://www.phoronix.com/scan.php?page=news_item&px=FFmpeg-AMD-AMF-Vulkan

Found this
ffmpeg has AMF enabled for x264/5
https://www.reddit.com/r/Amd/comments/8eirp4/ffmpeg_40_released_includes_amf_hardware_encoding/

AMF Linux Support still not official
https://github.com/GPUOpen-LibrariesAndSDKs/AMF/issues/4

Zen is CPU only. No hardware acceleration for any form of video decoding/encoding.
You need APU or dGPU. It will be a while before AV1 hardware acceleration shows up though (realistically 2020+).

VAAPI driver for Intel G45 & HD Graphics family uses the i965 va driver. 
https://packages.debian.org/sid/i965-va-driver

FfMpeg Support List
https://trac.ffmpeg.org/wiki/HWAccelIntro

On Ubuntu, the guide for setting up QSV is actually just using VAAPI.  
https://wiki.ubuntu.com/IntelQuickSyncVideo 

ffmpeg page for QSV states only Kaby Lake can do HEVC. 
"Encode a 1080p HEVC main10 profile (supported since Kaby Lake platform)"
http://trac.ffmpeg.org/wiki/Hardware/QuickSync

As always, the Arch Wiki lol. It does not mention MSDK or libmfx. 
https://wiki.archlinux.org/index.php/Hardware_video_acceleration

Information on MSDK and libmfx
https://software.intel.com/en-us/articles/quick-start-on-integrating-ffmpeg-libraries

AMF official support.
https://github.com/GPUOpen-LibrariesAndSDKs/AMF/blob/master/README.md

Enabling VAAPI for Intel Processors
https://gist.github.com/Brainiarc7/eb45d2e22afec7534f4a117d15fe6d89

Here's the Programmers Manual for MFX
https://01.org/sites/default/files/documentation/intel-gfx-prm-osrc-kbl-vol08-media_vdbox.pdf

Shows a nice breakdown for ffmpeg. 01.org is Intel's Open Source Technology Center
https://01.org/linuxmedia

https://stackoverflow.com/questions/43898097/how-to-determine-the-specific-h264-encoder-in-use-from-ffmpeg-library

Here is a note on the Ubuntu page about libmfx (MSDK)
```
Future Approach #2: Media SDK ("MSDK")
(This is the approach that the FFmpeg documentation rather confusingly refers to as "Intel QSV")

Intel's Media SDK is the company's professional offering with the aim of providing the highest performance and the most video features all accelerated on Intel chips.

It sounds great. You can download the SDK for free, and they have also published a first open source release of it too. But there are hidden reasons why we can't use any of this yet in Ubuntu. The problem is that pieces are missing. Both of them have a dependency on a custom proprietary fork of LibVA (VA-API). While this "missing" code is actually provided in the commercial download, it requires that you:

Overwrite official Ubuntu files, possibly breaking your system; and
Recompile all your video players yourself; and
Don't redistribute what you've made.
That won't work for us right now. And we don't recommend you try. It's very complicated and can easily break your Ubuntu installation.
```

I haven't checked, but is ffmpeg running with --enable-libmfx --enable-nonfree
This might be required to enable QSV/MFX, testing is needed. 
https://software.intel.com/en-us/articles/accessing-intel-media-server-studio-for-linux-codecs-with-ffmpeg

List of supported codecs
https://github.com/Intel-Media-SDK/MediaSDK
```
Supported video encoders: HEVC, AVC, MPEG-2, JPEG, 
VP9 Supported video decoders: HEVC, AVC, VP8, VP9, MPEG-2, VC1, JPEG 
Supported video pre-processing filters: Color Conversion, Deinterlace, Denoise, Resize, Rotate, Composition
```
http://www.d0wn.com/installing-jellyfin-on-a-rasberry-pi4/

https://www.elpamsoft.com/?p=Plex-Hardware-Transcoding

I can't find much on encoding with DXVA2 / D3D11VA on Windows. Even the QSV page is sparse. I think decoding is only supported.

http://jell.yfish.us/

-----
Current Transcoding issues

https://ffmpeg.org/ffmpeg.html

https://github.com/jellyfin/jellyfin/issues/1364

https://trac.ffmpeg.org/ticket/6472
-max_muxing_queue_size 198

-----
VLC has amazing support for codecs

https://wiki.videolan.org/Hacker_Guide/

https://wiki.videolan.org/Hacker_Guide/VLC_source_tree/

VLC HEVC Encoder Source
https://wiki.videolan.org/H.264/MPEG-4_AVC/

https://git.videolan.org/?p=vlc.git;a=blob;f=modules/codec/x265.c

https://forum.videohelp.com/threads/370018-H-264-vs-x264-and-H-265-vs-x265

https://superuser.com/questions/489087/what-are-the-differences-between-h-264-profiles

MP4 Wrapper
https://wiki.videolan.org/MPEG-4/

https://www.bhphotovideo.com/explora/video/tips-and-solutions/8-bit-10-bit-what-does-it-all-mean-for-your-videos


https://developer.android.com/guide/topics/media/media-formats


https://github.com/UniversalMediaServer/UniversalMediaServer/blob/master/src/main/external-resources/renderers/DefaultRenderer.conf

grep -rnw '/path/to/somewhere/' -e 'pattern'

---JF Expo
https://hackmd.io/s/BkNHM9W0r
---
https://stackoverflow.com/questions/3377300/what-are-all-codecs-and-formats-supported-by-ffmpeg

https://en.m.wikipedia.org/wiki/Comparison_of_video_container_formats

http://ffmpeg.org/ffmpeg-filters.html#overlay-1

https://digitalfortress.tech/tricks/encode-videos-with-ffmpeg/

https://www.techlila.com/compile-android-rom-from-source-code/

https://en.m.wikibooks.org/wiki/FFMPEG_An_Intermediate_Guide/subtitle_options

https://sites.google.com/site/linuxencoding/x264-ffmpeg-mapping

https://trac.ffmpeg.org/wiki/Limiting%20the%20output%20bitrate

https://github.com/sitkevij/ffmpeg/tree/master/ffmpeg-3.4.1-resin-rpi-raspbian

https://docs.brew.sh/Homebrew-on-Linux

https://trac.ffmpeg.org/wiki/CompilationGuide


----AV1

https://trac.ffmpeg.org/wiki/Encode/AV1

https://www.reddit.com/r/AV1/comments/ef4g5l/codecs_performance_report_6th_edition/

https://hackernoon.com/encoding-av1-700b6ee4210

https://github.com/OpenVisualCloud/SVT-AV1

https://streaminglearningcenter.com/codecs/av1-encoding-and-4k.html

https://streaminglearningcenter.com/blogs/good-news-av1-encoding-times-drop-to-near-reasonable-levels.html

https://github.com/OpenVisualCloud/SVT-AV1/blob/master/ffmpeg_plugin/0001-Add-ability-for-ffmpeg-to-run-svt-av1.patch

https://medium.com/@ewoutterhoeven/av1-is-ready-for-prime-time-svt-av1-beats-x265-and-libvpx-in-quality-bitrate-and-speed-31c1960703db
