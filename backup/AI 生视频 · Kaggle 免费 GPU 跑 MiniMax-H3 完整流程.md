# Kaggle 免费跑 MiniMax-H3（音视频同步、嘴型对齐）ComfyUI 教程
>- 0 元白嫖 AI 生视频 
>- Kaggle 免费 GPU 跑 MiniMax-H3 完整流程
>- 本文 + 一键包，全程不花一分钱。本地电脑 0 配置、0 安装。

## 为什么写这篇？

MiniMax-H3 不一样 —— 它是视频 + 音频一起生成（人物说话，嘴型和声音对得上），模型一共 32.02 GB：

| 文件 | 大小 | 作用 |
| ---- | ---- | ---- |
| MiniMax-H3-Ref2VA-Pruned-Q4_K_M.gguf | 11.56 GB | H3 主模型（视频+音频） |
| Qwen3-VL-32B-Instruct-MiniMax-H3-L0-49-IQ4_XS.gguf | 13.44 GB | 文本编码器 |
| Qwen3-VL-32B-Instruct-MiniMax-H3-L0-49-mmproj-BF16.gguf | 1.20 GB | 视觉投影 |
| minimax_h3_video_vae_fp16.safetensors | 5.21 GB | 视频 VAE |
| minimax_h3_audio_vae_fp32.safetensors | 605.25 MB | 音频 VAE |
| **合计** | **32.02 GB** | |

32 GB 装不进 19.5 GB 的磁盘 —— 这就是绝大多数人卡住的地方。

这帖的解法：把模型传成 Kaggle Dataset 挂载 —— 不占 Notebook 磁盘。

## 这帖解决什么
✅ 突破 Kaggle 19.5 GB 磁盘限制（Dataset 挂载 + 软链接）
✅ 一键包下载，代码不用手抄
✅ 自动开隧道、自检节点、固定 ComfyUI 版本
✅ 全程 0 元（GPU 免费 30 小时/周，Dataset 存储也免费）

## 3 步流程
### Step 1：注册 Kaggle
打开 https://www.kaggle.com/ 注册（完全免费）
不需要绑卡，不需要翻墙
邮箱 + Google 账号即可

💡 手机号验证：第一次开 GPU 时 Kaggle 会要求手机号验证（防滥用）—— 中国 +86 手机号也可以，验证后永久免费。

### Step 2：把 5 个模型传成 Dataset
这一步是本帖的核心。模型不进 Notebook 磁盘，进 Dataset —— 所以不受 19.5 GB 限制。

Kaggle 右上角 → Datasets → + New Dataset
名字建议填 `minimaxh3`，可见性选 **Private（别公开）**
上传那 5 个文件（下载地址在下面第 4 节，全部实测可访问）
上传完点 New Version → 勾选 Make dataset available（这句决定能不能挂载）

⚠️ 这一步最花时间：32 GB 上传，看网速，建议睡前传。
5 个文件一个都不能少，名字必须完全一致（大小写敏感）。

### Step 3：开 Notebook 跑脚本
New Notebook → Add Input → 选你刚传的 Dataset
Settings → Accelerator 选 **GPU T4×2、Internet On**
点 + Code，把 `1.Kaggle一键运行.py` 整个粘进去
改第 7 行：把 `casper62985/minimaxh3` 换成你自己的
Run All，等 5-10 分钟出链接

💡 第 7 行填错也能跑 —— 脚本下面会自动在 `/kaggle/input` 里扫描兜底。

## 📥 一键包下载
🔗 https://tools.zaihouse.com/downloads/minimax-h3-kaggle.zip
（右键“另存为”即可 —— 比从网页复制长脚本靠谱，少一行就报错）

