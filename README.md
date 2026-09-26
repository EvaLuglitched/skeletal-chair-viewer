# Skeletal Chair 3D 查看器

Skeletal Chair（骷髅椅）的在线 3D 查看器。用 GitHub Pages 托管，再用 iframe 嵌入 Squarespace。和鸟屋、VIPER 查看器是各自独立的项目。

## 文件夹里有什么

| 文件 | 作用 |
|---|---|
| `index.html` | 查看器页面 |
| `chair.glb` | 压缩后的椅子模型，1.0 MB（传输约 0.8 MB）。来自 chair123.3dm 的 A 椅：弯折钢筋框架、鱼嘴对接的横撑、TIG 焊缝、脚垫、座板和靠背 |
| `vendor/three/` | three.js 本地副本（MIT 协议）。网站不依赖任何外部 CDN，可以长期稳定运行 |
| `.nojekyll` | 让 GitHub Pages 原样发布文件，不要删 |

## 一、用 VS Code 发布到 GitHub（只需做一次）

1. 在 VS Code 里打开 `skeletal-chair-viewer` 这个文件夹。它已经是一个 git 仓库，第一次提交也已经做好了。
2. 点左侧的 **Source Control**（分叉图标，或按 ⌃⇧G），再点 **Publish Branch**（或 **Publish to GitHub**）。
   - 选 **Publish to GitHub public repository**。仓库名保持 `skeletal-chair-viewer` 就行。
3. 打开 GitHub 上的这个仓库，进入 **Settings → Pages**：
   - Source 选 **Deploy from a branch**。
   - Branch 选 **main**，文件夹选 **/ (root)**，然后点 **Save**。
4. 等一两分钟，页面顶部会显示网址：`https://你的用户名.github.io/skeletal-chair-viewer/`。

## 二、嵌入 Squarespace

在页面里添加一个 **Code** 模块，粘贴下面这段代码（把网址换成上一步得到的地址），并关掉 **Display Source**：

```html
<div style="position:relative;width:100%;height:80vh;min-height:520px;">
  <iframe src="https://你的用户名.github.io/skeletal-chair-viewer/"
          title="Skeletal Chair 3D viewer"
          loading="lazy"
          allow="fullscreen"
          style="position:absolute;inset:0;width:100%;height:100%;border:0;"></iframe>
</div>
```

## 三、以后怎么更新

改完文件后，在 **Source Control** 里写一句说明，点 **Commit**，再点 **Sync Changes**。一两分钟后网站和 Squarespace 页面都会更新。

## 查看器功能

- **视角：** Overall、Side（侧面）、Seat（座面）、Back（背面）、Welds（焊缝）、Stretcher（横撑）、Feet（脚）。Welds、Stretcher、Feet 三个近景会自动切换到线稿模式，焊缝看得更清楚。
- **显示模式：** X-ray（透视）和 Drawing（线稿）。线稿模式下，座板和靠背是半透明的，能看到下面的钢筋框架和螺丝。
- **Explode（爆炸图）：** 座板和靠背连同支架、螺丝一起分开；椅腿、横撑、焊缝和脚垫保持不动。
- **缩放不会抢走页面滚动：** 桌面端用 ⌘/Ctrl + 滚轮、触控板双指捏合，或 +/− 按钮。手机上先点 “Tap to interact” 才能旋转和缩放。
- **流畅：** 只有拖动、切换或调滑杆时才渲染，静止时几乎不占 CPU 和 GPU。
