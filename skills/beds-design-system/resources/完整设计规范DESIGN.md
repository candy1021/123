# B-End Enterprise Design System (BEDS)
# B端企业级通用设计规范 v1.0

> 适用场景：企业后台管理系统、数据大屏、表格表单密集型B端项目
> 设计风格：简约大气、高信息密度、现代专业
> 团队适配：前后端+设计一人团队，组件可直接复用，降低沟通成本

---

## 1. 设计理念与视觉基调

### 1.1 设计哲学

本设计系统融合 IBM Carbon 的工程严谨性、Ant Design 的B端实战经验与现代SaaS的简约美学，以**高效信息传递**为核心目标：

- **简约而不简单**：克制的色彩使用，大面积留白与清晰的层级划分
- **数据友好**：表格、表单、图表是第一公民，信息密度优先于装饰性
- **开发友好**：统一的 Design Token，所有组件基于8px网格，CSS变量直接复用
- **双主题支持**：默认浅色主题（管理后台）+ 暗色主题（数据大屏），一套Token切换
- **零设计债务**：圆角、阴影、间距全部标准化，杜绝"差不多"的随意值

### 1.2 核心特征

- **主色**：科技蓝 `#2563EB` —— 专业、可信、B端经典选择
- **字体**：系统字体栈优先，中文用 PingFang SC / Microsoft YaHei，英文用 Inter / -apple-system
- **圆角体系**：4px/6px/8px —— 适度圆润，既不生硬（0px）也不随意（大圆角）
- **深度系统**：克制的阴影层级，通过背景色分层+轻量阴影表达深度
- **间距系统**：严格8px基准网格，所有padding/margin/gap均为4的倍数
- **组件高度**：32px(小)/40px(默认)/48px(大) —— 表格紧凑优先，表单舒适优先

---

## 2. 色彩体系（Color Tokens）

所有颜色以CSS自定义属性定义，支持主题切换。命名格式：`--beds-{语义}-{层级}`。

### 2.1 主色（Primary）

| Token名 | 色值 | 用途 |
|---------|------|------|
| `--beds-primary-50` | `#EFF6FF` | 表格行hover浅蓝底、信息Tag底色 |
| `--beds-primary-100` | `#DBEAFE` | 选中行背景、主色Tag底色、浅色填充 |
| `--beds-primary-200` | `#BFDBFE` | 浅色边框、浅蓝分隔 |
| `--beds-primary-400` | `#60A5FA` | 输入框hover边框、图表辅助色 |
| `--beds-primary-500` | `#3B82F6` | 链接hover、大屏发光数字、焦点亮一级 |
| `--beds-primary-600` | `#2563EB` | **主色**：主按钮、链接、选中态、焦点环、品牌色 |
| `--beds-primary-700` | `#1D4ED8` | 主按钮hover、链接hover、侧边栏选中指示 |
| `--beds-primary-800` | `#1E40AF` | 主按钮active/pressed |
| `--beds-primary-text` | `#2563EB` | 链接文字 |

### 2.2 中性色（Neutrals）—— 浅色主题

| Token名 | 色值 | 用途 |
|---------|------|------|
| `--beds-bg-base` | `#F5F7FA` | 页面最底层背景（灰底） |
| `--beds-bg-container` | `#FFFFFF` | 卡片、面板、弹窗容器背景（白底） |
| `--beds-bg-elevated` | `#FFFFFF` | 下拉、浮层、悬浮卡片背景 |
| `--beds-bg-hover` | `#EFF6FF` | 行hover（蓝色调） |
| `--beds-bg-active` | `#DBEAFE` | 行选中/激活态 |
| `--beds-bg-disabled` | `#F5F5F5` | 禁用态背景 |
| `--beds-bg-mask` | `rgba(0,0,0,0.45)` | 遮罩层 |
| `--beds-border-1` | `#F0F0F0` | 分割线、表格内边框（最浅） |
| `--beds-border-2` | `#D9D9D9` | 输入框默认边框、卡片边框 |
| `--beds-border-3` | `#BFBFBF` | 输入框hover边框 |
| `--beds-text-primary` | `#1F2329` | 标题、正文主文字（近黑，非纯黑） |
| `--beds-text-secondary` | `#4E5969` | 正文辅助文字、描述 |
| `--beds-text-tertiary` | `#86909C` | 占位符、次要标签、禁用文字 |
| `--beds-text-disabled` | `#C9CDD4` | 禁用文字、不可操作文字 |
| `--beds-text-inverse` | `#FFFFFF` | 反色文字（深色背景上的白字） |

### 2.3 中性色（Neutrals）—— 暗色主题（大屏专用）

| Token名 | 色值 | 用途 |
|---------|------|------|
| `--beds-dark-bg-base` | `#0D1117` | 大屏最底层背景 |
| `--beds-dark-bg-container` | `#161B22` | 面板、卡片容器 |
| `--beds-dark-bg-elevated` | `#21262D` | 弹层、悬浮元素 |
| `--beds-dark-border-1` | `#21262D` | 分割线、内边框 |
| `--beds-dark-border-2` | `#30363D` | 卡片边框、输入框边框 |
| `--beds-dark-text-primary` | `#F0F6FC` | 主文字 |
| `--beds-dark-text-secondary` | `#8B949E` | 辅助文字 |
| `--beds-dark-text-tertiary` | `#6E7681` | 占位符、标签 |

### 2.4 功能色（Semantic/Status）

| 类型 | Token名 | 色值 | 浅色背景用 | 暗色背景用 |
|------|---------|------|-----------|-----------|
| **成功** | `--beds-success` | `#00B42A` | 按钮、文字、边框 | 按钮、文字、边框 |
| | `--beds-success-bg` | `#E8FFEA` | 成功Tag底色、行背景 | `rgba(0,180,42,0.15)` |
| **警告** | `--beds-warning` | `#FF7D00` | 按钮、文字、边框 | 按钮、文字、边框 |
| | `--beds-warning-bg` | `#FFF7E6` | 警告Tag底色 | `rgba(255,125,0,0.15)` |
| **错误/危险** | `--beds-danger` | `#F53F3F` | 按钮、文字、边框 | 按钮、文字、边框 |
| | `--beds-danger-bg` | `#FFECE8` | 错误Tag底色 | `rgba(245,63,63,0.15)` |
| **信息** | `--beds-info` | `#2563EB` | 提示文字 | `#3B82F6` |
| | `--beds-info-bg` | `#EFF6FF` | 信息Tag底色 | `rgba(37,99,235,0.18)` |

### 2.5 数据可视化色板（Charts）

用于图表、大屏数据展示，确保在浅色和暗色背景下均有良好区分度：

| 序号 | 色值 | 名称 | 用途 |
|------|------|------|------|
| C1 | `#2563EB` | 蓝（主色） | 核心指标、主要数据线 |
| C2 | `#14C9C9` | 青 | 第二指标、对比数据 |
| C3 | `#00B42A` | 绿 | 正向数据、增长 |
| C4 | `#F7BA1E` | 黄/金 | 中值、提醒 |
| C5 | `#F53F3F` | 红 | 负向、告警 |
| C6 | `#722ED1` | 紫 | 补充序列1 |
| C7 | `#F77234` | 橙 | 补充序列2 |
| C8 | `#60A5FA` | 浅蓝 | 补充序列3 |
| C9 | `#86909C` | 灰 | 基线、参考线、其他 |

> 大屏暗色主题下，图表颜色保持色值不变，背景使用 `--beds-dark-bg-container` 衬托。如需发光效果，可加对应色的 box-shadow `0 0 8px {color}40`。

---

## 3. 字体排版（Typography）

### 3.1 字体族

```css
--beds-font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'PingFang SC',
  'Hiragino Sans GB', 'Microsoft YaHei', 'Helvetica Neue', Helvetica, Arial, sans-serif;
--beds-font-mono: 'JetBrains Mono', 'SF Mono', Menlo, Monaco, Consolas,
  'Liberation Mono', 'Courier New', monospace;
--beds-font-number: -apple-system, BlinkMacSystemFont, 'PingFang SC', 'Helvetica Neue', Arial, sans-serif;
```

- 中文优先 PingFang SC（Mac）/ Microsoft YaHei（Windows）
- 数字使用等宽数字特性 `font-variant-numeric: tabular-nums`，确保表格中数字对齐
- 代码/金额/编号使用等宽字体

### 3.2 字号层级

| Token名 | 字号 | 行高 | 字重 | 用途 |
|---------|------|------|------|------|
| `--beds-font-size-display` | 38px | 46px (1.21) | 600 | 大屏标题、数据大屏核心数字 |
| `--beds-font-size-h1` | 28px | 36px (1.29) | 600 | 页面标题 |
| `--beds-font-size-h2` | 24px | 32px (1.33) | 600 | 模块标题、卡片标题 |
| `--beds-font-size-h3` | 20px | 28px (1.40) | 500 | 次级标题、弹窗标题 |
| `--beds-font-size-h4` | 16px | 24px (1.50) | 500 | 小标题、分组标题 |
| `--beds-font-size-body` | 14px | 22px (1.57) | 400 | **正文默认**：表格、表单、描述 |
| `--beds-font-size-body-sm` | 13px | 20px (1.54) | 400 | 紧凑场景正文 |
| `--beds-font-size-caption` | 12px | 18px (1.50) | 400 | 辅助文字、标签、时间戳 |
| `--beds-font-size-micro` | 11px | 16px (1.45) | 400 | 极小标签、徽章 |

### 3.3 排版原则

- 正文默认 **14px / 22px行高** —— B端信息密度最佳平衡点
- 数字始终开启 `font-variant-numeric: tabular-nums` 对齐
- 字重只用三个等级：**400（常规）/ 500（中等/标题）/ 600（强调/大标题）**，不使用700以上粗体
- 段落间距 12px，列表项间距 8px
- 表格中文字垂直居中，数字右对齐或居中

---

## 4. 间距系统（Spacing）

### 4.1 8px网格基准

所有间距值基于 **4px** 最小单位，常用值为8的倍数：

| Token名 | 值 | 用途 |
|---------|-----|------|
| `--beds-space-xs` | 4px | 图标与文字间距、紧凑内边距 |
| `--beds-space-sm` | 8px | 相关元素间距、标签内边距 |
| `--beds-space-md` | 12px | 表单元素间距、小组件间距 |
| `--beds-space-base` | 16px | **默认内边距**：卡片padding、表单项间距 |
| `--beds-space-lg` | 24px | 卡片间距、模块间距、区块间隔 |
| `--beds-space-xl` | 32px | 大区块间距、页面边距 |
| `--beds-space-2xl` | 48px | 页面顶部/底部留白、大模块间隔 |

### 4.2 布局间距规范

- **页面边距**：左右各 24px，顶部 24px
- **卡片内边距**：默认 24px（大屏/紧凑场景 16px）
- **卡片之间**：16px 或 24px 间距
- **表单项之间**：垂直间距 20px（表单）/ 16px（搜索筛选栏）
- **表格单元格padding**：垂直 12px，水平 16px（紧凑模式 8px / 12px）
- **导航侧栏宽度**：208px（展开）/ 48px（折叠）
- **顶部导航高度**：48px（紧凑）/ 56px（带面包屑）

---

## 5. 圆角与阴影（Border Radius & Shadows）

### 5.1 圆角体系

| Token名 | 值 | 用途 |
|---------|-----|------|
| `--beds-radius-none` | 0px | 仅特殊直角场景 |
| `--beds-radius-sm` | 2px | Tag、Badge、小徽章 |
| `--beds-radius-base` | 4px | **默认圆角**：按钮、输入框、卡片（最常用） |
| `--beds-radius-md` | 6px | 弹窗、大卡片、面板 |
| `--beds-radius-lg` | 8px | 大面板、模态框、图片容器 |
| `--beds-radius-full` | 9999px | 胶囊按钮、头像、圆形图标 |

> 原则：B端系统以4px为默认圆角，保持专业利落感。大屏卡片可用6px。不使用12px+大圆角（避免"消费感"）。

### 5.2 阴影层级

| Token名 | 值 | 用途 |
|---------|-----|------|
| `--beds-shadow-none` | none | 平面元素 |
| `--beds-shadow-sm` | `0 1px 2px 0 rgba(0,0,0,0.03), 0 1px 6px -1px rgba(0,0,0,0.02)` | 卡片默认阴影（极轻） |
| `--beds-shadow-base` | `0 2px 8px 0 rgba(0,0,0,0.08)` | **默认阴影**：卡片hover、下拉菜单 |
| `--beds-shadow-md` | `0 4px 16px 0 rgba(0,0,0,0.12)` | 弹窗、抽屉、悬浮面板 |
| `--beds-shadow-lg` | `0 6px 24px 0 rgba(0,0,0,0.16)` | 模态框、全局提示 |
| `--beds-shadow-focus` | `0 0 0 2px rgba(37,99,235,0.20)` | 输入框/按钮焦点环 |

> 暗色/大屏专用阴影为发光效果：`--beds-dark-glow: 0 0 12px rgba(37,99,235,0.3)`

---

## 6. 组件规范（Components）

### 6.1 按钮（Button）

| 类型 | 背景 | 文字 | 边框 | 圆角 | 高度 | 使用场景 |
|------|------|------|------|------|------|---------|
| **Primary（主要）** | `#2563EB` | `#FFF` | none | 4px | 32/40/48px | 页面主操作、提交、确认 |
| Hover | `#1D4ED8` | `#FFF` | none | 4px | | |
| Active | `#1E40AF` | `#FFF` | none | 4px | | |
| Disabled | `#2563EB` + opacity 0.5 | `#FFF` | | | | |
| **Default（默认）** | `#FFF` | `#1F2329` | 1px `#D9D9D9` | 4px | 32/40/48px | 次要操作、取消 |
| Hover | `#FFF` | `#2563EB` | 1px `#2563EB` | 4px | | |
| **Dashed（虚线）** | `#FFF` | `#1F2329` | 1px dashed `#D9D9D9` | 4px | 32/40/48px | 添加、更多操作 |
| **Text（文字）** | transparent | `#1F2329` | none | 4px | 32/40px | 表格操作列、弱操作 |
| Hover | `#EFF6FF` | `#2563EB` | none | 4px | | |
| **Link（链接）** | transparent | `#2563EB` | none | - | auto | 跳转、外部链接 |
| **Danger（危险）** | `#F53F3F` | `#FFF` | none | 4px | 32/40/48px | 删除、危险操作确认 |
| Hover | `#CB2634` | `#FFF` | | 4px | | |

- 按钮内边距：左右 16px（小12px），图标按钮 8px
- 按钮组间距：8px（同一行操作按钮之间）
- 加载中状态：显示Spinner + 文字变透明，禁止点击

### 6.2 输入框（Input）

| 状态 | 背景 | 边框 | 文字 | 说明 |
|------|------|------|------|------|
| 默认 | `#FFF` | 1px `#D9D9D9` | `#1F2329` | 占位符 `#86909C` |
| Hover | `#FFF` | 1px `#60A5FA` | | |
| Focus | `#FFF` | 1px `#2563EB` + `0 0 0 2px rgba(37,99,235,0.2)` | | 焦点蓝色光晕 |
| Error | `#FFF` | 1px `#F53F3F` | | 下方红色错误提示 |
| Disabled | `#F5F5F5` | 1px `#D9D9D9` | `#C9CDD4` | 不可编辑 |

- 高度：32px（表格内）/ 40px（表单默认）
- 内边距：左右 12px
- 圆角：4px
- Label标签：14px，`#1F2329`，与输入框间距 8px，居左对齐
- 必填标记：Label前加红色`*`（`#F53F3F`），右侧 4px间距
- 错误提示：输入框下方 12px caption字号，`#F53F3F`，带错误图标
- 帮助文字：输入框下方 12px caption字号，`#86909C`

### 6.3 表单（Form）

- **布局模式**：
  - 水平布局（默认）：Label 100px 宽右对齐，输入框占剩余，间距 12px
  - 垂直布局：Label在上输入框在下（适合窄栏/弹窗）
  - 行内布局：搜索筛选栏，Label+Input横向排列，间距 16px
- **表单分组**：使用 `--beds-border-1` 分割线，组间距 24px，组标题 16px/500
- **栅格**：表单区域使用24栅格，表单项默认占 12/24（半行），长字段占 24/24（整行）
- **操作栏**：主按钮在左（或右），取消按钮紧贴主按钮左侧（或右侧），间距 8px

### 6.4 表格（Table）—— 核心组件

- **容器**：白色背景 `#FFF`，1px `#F0F0F0` 外边框，4px圆角
- **表头**：
  - 背景：`#FAFAFA`（浅灰），不使用蓝色
  - 文字：14px，500字重，`#1F2329`
  - 高度：48px
  - 边框：底部 1px `#F0F0F0`
  - 排序图标：hover时显示，激活时变蓝 `#2563EB`
- **表体**：
  - 行高：48px（默认）/ 40px（紧凑模式，数据密集场景）
  - 文字：14px，400字重，`#1F2329`
  - 行边框：底部 1px `#F0F0F0`
  - 斑马纹：可选，偶数行 `#FAFBFC` 背景
  - **Hover行**：背景 `#EFF6FF`（浅蓝），过渡动画 0.2s
  - **选中行**：背景 `#DBEAFE`，左侧可加 3px 蓝色指示条
- **单元格**：
  - 内边距：垂直 12px（紧凑8px），水平 16px（紧凑12px）
  - 文字对齐：文字左对齐、数字右对齐、操作列右对齐居中图标、状态居中
  - 超长文本：省略号+tooltip，不换行（`max-width: 200px` 开始截断）
- **操作列**：
  - 文字按钮间距：16px（分割线`|`间距8px）
  - 危险操作用红色 `#F53F3F`
- **分页器**：
  - 靠右对齐，与表格间距 16px
  - 页码按钮高 32px，当前页蓝底白字
  - 每页条数选择器在左侧
- **空数据**：居中占位图标 + "暂无数据"文案 + 可选操作按钮，最小高度 200px
- **加载态**：表格区域覆盖 Skeleton 或 Spinner 遮罩

### 6.5 选择器/下拉（Select / Dropdown）

- 触发区域同输入框样式（40px高，4px圆角）
- 下拉面板：白色背景，`--beds-shadow-md` 阴影，4px圆角，1px `#F0F0F0`边框
- 选项高度：36px，内边距 12px，hover背景 `#EFF6FF`
- 选中项：`#DBEAFE` 背景 + 蓝色文字，右侧✓图标
- 分组选项：组标题 12px `#86909C`，不可点击

### 6.6 日期选择器/时间选择器（DatePicker）

- 触发区域同输入框样式
- 弹出面板：宽度 280px+，白色背景，阴影同下拉
- 选中日期：蓝底白字，今天用蓝色边框标识
- 日期单元格：28px×28px，hover浅蓝底

### 6.7 标签/徽章（Tag & Badge）

| 类型 | 背景 | 文字 | 边框 | 圆角 | 尺寸 |
|------|------|------|------|------|------|
| 默认Tag | `#F2F3F5` | `#4E5969` | none | 2px | 高度22px，padding 0 8px |
| 蓝色Tag | `#DBEAFE` | `#2563EB` | none | 2px | 同上 |
| 绿色Tag | `#E8FFEA` | `#00B42A` | none | 2px | 同上 |
| 橙色Tag | `#FFF7E6` | `#FF7D00` | none | 2px | 同上 |
| 红色Tag | `#FFECE8` | `#F53F3F` | none | 2px | 同上 |
| 紫色Tag | `#F5E8FF` | `#722ED1` | none | 2px | 同上 |
| 描边Tag | `#FFF` | 当前状态色 | 1px 当前状态色 | 2px | 同上 |
| Badge（红点）| - | - | - | 圆点 | 8px直径，右上偏移，可含数字 |

- Tag字号：12px，字重400
- 可关闭Tag：hover显示×图标，点击移除

### 6.8 导航系统（Navigation）

#### 侧边栏导航（Sidebar）
- 宽度：208px（展开）/ 48px（折叠图标模式）
- 背景：`#001529`（深色导航，经典B端）或 `#FFFFFF`（浅色导航）
- 文字：浅色导航文字 `rgba(255,255,255,0.65)`，选中 `#FFF`
- 菜单项高度：40px，内边距 16px（展开），图标+文字间距 12px
- 选中态：左侧3px蓝色指示条 `#2563EB` + 背景 `rgba(37,99,235,0.18)`
- Hover态：背景 `rgba(255,255,255,0.08)`
- 子菜单：缩进 24px，背景略深一级
- 折叠提示条：底部"收起/展开"按钮，48px高

#### 顶部导航（Topbar / Header）
- 高度：48px（纯导航）/ 56px（包含面包屑+搜索）
- 背景：`#FFF`，底部 1px `#F0F0F0` 分割线
- Logo区：左侧，宽度同侧边栏，品牌名 16px/600
- 面包屑：中部偏左，14px，当前页加粗
- 右侧功能区：搜索框、通知铃铛、用户头像+名下拉，间距 16px

#### 标签页导航（Tabs）
- 高度：40px，底部 1px `#F0F0F0`
- Tab文字：14px，默认 `#4E5969`，选中 `#2563EB`
- 选中指示：底部 2px 蓝色线，宽度跟随文字宽度
- Hover：文字变蓝 `#2563EB`
- Card模式：白底+边框+4px圆角，选中白底蓝边蓝字

### 6.9 弹窗/抽屉（Modal / Drawer）

#### Modal弹窗
- 宽度：默认 520px，大弹窗 720px，全屏 90%视口
- 圆角：8px
- 遮罩：`rgba(0,0,0,0.45)`
- 阴影：`--beds-shadow-lg`
- 标题栏：16px/500字重，底部 1px `#F0F0F0`，padding 20px 24px
- 内容区：padding 24px，最小高度 100px
- 底部操作栏：右对齐按钮，主按钮最右，padding 16px 24px，顶部 1px分割线
- 关闭按钮：右上角 32px×32px 图标按钮，hover灰色圆底
- 最大高度：视口高度的80%，超出内容区滚动

#### Drawer抽屉
- 宽度：右侧滑出，默认 480px（表单）/ 720px（详情）
- 其余规范同Modal

### 6.10 消息提示（Message / Notification）

#### Message 全局提示（顶部居中）
- 高度：40px，内边距 16px
- 圆角：4px
- 背景：`#FFF` + `--beds-shadow-md`，左侧 3px 对应功能色边线
- 停留时间：3秒（成功/信息），手动关闭（错误/警告）
- 位置：顶部居中，距顶 20px

#### Notification 通知框（右上角）
- 宽度：384px
- 圆角：8px
- 标题 16px/500 + 内容 14px/`#4E5969`
- 关闭按钮在右上角

### 6.11 数据卡片/统计卡片（Stat Card）—— 大屏核心

- **基础统计卡（浅色管理后台）**：
  - 白色背景，`--beds-shadow-sm`，4px圆角
  - padding 20px
  - 标题：14px `#4E5969`，上方
  - 数值：28px/600 `#1F2329`，使用tabular-nums
  - 环比/同比：12px，绿涨红跌（或根据业务），带上下箭头图标
  - 辅助说明/趋势图：下方

- **数据大屏面板（暗色）**：
  - 背景：`linear-gradient(135deg, rgba(37,99,235,0.08) 0%, rgba(37,99,235,0.02) 100%)` 或 `#161B22`
  - 边框：1px solid `rgba(37,99,235,0.25)` 或 `#30363D`
  - 顶部标题栏：高度 40px，padding 16px，标题 16px/500 浅色文字，左侧蓝色竖线装饰（4px宽）
  - 内容区 padding：16px 20px
  - 核心数字：32–48px/600，数据可视化色板颜色（推荐用`#3B82F6`），可加text-shadow发光 `0 0 12px rgba(59,130,246,0.5)`
  - 装饰元素：角落科技感三角/线条装饰（可选，克制使用）

### 6.12 图表容器（Chart Container）

- 统一使用卡片容器包裹
- 卡片头部：标题（14px/500）+ 右侧图例/操作（切换、下载），高度 40px，底部 1px分割线
- 图表区域padding：16px 0
- 图表配色使用本规范"数据可视化色板"（C1–C9）
- 坐标轴文字：12px `#86909C`
- 网格线：`#F0F0F0`（浅色）/ `#21262D`（暗色）
- tooltip：深色背景 `rgba(0,0,0,0.75)`，白色文字，圆角4px，padding 8px 12px

### 6.13 大屏布局规范（Dashboard / Big Screen）

- **基础画布**：
  - 背景色：`#0D1117`（深空黑蓝），可选细微渐变/网格装饰
  - 最小设计分辨率：1920×1080（FHD），适配时按比例缩放
  - 安全边距：四周各 24px，面板之间 16px 间距
- **顶部标题区**：
  - 高度：64–80px
  - 标题居中：32–38px/600，浅色文字，可加蓝色渐变发光
  - 两侧可放时间、天气、系统状态等辅助信息（14px，`#8B949E`）
  - 底部可加分隔装饰线（蓝色渐变线）
- **面板栅格布局**：
  - 使用CSS Grid，推荐12列栅格
  - 常用布局比例：左3-中6-右3（核心居中）/ 左4-中4-右4（三等分）/ 上2-中8-下2
  - 所有面板统一高度节奏：小面板 220px、中面板 320px、大面板 440px
- **动效规范**：
  - 数据加载可使用数字滚动动画（countUp）
  - 边框扫光/呼吸光效果可用于核心指标（一个大屏最多2-3处，避免过炫）
  - 图表入场动画不超过0.6秒
  - 禁止闪烁、旋转等干扰阅读的动画

---

## 7. 布局原则（Layout）

### 7.1 经典B端布局结构

```
┌─────────────────────────────────────────────┐
│  Topbar (48/56px): Logo | 面包屑 | 用户区    │
├──────┬──────────────────────────────────────┤
│      │  Page Header (标题+操作区 56px)       │
│ Side │  ┌──────────────────────────────┐    │
│ bar  │  │  筛选栏 / Tab 导航            │    │
│ 208px│  ├──────────────────────────────┤    │
│      │  │  内容区（卡片/表格/图表）      │    │
│      │  │                              │    │
│      │  └──────────────────────────────┘    │
│      │  分页                                │
└──────┴──────────────────────────────────────┘
```

### 7.2 页面结构层级

1. **Page Header（页头）**：页面标题 + 描述（可选）+ 右侧主操作按钮区域，高度自适应（约56px），底部margin 16px
2. **Filter Bar（筛选栏）**：搜索条件区域，背景 `#FAFAFA` 或白底，padding 16px，4px圆角，底部margin 16px；收起时高度36px，展开自适应
3. **Content Area（内容区）**：卡片/表格/图表，卡片间margin 16px
4. **Pagination（分页）**：底部右对齐

### 7.3 栅格系统

- 基于24栅格，gutter 16px
- 内容区域最大宽度：不设上限（B端后台通常撑满）
- 卡片内容排列：统计卡片常用 4列/3列（一行4个/3个）

---

## 8. 图标（Icons）

- **图标库推荐**：Ant Design Icons 或 IconPark（字节跳动），免费开源、覆盖B端全场景
- **默认尺寸**：14px（表格/按钮内）/ 16px（导航/工具栏）/ 20px（空状态/装饰）
- **图标颜色**：跟随文字颜色，默认 `#4E5969`，hover跟随主色
- **图标与文字间距**：4px或6px
- **按钮内图标**：若仅图标无文字，保持32px/40px方形容器

---

## 9. 交互状态与动效

### 9.1 状态定义统一

| 状态 | 视觉表现 |
|------|---------|
| Default | 组件默认外观 |
| Hover | 主色文字/浅蓝底/边框变色，过渡 0.2s ease |
| Active/Pressed | 颜色加深一级（如`#1E40AF`），可轻微缩放0.98 |
| Focus | 蓝色外光晕 `--beds-shadow-focus`，键盘导航必现 |
| Selected | 蓝底+蓝字，明确指示 |
| Disabled | opacity 0.5 或灰色背景，cursor: not-allowed，禁止交互 |
| Loading | Spinner/Skeleton，禁止重复提交 |

### 9.2 动效原则

- **时长**：微交互 0.2s（hover、focus），过渡 0.3s（展开、切换），入场 0.4s
- **缓动**：统一使用 `cubic-bezier(0.34, 0.69, 0.1, 1)` 或 `ease`
- **禁用场景**：数据加载超过300ms时才显示loading，避免闪烁；页面首次加载不做强入场动画（节省时间）

---

## 10. Do's and Don'ts

### ✅ Do

- 使用统一的Design Token（颜色、字号、间距、圆角、阴影），不要硬编码值
- 表格使用斑马纹或hover行高亮增强可读性
- 数字一律右对齐并使用等宽数字特性（tabular-nums）
- 表单必填项在Label前加红色`*`标记
- 弹窗宽度按内容选择（表单520px/详情720px）
- 大屏使用暗色主题 + 数据可视化色板，对比度要够（文字与背景对比度≥4.5:1）
- 所有交互元素（按钮/链接/可点击行）要有明确hover态
- 空状态、加载态、错误态都要有设计，不能留白
- 操作按钮按主次排列：主要按钮在最右或最醒目位置，危险操作二次确认

### ❌ Don't

- 不要在B端后台使用大圆角（>8px）、鲜艳渐变色、卡通装饰
- 不要混用多种颜色体系，主色统一为蓝色系 `#2563EB`
- 不要在一个页面使用超过3种字重（400/500/600）
- 不要让表格行高低于40px（会导致点击困难、阅读拥挤）
- 不要使用斜体、艺术字体、下划线（仅链接除外）
- 不要在同一行放超过3个主按钮
- 不要在大屏上使用过多动画和光效（数据可读性优先）
- 不要忽略暗色主题下的文字对比度
- 不要随意设定间距值，必须在 4/8/12/16/24/32 中选择

---

## 11. 响应式断点

| 断点名称 | 宽度 | 适配说明 |
|---------|------|---------|
| xs | <576px | 手机端（B端极少用到，仅部分审批移动页面） |
| sm | 576–768px | 平板竖屏，侧边栏折叠为图标 |
| md | 768–992px | 小笔记本，侧边栏可折叠 |
| lg | 992–1200px | 标准笔记本，默认布局 |
| xl | 1200–1600px | 桌面显示器，完整布局 |
| xxl | >1600px | 大屏，内容区可设置max-width: 1600px居中 |

- B端系统以 **1440×900** 和 **1920×1080** 为核心设计分辨率
- 侧边栏在 <1200px 时默认为折叠态或可收起
- 数据大屏固定16:9比例（1920×1080基准），使用transform scale自适应

---

## 12. Developer Quick Reference

### CSS变量快速引入

将以下变量放入全局 `:root`，暗色主题在 `[data-theme="dark"]` 或 `.dark-theme` 类下覆盖即可：

```css
:root {
  --beds-primary: #2563EB;
  --beds-primary-hover: #1D4ED8;
  --beds-primary-active: #1E40AF;
  --beds-primary-bg: #DBEAFE;
  --beds-primary-bg-hover: #EFF6FF;
  --beds-primary-border: #BFDBFE;
  --beds-primary-focus-ring: #60A5FA;
  --beds-success: #00B42A;
  --beds-warning: #FF7D00;
  --beds-danger: #F53F3F;
  --beds-bg-base: #F5F7FA;
  --beds-bg-container: #FFFFFF;
  --beds-text-primary: #1F2329;
  --beds-text-secondary: #4E5969;
  --beds-text-tertiary: #86909C;
  --beds-border-1: #F0F0F0;
  --beds-border-2: #D9D9D9;
  --beds-radius-base: 4px;
  --beds-shadow-base: 0 2px 8px 0 rgba(0,0,0,0.08);
  --beds-font-size-body: 14px;
  --beds-space-base: 16px;
}
```

### 常用组合片段

**标准卡片：**
```css
.card { background:#FFF; border-radius:4px; padding:24px; box-shadow:0 1px 2px rgba(0,0,0,0.03); }
```

**主按钮：**
```css
.btn-primary { background:#2563EB; color:#FFF; border:none; border-radius:4px; height:40px; padding:0 16px; font-size:14px; cursor:pointer; transition:background .2s; }
.btn-primary:hover { background:#1D4ED8; }
.btn-primary:active { background:#1E40AF; }
```

**输入框：**
```css
.input { height:40px; padding:0 12px; border:1px solid #D9D9D9; border-radius:4px; font-size:14px; outline:none; transition:all .2s; }
.input:focus { border-color:#2563EB; box-shadow:0 0 0 2px rgba(37,99,235,.2); }
```

**表格行：**
```css
.tr:hover { background:#EFF6FF; }
.tr.selected { background:#DBEAFE; }
```

### Trae IDE 开发建议

1. 把本规范的 DESIGN.md 放到项目根目录，AI生成代码时直接读取
2. 建立全局 `styles/tokens.css` 文件存放所有CSS变量
3. 封装基础组件（Button/Input/Table/Card/Modal）后在各页面复用
4. 表格组件优先使用成熟组件库（Ant Design Vue/React 或 Element Plus），主题色通过ConfigProvider覆盖为本规范色值即可
5. 大屏图表推荐 ECharts，主题使用自定义深色主题匹配本规范

---

## 附录A：大屏设计专项 Checklist

- [ ] 分辨率基准 1920×1080，使用 transform:scale 自适应
- [ ] 背景色 #0D1117，面板边框 rgba(37,99,235,0.25)
- [ ] 标题文字 #F0F6FC，数字可加轻微发光
- [ ] 配色严格使用数据可视化色板C1-C9
- [ ] 面板间距16px，四周安全边距24px
- [ ] 每个面板必须有标题（16px，左侧蓝色装饰竖线）
- [ ] 数字字体 tabular-nums，字号≥20px保证可读
- [ ] 动效克制：不超过3处发光/扫光效果
- [ ] 图表网格线使用半透明深色 #21262D
- [ ] 实时数据刷新不加动画（除非业务需要）

## 附录B：表单页设计 Checklist

- [ ] 必填项Label前有红色 `*`
- [ ] Label宽度统一（100px右对齐）
- [ ] 输入框高度统一40px
- [ ] 错误状态红色边框+错误文字
- [ ] 提交按钮为主按钮，放在最醒目的位置
- [ ] 表单分区块时使用分割线或小标题分组
- [ ] 提交前前端校验，错误定位到第一个出错字段

## 附录C：表格页设计 Checklist

- [ ] 表头背景 #FAFAFA，与表体视觉区分
- [ ] 行高≥40px（默认48px）
- [ ] 操作列文字按钮间距≥16px
- [ ] 长文本省略号+tooltip
- [ ] 数字右对齐、文字左对齐
- [ ] hover行有浅蓝背景（#EFF6FF）
- [ ] 分页器在表格底部右对齐
- [ ] 空状态有占位图和提示
