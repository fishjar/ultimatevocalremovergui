## 安装问题

```sh
2023-05-12 16:12:12,480 - UVR BEGIN
No splash screen.
Traceback (most recent call last):
  File "/home/gabe/code/audio/ultimatevocalremovergui/UVR.py", line 5161, in <module>
    root = MainWindow()
  File "/home/gabe/code/audio/ultimatevocalremovergui/UVR.py", line 889, in __init__
    font.add_file(FONT_PATH)
AttributeError: module 'tkinter.font' has no attribute 'add_file'
```

解决：

- https://github.com/Anjok07/ultimatevocalremovergui/pull/472
- https://github.com/Anjok07/ultimatevocalremovergui/pull/472/commits/52c01acd2be0c4a88bb491568c5b84fe7e56d82e

```sh
- from pyglet import font
+ from pyglet import font
- def cached_source_model_list_check(self, model_list: list[ModelData]):
+ def cached_source_model_list_check(self, model_list: List[ModelData]):
```

## 使用参考

- https://zhuanlan.zhihu.com/p/619606384

### 模型

手工下载，放到 对应目录（VR_Models） 后重启

```sh
#UVR5 在所提供的每个模型都有不同的微调的算法：
⚫ 1_HP-UVR.pth：针对器乐(伴奏)的模型
⚫ 2_HP-UVR.pth：1_HP-UVR.pth 模型的一个微调版
⚫ 3_HP-Vocal-UVR.pth：强化了人声的提取，伴奏的声音可能会很混浊
⚫ 4_HP-Vocal-UVR.pth 这个模型也强化了人声的提取，比前一个模型更激进
⚫ 5_HP-Karokee-UVR.pth 这个模型在去除主要人声的同时保留了背景的人声
#需要额外下载的:
⚫ 6_HP-Karaoke-UVR.pth 这个模型在保留背景人声的同时去掉了主要人。
⚫ 7_HP2-UVR.pth：使用更多数据和新参数训练的强大的器乐模型
⚫ 8_HP2-UVR.pth：器乐模型
⚫ 9_HP2-UVR.pth：8_HP2-UVR.pth 模型的微调版
#窗口大小与力度设置：
Windows Size(窗口大小)：Windows Size 越小， 效果就越好。较小的 Windows Size 意味着 越长的转换时间和越大的资源占用
#以下是可选择的 Windows Size 的值：
⚫ 1024 ：低转换质量， 最短的转换时间，低资源使用率
⚫ 512 ：平均转换质量，平均转换时间， 正常资源使用率
⚫ 320 ：较好的转换质量较长的转换时间较高的资源使用率
#Aggression Setting (力度设置)：这个选项允许你设置去除声音的力度
⚫ 范围是 1-20
⚫ 值越大，就会进行越深度的提取
⚫ 数值过大可能会导致部分乐器变得模糊
```
