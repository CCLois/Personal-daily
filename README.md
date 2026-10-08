# CClois 的个人工作台

> 一个模型无关的每日看板：穿搭 · 天气 · 复盘 · 便签
> 任何 AI 模型都可以接管和维护这个仓库。

## 页面地址

`https://cclois.github.io/Personal-daily/`
（GitHub Pages 自动部署，push 到 main 分支后约 1-2 分钟生效）

## 仓库结构

```
├── index.html              ← 看板页面（移动端优先，响应式）
├── data/
│   ├── today.json          ← 每日核心数据（穿搭/天气/干支/复盘）
│   └── notes.json          ← 跨设备便签数据
└── prompts/
    ├── outfit-rules.md     ← 穿搭生成规则（模型无关）
    └── review-rules.md     ← 复盘生成规则（模型无关）
```

## 数据更新协议

### 每日更新（由 AI 执行）

1. **05:00-07:00 早间更新**：读取 `prompts/outfit-rules.md`，生成当日穿搭数据，写入 `data/today.json` 的 `outfit` 字段
2. **21:00 晚间复盘**：读取 `prompts/review-rules.md`，生成复盘数据，写入 `data/today.json` 的 `review` 字段
3. **便签更新**：用户请求时更新 `data/notes.json`

### 更新步骤

```bash
# 1. 拉取最新
git pull origin main

# 2. 修改数据文件（today.json / notes.json）

# 3. 提交并推送
git add -A
git commit -m "update: <日期> 数据更新"
git push origin main
```

### 数据格式

所有数据格式和字段说明见 `prompts/outfit-rules.md` 和 `prompts/review-rules.md` 中的 JSON 示例。

**关键约束：**
- `today.json` 的 `meta.last_updated` 字段必须更新为当前时间
- 同日不可重复生成穿搭（避免覆盖已推送内容）
- 新增组件时：先扩展 JSON 结构，再更新 `index.html` 的渲染逻辑

## 用户偏好备忘

- 喜用神：火、木
- 城市：武汉
- 穿搭习惯：黑白基础 + 一件出彩单品 / 全身同色系
- 页面使用场景：手机 + 电脑浏览器

## 历史

- 2026-10-08：初始化仓库，由 OpenClaw（CClois 的个人 AI 助手）创建
