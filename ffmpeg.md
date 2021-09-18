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
