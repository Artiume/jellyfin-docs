For Linux, QSV will use the libmfx library (MFX should be the proper term for QSV, MFX uses a modified VAAPI, see notes below). Normal VAAPI will use the libva library.  The Debian link I added shows a list of supported HW for VA-API, we could incorporate this into the guide. 

https://github.com/Intel-FFmpeg-Plugin/Intel_FFmpeg_plugins/wiki 
"QSV transcode acceleration on Linux systems are enabled from FFMPEG 2.8 and forward"

Intel Media Driver
https://github.com/intel/media-driver

AMF is supported on Linux but x265 coding is not. 
https://www.phoronix.com/scan.php?page=news_item&px=FFmpeg-AMD-AMF-Vulkan

VAAPI driver for Intel G45 & HD Graphics family uses the i965 va driver. 
https://packages.debian.org/sid/i965-va-driver

On Ubuntu, the guide for setting up QSV is actually just using VAAPI.  
https://wiki.ubuntu.com/IntelQuickSyncVideo 

ffmpeg page for QSV states only Kaby Lake can do HEVC. 
"Encode a 1080p HEVC main10 profile (supported since Kaby Lake platform)"
http://trac.ffmpeg.org/wiki/Hardware/QuickSync

As always, the Arch Wiki lol. It does not mention MSDK or libmfx. 
https://wiki.archlinux.org/index.php/Hardware_video_acceleration

Information on MSDK and libmfx
https://software.intel.com/en-us/articles/quick-start-on-integrating-ffmpeg-libraries

Here's the Programmers Manual for MFX
https://01.org/sites/default/files/documentation/intel-gfx-prm-osrc-kbl-vol08-media_vdbox.pdf

Shows a nice breakdown for ffmpeg. 01.org is Intel's Open Source Technology Center
https://01.org/linuxmedia

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

I can't find much on encoding with DXVA2 / D3D11VA on Windows. Even the QSV page is sparse. I think decoding is only supported.


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



https://developer.android.com/guide/topics/media/media-formats


https://github.com/UniversalMediaServer/UniversalMediaServer/blob/master/src/main/external-resources/renderers/DefaultRenderer.conf
