### Take a video with an audio segment to make a 10 hour repeating video

Requires `sox` and `ffmpeg`

- loopable video is `edit.mp4`, loopable  audio is `edit.wav`

Make a long loop of the audio 

`sox edit.wav edit999.wav repeat 999`

Make a long loop of the video

`ffmpeg -f concat -i <(for i in {1..450}; do printf "file '%s'\n" <full_path_toEdit.mp4> ; done) -c copy output.mp4` 

Combine

`ffmpeg -i output.mp4 -i edit999.wav  -c:v copy -c:a aac -strict experimental -shortest final.mp4`


