# 市面 UI/UX 设计类 Skill 全景盘点

> 盘点时间：2026 年 10 月 ｜ 面向 B 端设计师 / 一人全栈团队选型
> 先搞懂是什么，再看有哪些，最后说该装哪几个

---

## 一、先厘清概念：这里的 "skill" 指什么

**Agent Skill（智能体技能）** 是目前 AI 编程工具通用的一种能力封装格式，由 Anthropic 发起并成为开放标准，Claude Code、Cursor、Codex、Gemini CLI、Trae 等都已支持。

- **本质**：一个文件夹 + 一份 `SKILL.md`（YAML 头部 + Markdown 正文），可附带脚本、模板、参考文档
- **和 Prompt 的区别**：Prompt 是"临时交代"，Skill 是"岗位说明书"——写一次，长期复用，可进 Git、可 review
- **和 Rules 的区别**：Rules 全量加载、常驻占用上下文；Skill 按需加载，先看简介、命中才读全文
- **和 MCP 的区别**：MCP 提供"能调用的工具"，Skill 定义"该怎么干活的流程"

一句话：**Skill 把设计规范和设计判断，变成 AI 每次都会遵守的显性工作流。**

---

## 二、全景清单

### A 类 · 官方 / 大厂系（最稳，优先装）

| 技能 | 来源 | 核心能力 | 适配 B 端 | 安装 |
|------|------|----------|:--------:|------|
| `frontend-design` | Anthropic 官方（anthropics/skills） | 先定视觉方向再写代码，明确禁止通用 AI 套路（紫色渐变、Inter 字体等） | ★★★★ | `/plugin install example-skills@anthropic-agent-skills` |
| `web-design-guidelines` | Vercel Labs | 按 Web 界面规范审计代码：可访问性、响应式、焦点态、表单、暗色模式 | ★★★★★ | `npx skills add vercel-labs/agent-skills --skill web-design-guidelines` |
| `vercel-react-best-practices` | Vercel Labs | 自动应用 React/Next.js 性能规则 | ★★★ | 同上仓库 |
| `canvas-design` | Anthropic 官方 | 生成 PNG/PDF 视觉作品（海报、宣传图） | ★★ | 随 example-skills 安装 |
| `brand-guidelines` | Anthropic 官方 | 套用品牌风格（配色、字体、语气） | ★★ | 同上 |
| `theme-factory` | Anthropic 官方 | 10 套预设配色字体方案，一键换肤 | ★★ | 同上 |
| `algorithmic-art` | Anthropic 官方 | p5.js 算法艺术、粒子效果 | ★ | 同上 |
| `skill-creator` | Anthropic 官方 | **元技能**：帮你创建/优化自定义技能 | ★★★★★ | 同上 |

> 官方系总计 18 个技能，打包为 `document-skills`（docx/pdf/pptx/xlsx）与 `example-skills` 两个插件发布，装 2 个插件即可全拿到。官方维护、随工具版本同步适配，是**最不容易出问题**的一类。

### B 类 · 社区爆款系（设计能力最强，反 AI 味）

| 技能 | 来源 | 核心能力 | 适配 B 端 | 安装 |
|------|------|----------|:--------:|------|
| `ui-ux-pro-max` | nextlevelbuilder | 设计数据库驱动：79 种风格 / 192 套配色 / 74 组字体搭配 / 192 类产品形态 / 119 条 UX 准则 / 25 种图表 / 22 个技术栈，可生成**项目级设计系统**（MASTER.md + 页面级覆盖） | ★★★★ | `npx skills add nextlevelbuilder/ui-ux-pro-max-skill` |
| `design-taste-frontend` | Leonxlnx/taste-skill | 用三个"旋钮"（设计方差 / 动效强度 / 视觉密度）驱动产出，带强制交付前检查清单 | ★★★ | `npx skills add https://github.com/leonxlnx/taste-skill --skill design-taste-frontend` |
| `high-end-visual-design` | 同仓库 | 高端视觉方向（品牌感更强） | ★★ | 同上换 skill 名 |
| `Impeccable` | pbakaus | 23 条命令（shape / craft / polish / audit）+ 27–60 条确定性反模式检测规则，7 份领域参考（排版/色彩对比/空间/动效/交互/响应式/UX 文案） | ★★★★ | `npx impeccable install` |
| `dembrandt-skills` | dembrandt | 资深设计师经验封装：品牌视觉语言、明暗主题、算法配色、设计令牌与尺度 | ★★★★★ | `npx skills add dembrandt/dembrandt-skills` |
| `ui-ux-design` | hicay/claude-code-skills | Dieter Rams 十原则 + 8pt 网格 + 三级字号 + 组件库 + 60 项审查清单 | ★★★★ | 见仓库 README |
| `bencium-controlled-ux-designer` | bencium | 强调"做设计决策前先问"，不擅自动手，产出更克制 | ★★★ | `npx skills add https://github.com/bencium/bencium-marketplace --skill bencium-controlled-ux-designer` |
| `logo-design-skill` | 社区 | Logo / 字标设计，内置 1400+ 真实 SVG 参考库 | ★ | 见 gitcode 镜像 |

> 这三个是社区里设计能力最强的一档：`ui-ux-pro-max`（广度最大）、`design-taste-frontend`（审美最独特）、`Impeccable`（审查最严谨）。

### C 类 · 设计系统 / 规范方法论系

| 技能 | 来源 | 核心能力 |
|------|------|----------|
| `design-tokens` | julianoczkowski/designer-skills | 按选定美学生成设计令牌文件（CSS 变量 / Tailwind config），含明暗主题、间距尺度、字号阶梯 |
| `ui-design-system` | dicklesworthstone、alirezarezvani 等 | 生成完整设计系统文档：原则、色板、排版、组件规格、开发交付文档；附令牌生成脚本 |
| `DESIGN.md` / `awesome-design-md` | VoltAgent | 收录 60+ 大厂设计语言（Apple / Stripe / Linear / Vercel / Figma…）的 Markdown 规范，丢进项目根目录即被 AI 读取 |
| `stitch-skills` | google-labs-code | 与 Google Stitch 配套，`design-md` 技能可从已有项目反向提炼设计系统 |
| `hooked-ux` | wondelai/skills | Hook 模型（触发-行动-奖励-投入）设计习惯养成闭环 |

> **DESIGN.md 值得单独提**：它不是插件、不是 SaaS，就是一份写给 AI 看的设计说明书。目前社区已有 60+ 大厂规范可直接取用。对一人团队来说，这是**成本最低、收益最直接**的一招——本项目包本质上也是在做同样的事，只不过更贴合你自己的 B 端场景。

### D 类 · B 端 / 后台专用系

| 技能 | 来源 | 核心能力 |
|------|------|----------|
| `kaicalls-design` | 社区 | 专为 B2B SaaS 后台：dark-first 设计系统、shadcn/ui、表格/表单/卡片/徽章、B2B 最佳实践 |
| `ux-design-systems` | hoodini/ai-agents-skills | 为 agent UI、仪表盘、对话界面提供令牌与组件对齐、无障碍交互模式 |
| `premium-frontend-ui` | github/awesome-copilot | 高质感 Web 体验：动效、排版、架构 |
| `emil-design-eng` | 社区 | 设计工程导向的前端产出（约 34 万安装） |

> 这类最贴合你的场景，但大多绑定特定技术栈或体系。**参考它们的组织方式，落地时仍建议用自己的规范**（即本包的 `beds-design-system`）。

### E 类 · 大屏 / 数据可视化系

| 技能 | 来源 | 核心能力 |
|------|------|----------|
| `jimubi-bigscreen` | JEECG 积木 BI | 一句话生成**整屏大屏**，自动配齐 KPI、趋势、排行、地图、边框装饰；内置 10+ 行业模板 |
| `jimubi-dashboard` | 同上 | 24 列栅格仪表盘，卡片式、亮色主题，适合日常数据看板 |
| Claude `Dashboards` / `Motion` | Anthropic 产品功能 | 接入数据源后生成自动更新的看板；把结论做成分镜动画（付费套餐，非 skill） |

> `jimubi-*` 是**中文生态里少见的成熟大屏 skill**，但依赖积木 BI 平台。若你自建大屏（ECharts + 自研），用本包的 `data-screen-dark` 更合适。

### F 类 · 生态工具与聚合站

| 名称 | 作用 |
|------|------|
| `skills.sh`（Vercel） | 技能聚合站，按 24 小时安装量排名，找技能首选入口 |
| `agentskill.sh` / `claudeskills.info` / `skillselion.com` | 技能目录与榜单站，可按类别（含 design / UX）浏览 |
| `SkillHub`（桌面应用） | 跨工具管理技能：浏览、安装、同步、版本对比 |
| `TRAE-Skills`（AlperGuven） | 专门为 Trae 写的技能集（Vue3 / Vite / Pinia 方向） |
| `skills-tree` | 全量技能索引（约 360 个，按 17 类组织） |
| `skill-security-scan` / `skill-security-analyzer` | 安装第三方技能前的安全扫描工具 |

> ⚠️ **安全提醒**：第三方 skill 可以带脚本，务必先看内容。已有案例：`design-mobile-apps` 安装量高达 56 万，但其 skills.sh 页面的安全审计**未通过**——**安装量 ≠ 可信度**。装之前，优先选官方仓库或高星、近期有维护的项目。

---

## 三、选型建议：不要全装

社区实测的一致结论是：**装 50 个，每天真正用到的不到 5 个**；同类设计技能装多了只会互相抢上下文、烧 token。

### 给你的推荐组合（B 端 + 一人团队 + Trae）

**第一步 · 装本包的 5 个技能**（已针对你的场景定制，覆盖全链路）

**第二步 · 从市面技能里补 2 个**

| 补哪个 | 为什么 | 安装 |
|--------|--------|------|
| `frontend-design`（Anthropic 官方） | 兜底的"反 AI 味"设计哲学，最稳、几乎不出错 | `/plugin install example-skills@anthropic-agent-skills` |
| `web-design-guidelines`（Vercel 官方） | 上线前用规范审一遍代码，覆盖无障碍与响应式 | `npx skills add vercel-labs/agent-skills --skill web-design-guidelines` |

**想再进一步（三选一，别都装）**

- 要**设计系统生成**：`ui-ux-pro-max`
- 要**精细化审查**：`Impeccable`
- 要**逆向提炼设计系统**：`dembrandt-skills`

### 不建议装的

- 只做移动端 / 消费级审美的（与 B 端基调不符）
- 依赖特定平台且你不在用的（如未用积木 BI 就别装 `jimubi-*`）
- 长期未更新、无源码可查的小众技能

---

## 四、装好之后怎么用（关键）

1. **把规范放项目根目录**：`DESIGN.md` 丢进根目录，让 AI 每次都能读到
2. **用 Skill 管流程**：建页面、做表格、搭大屏、走查，各交给对应技能
3. **一句话锁定规范**：对话时补"严格遵循 DESIGN.md，不得使用规范以外的颜色和字体"
4. **定期清理**：每季度看一次哪些技能真正在用，不用的删掉

真正决定效果的，不是装了多少个技能，而是**有没有一套属于自己的、可执行的规范**。市面技能解决的是"通用审美下限"，你的项目规范解决的才是"团队一致性上限"。

---

## 五、来源参考（截至 2026-10）

- Anthropic 官方技能仓库 `anthropics/skills`
- Vercel `vercel-labs/agent-skills`、聚合站 `skills.sh`
- `nextlevelbuilder/ui-ux-pro-max-skill`、`leonxlnx/taste-skill`、`pbakaus/impeccable`、`dembrandt/dembrandt-skills`
- `VoltAgent/awesome-design-md`（60+ 大厂设计规范）
- Trae 官方文档「技能（Skill）」`docs.trae.cn/ide_skills`
- 第三方榜单：skillselion.com、claudeskills.info、agentskill.sh

> 数据会随时间变化，安装量 / 星标为盘点时的快照，仅用于横向比较，不代表实际效果。
