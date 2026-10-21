---
name: beds-design-system
description: 'B端企业级设计规范（BEDS v1.0）的落地执行技能。当需要新建或修改后台管理页面/组件、确定颜色/字体/间距/圆角/阴影等设计令牌、生成或修改 CSS 变量与 Tailwind/组件库主题配置、判断某个 UI 实现是否符合团队规范时使用。适用于企业管理后台、数据统计、表格表单密集型系统。主色 #2563EB。'
---

# BEDS 设计系统（B端企业级通用规范）

## 描述

本技能封装团队统一的 B 端设计规范 **BEDS v1.0**，确保 AI 产出的每一个界面在配色、字体、间距、组件形态上保持一致，杜绝"AI 味"的自由发挥。核心是一个蓝色主色 `#2563EB` 的、简约大气的企业级设计令牌体系。

完整规范见 `resources/完整设计规范DESIGN.md`，本文件是其可执行摘要。

## 使用场景

- 新建页面 / 组件 / 模块，需要确定视觉样式
- 生成或修改主题文件、CSS 变量、Tailwind 配置、组件库主题覆盖
- 判断某个颜色、字号、间距、圆角取值是否合规
- 重构已有页面、统一视觉风格

## 指令

### 第 1 步：先加载令牌，再写样式

生成任何样式前，先读取 `resources/完整设计规范DESIGN.md`。**所有色值、字号、间距、圆角、阴影只能从下方令牌中取值，禁止自造数值。**

### 第 2 步：核心令牌速查（必须遵守）

**色彩**

| 语义 | 令牌 | 色值 |
|------|------|------|
| 主色 | `--beds-primary-600` | `#2563EB` |
| 主色 hover / active | `--beds-primary-700` / `-800` | `#1D4ED8` / `#1E40AF` |
| 主色浅底（行 hover / 选中） | `--beds-primary-50` / `-100` | `#EFF6FF` / `#DBEAFE` |
| 页面底 / 容器底 | `--beds-bg-base` / `--beds-bg-container` | `#F5F7FA` / `#FFFFFF` |
| 文字主 / 次 / 弱 | `--beds-text-primary/-secondary/-tertiary` | `#1F2329` / `#4E5969` / `#86909C` |
| 分割线 / 边框 | `--beds-border-1` / `-2` | `#F0F0F0` / `#D9D9D9` |
| 成功 / 警告 / 危险 / 信息 | `--beds-success/-warning/-danger/-info` | `#00B42A` / `#FF7D00` / `#F53F3F` / `#2563EB` |
| 大屏底 / 面板 / 边框 | `--beds-dark-bg-base/-container/-border-2` | `#0D1117` / `#161B22` / `#30363D` |

**图表色板**（顺序不可乱用）：C1 `#2563EB` · C2 `#14C9C9` · C3 `#00B42A` · C4 `#F7BA1E` · C5 `#F53F3F` · C6 `#722ED1` · C7 `#F77234` · C8 `#60A5FA` · C9 `#86909C`

**字体**：正文 `14px/22px`；标题 `28/24/20/16px`；辅助 `12px`；大屏核心数字 `32–48px`。字重仅用 **400 / 500 / 600**。数字一律 `font-variant-numeric: tabular-nums`。

**间距**（严格 4px 网格）：`4 / 8 / 12 / 16 / 24 / 32 / 48`。默认内边距 16px，卡片内边距 24px，页面边距 24px。

**圆角**：Tag `2px`、按钮/输入框/卡片 `4px`、弹窗/大面板 `6–8px`、头像/胶囊 `9999px`。**禁止 12px 以上大圆角。**

**阴影**：卡片默认 `0 1px 2px rgba(0,0,0,0.03)`；hover/下拉 `0 2px 8px rgba(0,0,0,0.08)`；弹窗 `0 4px 16px rgba(0,0,0,0.12)`；焦点环 `0 0 0 2px rgba(37,99,235,0.20)`。

**组件高度**：小 32px / 默认 40px / 大 48px；表格行高默认 48px（紧凑 40px，**不得低于 40px**）；侧边栏 208px（折叠 48px）；顶栏 48/56px。

### 第 3 步：落地实现方式

1. 建立全局 `styles/tokens.css`，把令牌写成 `:root` 下的 CSS 变量；暗色主题在 `[data-theme="dark"]` 下覆盖。
2. 若使用组件库（Ant Design / Element Plus / Arco），通过主题配置把主色覆盖为 `#2563EB`、圆角设为 `4px`，其余令牌映射为对应变量，**不要逐组件手写样式**。
3. Tailwind 项目：在 `theme.extend` 中把上述令牌映射为设计变量，避免直接使用 `blue-500` 之类的原始色阶。

```css
:root {
  --beds-primary: #2563EB;
  --beds-primary-hover: #1D4ED8;
  --beds-primary-active: #1E40AF;
  --beds-bg-base: #F5F7FA;
  --beds-bg-container: #FFFFFF;
  --beds-text-primary: #1F2329;
  --beds-text-secondary: #4E5969;
  --beds-border-1: #F0F0F0;
  --beds-border-2: #D9D9D9;
  --beds-radius-base: 4px;
  --beds-space-base: 16px;
  --beds-font-size-body: 14px;
}
```

### 第 4 步：交付前自检

- [ ] 所有色值均来自令牌，无自造色、无 `blue-500` 等原始色阶
- [ ] 所有间距均为 4 的倍数且落在 4/8/12/16/24/32/48 内
- [ ] 圆角不超过 8px
- [ ] 页面内字重不超过 3 种
- [ ] 数字使用等宽数字特性、右对齐
- [ ] 交互元素均有 hover / focus / disabled 态

## 反面清单（Don't）

- ❌ 大圆角（>8px）、鲜艳渐变、卡通装饰
- ❌ 混用多套色彩体系；主色必须统一为 `#2563EB`
- ❌ 表格行高低于 40px
- ❌ 斜体、艺术字体、非链接的下划线
- ❌ 同一行放超过 3 个主按钮
- ❌ 随意设定间距值（如 5px、13px、18px）
- ❌ 只做默认态，不留 hover / 空态 / 加载态 / 错误态

## 示例

**输入**：给这个后台做一套主题变量。

**输出**：生成 `styles/tokens.css`，`:root` 内定义全部 BEDS 令牌，主色 `#2563EB`；同时生成 `[data-theme="dark"]` 暗色覆盖块；末尾附一段说明，指出组件库应如何映射这些变量。
