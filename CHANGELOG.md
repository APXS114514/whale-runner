# 更新日志 / Changelog

本项目的版本号有两层：`shared/version.js` 里的 **资源版本**（给静态资源破缓存用，见
[README「发布」](README.md)）与这里的 **发布版本**。二者同步递增。

## v1.8.0 — 2026-10-20 · 大厅重做：柜机墙

### 大厅（首页）

- **整体重做**：页面底色换成六款游戏画布里的同一片深海（`#071224`），不再是浅蓝渐变上的白色卡片。
- **首屏**：左边标题、一句话和主按钮；右边一台「柜机」——纸面面板、左上角切一刀，屏幕里是当前选中游戏的预告画面。
- **换台**：柜机下方六个按钮切换预告画面、游戏名、本机最高分和主按钮的落点；键盘 ←/→ 同样可用。
  脚本失效时第一台照常显示，清单里六个「开始游戏」链接始终可用。
- **六台柜机清单**：名字 / 一句话 / 本机最高分 / 去玩，一行一台，悬停有底纹反馈。
- **四个概念**（新增）：词元、上下文、注意力、幻觉四联画，每格配一张真实游戏画面截图和对应游戏入口。
- **收尾**（新增）：一条 Whale Runner 真实游玩录屏（3.4 秒 webm、静音循环、带封面帧）+ 蓝色 CTA 区块。
- **字体**：全站换成 Archivo（自托管拉丁子集 35KB，SIL OFL 1.1，零外部请求），中文按字符回落系统黑体；
  同时移除了等宽字体。
- **文案**：音效 / 角色 / 语言三个按钮与角色名去掉 emoji，改用文字；新增像素鲸鱼字标（从 `shared/whale.js` 同一份素材导出）。
- **动效**：柜机快门式入场、分区逐个上浮、悬停与焦点反馈；全部尊重 `prefers-reduced-motion`。

### 公共层

- `shared/arcade.css`：加入 Archivo `@font-face`；清掉 5 个已无人引用的设计变量。
- `shared/i18n.js`：新增柜机墙文案（中英各一套），控件标签去 emoji。
- `shared/version.js`：资源版本 1.7.1 → **1.8.0**（七个页面的 `?v=` 已同步）。

### 素材与许可

- 新增 `assets/lobby/`：像素鲸鱼字标、四张概念区截图、真实游玩录屏。
- 新增 `assets/fonts/archivo-latin.woff2` 与 `LICENSES/Archivo-OFL.txt`；
  `THIRD_PARTY_NOTICES.md` 增加字体一节。

### 测试

- 逻辑断言 **1882 / 1882** 通过；真实浏览器冒烟 **46 / 46** 通过。
- 因按钮文案去 emoji、大厅结构改为柜机墙，同步更新了对应断言（判定意图不变）；
  `browser-smoke` 仍校验「六台柜机 / 六个入口 / 六张预告画面」与 `--accent-fill`。

### 兼容性

- 玩法、关卡、存档键、游戏页行为**均未改动**。
- `file://` 双击打开依旧可用（字标、字体、预告画面、换台都验证过）。

## 1.8.0 — English summary

- The lobby is now a dark **cabinet wall** built on the same deep-sea palette as the six games.
- One cabinet screen plays the selected game's attract art; six tabs switch the screen, title,
  best score and where the primary button goes. Keyboard arrows work; it degrades to the first
  cabinet without JavaScript and every "play" link always works.
- New "four ideas" band (tokens / context / attention / hallucination) with real in-game screenshots,
  and a 3.4 s recorded gameplay loop as the closing band.
- Archivo (self-hosted Latin subset, SIL OFL 1.1) is now the site typeface; emoji removed from the
  sound / character / language controls.
- Gameplay, level data, storage keys and the six game pages are unchanged.
