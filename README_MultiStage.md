# 📷 PaperTracker 多阶段眼球数据录制工具

这是一个专门用于眼球数据采集的图像录制工具，支持多阶段录制和语音提示功能。

## 🎯 主要功能

### 多阶段录制模式
- **4个不同的录制阶段**，每个阶段针对不同的眼部状态
- **语音提示和倒计时**，优化用户体验
- **自动分文件夹保存**，便于数据分析
- **自动打包压缩**，便于数据传输

### 录制阶段详情

| 阶段 | 描述 | 录制间隔 | 图片数量 | 预计时长 |
|------|------|----------|----------|----------|
| 1 | 正常眨眼：眼睛正常睁开，四处看，正常眨眼 | 300ms | 100张 | ~30秒 |
| 2 | 半睁眼：眼睛半睁开四处看，不眨眼 | 100ms | 40张 | ~4秒 |
| 3 | 闭眼放松：放松状态下闭眼 | 100ms | 20张 | ~2秒 |
| 4 | 快速眨眼：不断快速眨眼 | 50ms | 30张 | ~1.5秒 |

## 🚀 使用方法

### 1. 启动应用
```bash
python demo_multi_stage.py
```

### 2. 连接设备
- 在"设备地址"输入框中输入眼球追踪设备的IP地址和端口
- 点击"连接"按钮建立连接

### 3. 选择录制模式
- **单次录制**：连续录制图片，手动控制开始/停止
- **眼球数据采集**：4阶段自动录制（推荐）

### 4. 开始录制
- 点击"开始眼球数据录制"按钮
- 根据语音提示和屏幕指示完成各阶段动作
- 系统会自动进行阶段切换和倒计时

### 5. 数据输出
录制完成后会自动生成压缩包，包含：
- 各阶段图片文件（分文件夹存储）
- 录制信息JSON文件
- 用户信息和时间戳

## 📁 输出文件结构

```
用户名_eyedata_190pics_2min.zip
├── stage_1_正常眨眼/
│   ├── stage1_正常眨眼_20250725_143001_001_0001.jpg
│   ├── stage1_正常眨眼_20250725_143001_304_0002.jpg
│   └── ... (100张图片)
├── stage_2_半睁眼/
│   ├── stage2_半睁眼_20250725_143032_001_0001.jpg
│   └── ... (40张图片)
├── stage_3_闭眼放松/
│   ├── stage3_闭眼放松_20250725_143036_001_0001.jpg
│   └── ... (20张图片)
├── stage_4_快速眨眼/
│   ├── stage4_快速眨眼_20250725_143038_001_0001.jpg
│   └── ... (30张图片)
└── recording_info.json (录制信息)
```

## 🔧 配置选项

可以通过修改 `recording_config.json` 文件来调整录制参数：

- `interval_ms`: 录制间隔（毫秒）
- `target_count`: 目标图片数量
- `voice_messages`: 语音提示内容
- `countdown_seconds`: 倒计时时长
- `image_quality`: 图片质量（1-100）

## 📊 系统要求

- Python 3.7+
- PyQt5
- OpenCV (cv2)
- NumPy
- Windows操作系统（用于语音提示）

## 🎵 语音提示

系统使用Windows内置的消息提示音：
- 📢 阶段开始：信息提示音
- ⏰ 倒计时：星号提示音  
- ✅ 录制开始/完成：确认提示音

## 🔍 故障排除

### 连接问题
- 确保设备IP地址正确
- 检查网络连接
- 确认设备WebSocket服务正常运行

### 录制问题
- 确保有足够的存储空间
- 检查摄像头权限
- 查看状态栏的错误信息

### 语音提示问题
- 确保系统音量开启
- Windows系统提示音未被禁用

## 📝 更新日志

### v3.2.0 (2025-07-25)
- ✨ 新增多阶段眼球数据录制功能
- 🎵 添加语音提示和倒计时
- 📁 支持分阶段文件夹保存
- 🎯 优化用户体验和界面显示
- 📦 改进数据打包和压缩功能

---

💡 **提示**: 首次使用建议先用单次录制模式熟悉界面，然后使用多阶段模式进行正式的眼球数据采集。
