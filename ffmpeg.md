# FFmpeg Command Line

## Using CUDA

### Full hardware transcode with NVDEC and NVENC:
```bash
ffmpeg -hwaccel cuda -hwaccel_output_format cuda -i input -c:v h264_nvenc -preset slow output
```

### ffmpeg was compiled with support for libnpp, it can be used to insert a GPU based scaler into the chain:
```cmd
ffmpeg -hwaccel_device 0 -hwaccel cuda -i input -vf scale_npp=-1:720 -c:v h264_nvenc -preset slow output.mkv
```
The `-hwaccel_device` option can be used to specify the GPU to be used by the hwaccel in ffmpeg.

### FHD 1080p 60FPS Dolby Digital 5.1 -Setting
```bat
@echo off

echo "Using CUDA to enhance FHD1080p with 60 FPS and Dolby Digital 5.1"
set input=%1
set output=%2
set def="1080p F60 5.1"

ffmpeg -hwaccel_device 0 -hwaccel cuda -i "%input%" -vf scale=-1:1080 -r 60 -c:v hevc_nvenc -preset slow -ac 6 -map 0 -c:a ac3 "FHD_60FPS_DolbyDigital_%output%"
```
