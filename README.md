# ffplay-cmake
ffplay cmake工程


## 用法

### 播放一个mp4文件
```
./ffplay -i /work/video/test.mp4
```

### 播放一个h264/h265文件
```
/ffplay -i /work/video/venc/3840x2160_8bit.h264
/ffplay -i /work/video/venc/3840x2160_8bit.h265
```

### 播放一个yuv420p的文件
```
./ffplay -f rawvideo -video_size 3840x2160 -pixel_format yuv420p /work/video/venc/3840x2160_8bit.yuv

```

