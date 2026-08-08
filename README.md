# 萤火 / Lumen Phonia

> 一个基于 p5.js 的生成艺术音频可视化 sketch：乐谱如草叶在暗处生长，萤火环绕，雨落涟漪，光束探入洞穴。
> A p5.js generative audio-visual sketch: sheet music grows like grass in darkness, surrounded by fireflies, rain ripples, and a cave light beam.

---

## 作品概述 / Overview

1. **草叶乐谱 / Botanical Score**
   五线谱从画面底部向上生长，每条谱线模拟草叶的弯曲、尖端下垂和随风摇摆。音符沿谱线滚动，跟随草叶摆动。
   Staff lines grow upward from the bottom, each curving like a blade of grass with drooping tips and wind sway. Notes scroll along and follow the bending.

2. **萤火虫环绕 / Firefly Orbit**
   15 个音乐符号粒子围绕谱表椭圆轨道盘旋，暖金色辉光脉冲闪烁，偶尔随机爆闪。
   15 musical symbol particles orbit the staff area with warm gold glow, pulsing and occasionally flashing.

3. **雨与涟漪 / Rain & Ripples**
   40 条暖金色斜雨丝从左上飘落，触及水面（倒影轴）时生成扁椭圆涟漪并向四周扩散消失。
   40 warm-gold slanted rain streaks fall from upper-left, creating flat elliptical ripples on the water surface.

4. **洞穴光束 / Cave Light Beam**
   从画面顶部中央探入的暖金色锥形光束，多层叠加 + 高斯模糊模拟柔和光感。
   A warm-gold cone of light enters from the top center, layered with Gaussian blur for soft edges.

5. **水面倒影 / Water Reflection**
   以起始小节线为镜面轴，画面内容镜像翻转至下部，逐行水波微扰 + 渐隐模拟水面倒影。
   The canvas is mirrored below the staff baseline with per-row wave distortion and fade-out.

6. **音符迸发火花 / Note Sparks**
   每个音符生成时在屏幕位置迸发 3~6 个音乐符号粒子，向外扩散后淡出消失。

---

## 交互方式 / Interaction

| 操作 / Action | 效果 / Effect |
|---|---|
| 点击画布 / Click canvas | 播放 / 暂停 / Play / Pause |
| 空格键 / Spacebar | 播放 / 暂停 / Play / Pause |
| 自动循环 / Auto-loop | 播放结束后自动从头开始 |

---

## 技术实现 / Technical Details

| 项目 / Item | 内容 / Detail |
|---|---|
| 画布尺寸 / Canvas | 1440 × 1920 px |
| 帧率 / Frame Rate | 24 fps |
| 核心库 / Library | p5.js 1.10 + p5.sound |
| 音频分析 / Audio | p5.FFT（256 bins）+ 自定义 AudioAnalyzer 类 |
| 音乐字体 / Font | music.ttf base64 嵌入（无外部依赖） |
| 旋转布局 / Layout | 270° 旋转变换，乐谱竖向排列 |
| 谱线动画 / Staff | 幂函数弯曲 + 风场 + 波浪传播 + Perlin 噪声微扰 |
| 辉光 / Glow | Canvas shadowBlur 统一暖金色柔光 |

---

## 文件结构 / Files

```
_260808/
  sketch.js      ← 主程序（自包含，可直接粘贴到 p5.js Web Editor）
  index.html     ← 预览页面（CDN 加载 p5.js + p5.sound）
  undercooled.mp3 ← 默认音频文件
  README.md      ← 本文件
```

`sketch.js` 包含内嵌的 `Pitch` 类、`AudioAnalyzer` 类、music.ttf base64 字体数据，以及全部绘制、粒子、效果逻辑，约 1200 行。

---

## 运行方式 / How to Run

1. **本地预览**：用浏览器打开 `index.html`（需同目录下放置音频文件 `undercooled.mp3`）
2. **p5.js Web Editor**：将 `sketch.js` 内容粘贴到编辑器中，上传音频和字体文件（或使用嵌入字体）

---

## 参数自定义 / Customization

`sketch.js` 顶部 "全局参数 CONFIG" 区域集中了所有可调参数：

| 参数组 / Group | 说明 / Description |
|---|---|
| 布局常量 | 画布、谱线间距、音符几何 |
| 颜色参数（Hex） | 背景、谱线、音符、速度标记、小节号 |
| 辉光参数 | 模糊半径、透明度 |
| 五线谱弯曲参数 | 弯曲基数、外侧增量、幂指数、摆动、波浪 |
| 萤火虫参数 | 数量、辉光、速度 |
| 雨水参数 | 数量、雨丝长度、速度、涟漪范围 |

---

## 创作 / Credits

*"Sheet music grows; fireflies dance."*
*"乐谱生长，萤火飞舞。"*
