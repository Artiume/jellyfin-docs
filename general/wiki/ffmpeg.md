How to use ffmpeg<br>
https://www.ostechnix.com/20-ffmpeg-commands-beginners/

https://devblogs.nvidia.com/nvidia-ffmpeg-transcoding-guide/


https://github.com/Diagonactic/plex-new-transcoder/blob/3cf85fd34bfa94f679ca934ebf9e2a31ff0bb0eb/plex-ffmpeg-source/NewPlexTranscoder/fftools/ffmpeg.c#L1788-L1866

https://github.com/Diagonactic/plex-new-transcoder/blob/3cf85fd34bfa94f679ca934ebf9e2a31ff0bb0eb/plex-ffmpeg-source/NewPlexTranscoder/fftools/ffmpeg.c#L4649-L4653

https://manpages.debian.org/experimental/ffmpeg/ffmpeg.1.en.html

SAR and DAR
https://ffmpeg.org/ffmpeg-filters.html#setdar_002c-setsar

https://stackoverflow.com/questions/45396813/ffmpeg-copyts-makes-t-stop-at-timestamps-not-duration

The different types of codecs<br>
https://write.corbpie.com/ffmpeg-list-all-codecs-encoders-decoders-and-formats/

https://stackoverflow.com/questions/22710099/ffmpeg-create-blank-screen-with-text-video#22719247

HDR Color Matrixg<br>
https://arstechnica.com/civis/viewtopic.php?t=1403375

[Chomra Subsampling](https://trac.ffmpeg.org/wiki/Chroma%20Subsampling) 

https://trac.ffmpeg.org/wiki/colorspace

https://www.projectorcentral.com/chroma-subsampling-explained.htm

Notes on HDR<br>
https://github.com/jellyfin/jellyfin/issues/2404#issuecomment-586043667

https://web.archive.org/web/20190722004804/https://stevens.li/guides/video/converting-hdr-to-sdr-with-ffmpeg/

https://wiki.archlinux.org/index.php/Hardware_video_acceleration

https://stackoverflow.com/questions/58994428/is-there-any-way-to-specify-streams-by-pid-with-ffmpeg-if-the-value-of-pid-is-d

---
Extra notes:
ffmpeg php wrapper
https://github.com/soluble-io/soluble-mediatools

splitting<br>
https://www.reddit.com/r/ffmpeg/comments/fadjj6/how_to_split_long_mp4_video_into_smaller_25_min/

recursive looper<br>
https://ss64.com/nt/for_r.html

https://superuser.com/questions/939357/how-to-position-drawtext-text

https://ffmpeg.org/ffmpeg-filters.html#drawtext

https://stackoverflow.com/questions/3169916/can-ffmpeg-burn-in-time-code

https://stackoverflow.com/questions/24961127/how-to-create-a-video-from-images-with-ffmpeg

https://stackoverflow.com/questions/22710099/ffmpeg-create-blank-screen-with-text-video#22719247

https://github.com/dyne/frei0r

https://stackoverflow.com/questions/42980663/ffmpeg-high-quality-animated-gif

https://stackoverflow.com/questions/24961127/how-to-create-a-video-from-images-with-ffmpeg

[the guide on H.265/HEVC encoding](http://trac.ffmpeg.org/wiki/Encode/H.265

ffmpeg -f lavfi -i color=c=172138:s=480x320:d=30 -vf "\
drawtext=fontfile=/path/to/font.ttf:fontsize=20: \
fontcolor=white:boxcolor=black:x=(w-text_w)/2:y=10:text='%{pts\:hms}', \
drawtext=fontfile=/path/to/font.ttf:fontsize=30: \
fontcolor=white:x=(w-text_w)/2:y=(h-text_h-text_h)/2:text='Jellyfin Sample', \
drawtext=fontfile=/path/to/font.ttf:fontsize=30: \
fontcolor=white:x=(w-text_w)/2:y=(h+text_h)/2:text='H264 8-bit' \
" -c:v libx264 output3.mp4

https://www.reddit.com/r/ffmpeg/comments/g6omt1/create_new_audio_stream_from_current_within_same/fobhyvo

https://el-tramo.be/blog/ken-burns-ffmpeg/

https://www.reddit.com/r/ffmpeg/comments/g3b7nl/audio_goes_out_of_sync_when_merging_two_audio/

http://dranger.com/ffmpeg/tutorial01.html

https://www.reddit.com/r/ffmpeg/comments/gbow93/is_it_possible_to_inject_a_new_vf_during_a_stream/

https://www.reddit.com/r/ffmpeg/comments/gbo4l4/delete_older_part_of_recording_while_still/fp7r633
