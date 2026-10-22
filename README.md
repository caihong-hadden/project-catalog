# 项目总览 · Project Catalog

> 一份持续维护的个人工程清单：**全栈 Web / 微信小游戏 / 嵌入式固件 / AI 工具链 / 内容渲染管线**。
> 每一条都对应一个真实存在、能跑起来的本地工程，不是课程作业目录。

**English** — A living catalog of personal engineering work: full-stack web apps, WeChat mini games, embedded firmware, AI tooling, and a deterministic frame-by-frame video pipeline.

---

## 关于这份清单

- **路径说明**：文中 `F:/...`、`~/.gemini/antigravity/scratch/...` 均为本机工作区位置，`~` 指本机用户目录。这些是索引，不是下载链接。
- **开源状态**：标注「已开源」的项目可直接访问仓库；其余工程含硬件私有依赖或第三方平台凭据，需要时会整理后单独开源。
- **维护方式**：新项目完成后追加一节，同步更新末尾的快速索引表。

### 已开源的代码仓库

| 仓库 | 内容 | 主要技术 |
| :--- | :--- | :--- |
| [smart-component-inventory](https://github.com/caihong-hadden/smart-component-inventory) | 智能元器件库存与 BOM 配单系统 | React · TypeScript · FastAPI · SQLite |
| [token-cat-nest](https://github.com/caihong-hadden/token-cat-nest) | 3D 猫咪互动社区 | React · Three.js · Cloudflare D1/R2 |
| [smart-lyrics-generator](https://github.com/caihong-hadden/smart-lyrics-generator) | 歌词逐句打轴与双向联动播放器 | Whisper · Python · Web |
| [tc264-gesture-car](https://github.com/caihong-hadden/tc264-gesture-car) | 手势控制小车核心模块 | AURIX TC264 · I2C · 串级 PID |
| [windows-drive-migration](https://github.com/caihong-hadden/windows-drive-migration) | 系统盘无损迁移套件 | PowerShell · NTFS Junction |
| [local-vision-api](https://github.com/caihong-hadden/local-vision-api) | 本地多模态视觉服务 | Python · HTTP · 视频抽帧 |
| [docx-quiz-parser](https://github.com/caihong-hadden/docx-quiz-parser) | Word 题库解析与刷题页 | Python · 原生 JS |
| [word-machine](https://github.com/caihong-hadden/word-machine) | 桌面背单词机 | Python · SQLite |
| [dot-matrix-debugger](https://github.com/caihong-hadden/dot-matrix-debugger) | 点阵屏取模工具 | 单文件 HTML/JS |
| [cet4-diagnostic](https://github.com/caihong-hadden/cet4-diagnostic) | 四级分维度诊断单页 | 单文件 HTML |

> 其余工程（嵌入式实验库、视频渲染管线、桌面自动化等）在陆续整理开源中，代码需先做依赖裁剪与脱敏。

---

## 零、快速索引（10 个代表作）

| # | 项目 | 核心技术栈 | 一句话价值 |
| :---: | :--- | :--- | :--- |
| 01 | **Token 的小窝**（猫咪全栈社区） | React · Three.js · Cloudflare Pages / D1 / R2 | 前端 3D 交互 + 全 Serverless 后端，零运维成本上线 |
| 02 | **微信摸鱼物理小游戏** | 微信小游戏 · Canvas · Matter.js · 云开发 | 物理引擎 + 跨用户实时排行榜 + 合规隐私弹窗 |
| 03 | **智能元器件库存系统** | FastAPI · SQLModel · SQLite · React · TS | 把硬件工程经验编码成软件规则，已开源 |
| 04 | **C 盘智能研判与迁移套件** | PowerShell · NTFS Junction · Python | 两阶段完整性校验的无损目录迁移，可回滚 |
| 05 | **TC264 手势控制智能车** | Infineon AURIX · I2C 驱动 · 双闭环 PID | 手势识别 + 编码器测速 + 串级 PID 的完整闭环 |
| 06 | **ESP32-S3 根系损伤探测** | ESP32-S3 · FreeRTOS · DSP 滤波管线 | 微弱阻抗信号的实时采集与诊断 |
| 07 | **悬浮 Token 监视器** | Python · Win32 GUI · PyInstaller | 独立 exe，免环境依赖的运行态监控 |
| 08 | **Vibe 科普视频渲染管线** | HTML5 Canvas · Chrome CDP · NVENC | 确定性逐帧截图 + 60 FPS 母带合成，12 支成片 |
| 09 | **51 / STM32 实验库** | Keil C51 · STM32CubeIDE | 20 个递进实验，从流水灯到 BLE 上报 |
| 10 | **点阵屏可视化调试器** | 单文件 HTML / JS | 点格子自动生成 C 字模数组，嵌入式提效工具 |

---

## 一、全栈 Web 与云原生

### 1. Token 的小窝（Token Cat Nest）

- **做什么**：给三花猫「Token」做的 3D 萌宠互动 + 喂养打卡全栈社区，含在线喂食记录、心愿留言板、相片瀑布流、背景音效与管理员认证后台。
- **技术栈**：Vite · React · TypeScript · Three.js · Cloudflare Pages / Functions / D1 / R2
- **关键点**：三维猫咪模型与用户操作状态联动；后端完全跑在 Serverless 生态，认证与媒体存储走 D1 + R2，没有常驻服务器。
- **路径**：`F:/token`（工作区镜像：`~/.gemini/antigravity/scratch/token-cat-nest`）
- **核心文件**：`src/App.tsx`、`src/components/ThreeCatScene.tsx`、`functions/api/status.ts`、`migrations/0001_init.sql`

### 2. 智能电子元器件库存管理系统（Smart Component Inventory）

- **做什么**：面向硬件工程师的本地化元器件库存、规格参数与视觉识别管理系统；含分类筛选、出入库日志、阈值预警与一键免配置启停脚本。
- **技术栈**：Python · FastAPI · SQLModel · SQLite · React 18 · TypeScript · Vite · Tailwind
- **关键点**：替代料门禁把硬件经验写成可执行规则（封装阶梯、晶振匹配容值、肖特基功率分级、连接器公母隔离）；标签识别走三引擎并行竞速（浏览器端 `BarcodeDetector` / `zxing-wasm` / 后端 PIL 二值化）。
- **路径**：`F:/workbuddy/inventory-system`（交付归档：`F:/Smart-Component-Inventory-v1.0`）
- **开源**：已开源 → <https://github.com/caihong-hadden/smart-component-inventory>

### 3. 智能歌词 / 字幕生成与播放器（Smart Lyrics Generator）

- **做什么**：音频与视频的自动识别 + 双向交互播放系统。
- **技术栈**：Python · 离线 Whisper · Web 前端（时间轴联动）
- **关键点**：Whisper 离线推理逐句打时间戳；播放进度反向驱动歌词高亮，点击歌词又反向 Seek 音频，形成双向联动而非单向滚动。
- **路径**：`~/.gemini/antigravity/scratch/review/smart-lyrics-generator`（演进版：`review2`、`review3`）

### 4. AuraText 交互原型与使用手册

- **做什么**：写作工具的单文件前端视觉原型：极简风格展示页、注册交互原型、中英文排版规范说明书。
- **技术栈**：纯静态 HTML / CSS、Word 文档
- **路径**：`F:/AuraText` → `AuraText.htm`、`auratext_register.html`、`AuraText使用说明书.docx`

---

## 二、微信小游戏生态

### 微信摸鱼小游戏（Moyu Mini Game）

- **做什么**：面向微信平台的 2D 物理碰撞消除类休闲游戏。
- **技术栈**：微信小游戏 · Canvas 原生渲染 · Matter.js · 微信云开发（云函数 / 数据库）
- **关键点**：云函数做 IP 属地动态解析与跨用户实时排行榜；内建符合微信 v1031 规范的隐私协议弹窗管理模块，过审不需要临时补丁。
- **路径**：`F:/wechatmini`（工作区联接：`~/.gemini/antigravity/scratch/moyu_game`）
- **核心文件**：`game.js`、`src/gameCore.js`、`src/privacyManager.js`、`src/cloudService.js`

---

## 三、Vibe 知识科普视频逐帧渲染管线

> 一套知识可视化的全自动制作矩阵，风格取 Linear / Apple 的极简科技感。
> 每一幕用 HTML5 Canvas 状态机构建虚拟摄像机轨迹与动效，通过无头 Chrome CDP **确定性逐帧截图**，再由 NVENC 硬件编码合成 60 FPS 母带，叠加环境音效与旁白卡点。

**为什么不用传统剪辑**：逐帧渲染意味着任何一帧都可复现、可 diff，改一行参数只重跑受影响的片段，而不是重剪整条片子。

- **管线原型与 60 FPS 抓帧测试**：`~/.gemini/antigravity/scratch/vibe_project`、`vibe_test`
- **对标与竞品分析**：`~/.gemini/antigravity/scratch/vibe_benchmark_analysis`（热门科普短视频的叙事结构与节奏采样）

**已产出的成片工程（12 支）**

| 主题 | 内容 | 目录 |
| :--- | :--- | :--- |
| 《知识的诅咒》 | 沟通隔阂与认知壁垒（含 60 s 成片与分镜脚本） | `curse_of_knowledge` |
| 《达克效应》 | 愚昧之山与绝望之谷的认知曲线 | `dunning_kruger_vibe` |
| 《熵增定律》 | 热力学与人生混乱度的对抗 | `entropy_vibe` |
| 《飞轮效应》 | 从极难启动到势不可挡的旋转模型 | `flywheel_effect_vibe` |
| 《男女沟通思维差异》 | 「解决问题 vs 情感共情」双轨、横竖屏双版本 | `gender_communication_vibe` |
| 《习得性无助》 | 塞利格曼实验与破局路径 | `learned_helplessness_vibe` |
| 《光刻机与纳米制程》 | 掩膜版 → EUV → 晶圆曝光 | `lithography_vibe` |
| 《大脑低功耗模式》 | 认知带宽节约与专注恢复（含最终母带） | `neural_low_power_vibe` |
| 《聚光灯效应》 | 社交焦虑与焦点错觉 | `spotlight_effect_vibe` |
| 《以牙还牙》 | 阿克塞尔罗德重复囚徒困境的最优策略 | `tit_for_tat_vibe` |
| 《海森堡测不准原理》 | 微观不确定性与动量测量 | `uncertainty_vibe` |
| 《局部最优解与认知突围》 | 含人体微血管流动与子弹射击粒子动效 | `vibe_local_optima` |

---

## 四、嵌入式硬件与单片机工程

### 1. Infineon AURIX TC264 手势控制与自动跟随小车

- **做什么**：手势控制的微型移动小车，支持挥手启停转向、超声波 / 激光避障、自动跟随。
- **技术栈**：Infineon AURIX TC264 · C · I2C（PAJ7620）· 正交编码器 · 双闭环 PID
- **关键点**：自己写 PAJ7620 手势传感器驱动（I2C 时序 + 中断上报）；编码器脉冲采集做速度环，方向做转向环，串级 PID 同时压住速度波动与航向漂移。
- **路径**：`~/.gemini/antigravity/scratch/tc264_gesture_car`（完整 ADS 工程：`F:/TC264_Crazy_Circuit_Promax (2)`）
- **核心文件**：`include/car_config.h`、`include/paj7620.h`、`src/pid.c`

### 2. 基于 ESP32-S3 的植物根系损伤阻抗探测系统

- **做什么**：用生物电阻抗判断植物根系受损程度的检测工程。
- **技术栈**：ESP32-S3 · FreeRTOS · C · DSP（数字滤波 / 复数变换）
- **关键点**：微弱土壤阻抗信号极易被工频与开关噪声淹没，用多级滤波管线 + 复数域变换把幅相信息分离出来，再按任务优先级拆分采集与运算线程。
- **路径**：`F:/基于ESP32-S3的根系损坏探测项目`
- **核心文件**：`dsp_pipeline.c`、`dsp_math_utils.c`、`freertos.c`

### 3. 51 单片机与 STM32 教学实验库

- **做什么**：系统化的单片机实验合集，20 个递进式实验 + 两个扩展工程。
- **技术栈**：Keil C51（STC89C52 / STC15）· STM32CubeIDE · I2C（AHT20）· BLE · PWM 舵机
- **覆盖内容**：流水灯、矩阵按键、数码管动态扫描、8×8 点阵字模、外部中断与定时器；扩展 `AHT20_BLE` 温湿度蓝牙上报与 `SERVO_TEST` 舵机控制。
- **路径**：`E:/Desktop/工具箱/单片机文件`

### 4. RTX 4090 显卡风扇测控工程

- **做什么**：针对显卡散热模块的风扇固件与测控分析。
- **内容**：PWM 调速 HEX 固件解析、引脚线序映射、硬件高清图集。
- **路径**：`~/.gemini/antigravity/scratch/4090FAN`

---

## 五、系统工程、自动化与 AI 工具

### 1. C 盘智能研判与迁移清理套件（Jev Disk Cleaner）

- **做什么**：把微信大文件、缓存与桌面目录无损迁移到大容量数据盘，缓解系统盘爆满。
- **技术栈**：PowerShell · NTFS Junction · Python
- **关键点**：迁移前做两阶段完整性校验（数量 + 内容哈希），再建目录联接，失败可整体回滚；风险等级由 System One 常识模型做多维研判，无人值守场景单独标注。
- **路径**：`F:/C-Clean`（实验目录：`~/.gemini/antigravity/scratch/jev_disk_cleaner`）
- **核心文件**：`Migrate-Junctions.ps1`、`jev_evaluate.py`、`sync_and_junction_desktop.py`

### 2. Antigravity 悬浮 Token 监视器

- **做什么**：桌面半透明悬浮窗，实时监控会话与模型 Token 消耗。
- **技术栈**：Python · Win32 GUI · PyInstaller
- **关键点**：置顶但不抢焦点，低占用常驻；打包成独立 exe，目标机不需要 Python 环境。
- **路径**：`~/.gemini/antigravity/scratch/antigravity-token-monitor`
- **核心文件**：`floating_widget.py`、`token_engine.py`、`AntigravityTokens_x64.exe`

### 3. 本地多模态视觉 API 服务

- **做什么**：给不支持多模态输入的模型补一个图像理解与视频帧解析入口。
- **技术栈**：Python · HTTP 服务 · 视频帧抽取
- **路径**：`~/.gemini/antigravity/scratch/vision-api`
- **核心文件**：`vision_server.py`、`video_analyzer_v2.py`、`start.bat`

### 4. 桌面自动化驱动（Computer Use）

- **做什么**：基于模型上下文协议（MCP）接管 Windows 的自动化框架，用屏幕图像理解驱动跨应用操作。
- **技术栈**：Python · MCP · 屏幕捕获与图像分析
- **路径**：`~/.gemini/antigravity/scratch/computer_use`
- **核心文件**：`driver.py`

### 5. SolidWorks 自动化与三维建模工具库

- **做什么**：通过 Windows COM 接口连接正在运行的 SolidWorks 实例，用 Python 脚本自动构建实体特征。
- **技术栈**：Python · SolidWorks COM API
- **关键点**：不用打开界面重跑脚本，直接挂在已运行实例上增量建模；含实例探测与打孔 / 参数化拉伸等常用特征封装。
- **路径**：`~/.gemini/antigravity/scratch/solidworks_study`
- **核心文件**：`create_frustum_hole.py`、`detect_solidworks.py`

---

## 六、辅助学习与调试工具

| 项目 | 说明 | 技术栈 | 路径 |
| :--- | :--- | :--- | :--- |
| **8×8 点阵屏可视化调试器** | 点格子画图案，侧栏调色，下方同步生成 C 字模十六进制数组与坐标 | 单文件 HTML / JS | `~/.gemini/antigravity/scratch/dot-matrix-debugger/index.html` |
| **极简背单词机** | 生词本分类、词典一键导入、复习曲线判定 | Python GUI · SQLite | `~/.gemini/antigravity/scratch/simple_word_machine` |
| **课程题库在线刷题平台** | Word 试题文档自动解析、按章节切分、单选/多选/判断即时判分与错题汇总 | Python · 单页 Web | `~/.gemini/antigravity/scratch/maogai-quiz` |
| **CET-4 诊断自测单页** | 听力 / 词汇 / 阅读分维度快速模考与薄弱点反馈 | 单文件 HTML | `~/.gemini/antigravity/scratch/cet4_diagnostic/index.html` |
| **CTF 逆向与密码学工作区** | AES ECB 模式泄露还原、Python 字节码逆向、图片隐写提取 | Python · 密码学脚本 | `~/.gemini/antigravity/scratch/ecb_leakage`、`gulu_out` |

---

## 七、技术栈总览

| 领域 | 语言 / 框架 / 工具 |
| :--- | :--- |
| **嵌入式** | C、ESP-IDF、FreeRTOS、STM32 HAL / 标准库、Infineon AURIX、Keil C51、DSP 滤波、PID |
| **前端** | TypeScript、React、Vite、Tailwind、Three.js、Canvas / WebGL、单文件 HTML 原型 |
| **后端** | Python、FastAPI、SQLModel、SQLite、Cloudflare Workers / D1 / R2、微信云开发 |
| **AI 工程** | PyTorch、Transformers、PEFT / QLoRA、Whisper、本地 OCR / 视觉模型推理服务 |
| **系统与自动化** | PowerShell、NTFS Junction、Windows COM、MCP、PyInstaller、批处理 |
| **内容管线** | Chrome DevTools Protocol、逐帧渲染、NVENC 硬件编码、FFmpeg |
| **硬件设计** | SolidWorks、EasyEDA、BOM 与供电链路核算 |

---

## 八、持续更新

- 新工程完成后追加到对应分类，并同步刷新顶部快速索引表。
- 每个条目至少写清三件事：**做什么、用了什么、难在哪**。只列「做过」不写「难在哪」的条目会被删掉。

---

<sub>本清单由本地工作区自动汇总整理，持续维护中。</sub>
