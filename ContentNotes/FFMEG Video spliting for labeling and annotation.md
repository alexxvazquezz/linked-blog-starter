
How to set up video for cvat labeling and annotation. Since we want to track move t wieh will not separate into images.. rater make videoen smaller chunks

Yes, here’s an ordered approach for segmenting, annotating, and exporting large videos in CVAT:

1. **Segment the Video**: Use `ffmpeg` or another tool to split the large video into smaller, manageable clips (e.g., 1–5 minutes each).
    
2. **Create a Project in CVAT**: Start a project for the whole video sequence.
    
3. **Upload and Annotate**: Upload one segment at a time to CVAT. Complete annotation on each segment before adding the next clip.
    
4. **Export All Together**: After all segments are annotated, export all annotations from the project as a single dataset.
    

This setup keeps your project organized and ready for efficient ML training! Let me know if you’d like help with any specific step.

cutting video, for ecampt just the first half a the game:
```bash
ffmpeg -i input_video.mp4 -ss 00:10:32 -to 00:59:09 -c copy output_video.mp4
```

Splitting a video in chunks by time
```bash
ffmpeg -i "input_file_name.ext" -c copy -map 0 -segment_time 00:05:00 -f segment -reset_timestamps 1 "output_%03d.mkv"
```

1. - Replace `"input_file_name.ext"` with the name of your video file (e.g., `video.mp4`).
    - The output files will be named sequentially as `output_001.mkv`, `output_002.mkv`, etc.
    
2. **Execute the Command**: Press Enter to run the command. FFmpeg will process the video and create multiple 5-minute segments.


Create images from frames
 this makes a video into a video of fps=30 frames per second
```bash
ffmpeg -i input.mp4 -filter:v fps=30 -b:v 2000k output.mp4
```


To split videos into images by fps (frames per second)
```bash
ffmpeg -i input.mp4 -vf fps=25 frame%04d.png
```