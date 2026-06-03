# Agnes Dashboard

**Agnes-2.0-flash Token 用量仪表盘**

基于原始 CSV 日志数据，实时生成分时、分 Key、分日期的 Token 消耗统计。纯前端实现，零依赖。

## 功能

- 📊 **每日用量** — 按日分组的 Input / Output Token 堆叠柱状图
- 🗝️ **Key 分时段用量** — 按 Key 维度的 24 小时热力柱状图
- 📈 **Token 总用量表** — 每个 Key 的 Input / Output / 总量 / 调用次数
- 🔄 **实时刷新** — 每次页面加载自动从 `rawdata.csv` 读取最新数据

## 快速开始

### 1. 准备数据

将你从agnes后台（https://platform.agnes-ai.com/billing/billing）导出的 CSV 日志文件重命名为 `rawdata.csv` 并放在项目根目录：

```
agnes-dashboard/
├── index.html
├── rawdata.csv          # ← 数据文件，会被 .gitignore 忽略
└── .gitignore
```

CSV 格式要求（与 Agnes API 导出格式一致）：

```csv
Type,Secret Key Name,Consumption Model,Consumption Amount(cents),Consumption Quantity,Consumption Time,Consumption Status
api_call,aniu,agnes-2.0-flash,0.0,input:20311/output:559,2026-06-03T03:13:37,success
```

### 2. 启动服务

**方式一：Python**
```bash
python3 -m http.server 8765
```

**方式二：Node.js**
```bash
npx serve .
```

**方式三：PHP**
```bash
php -S localhost:8765
```

浏览器打开 `http://localhost:8765` 即可看到仪表盘。

## 每天更新数据

1. 将新的 CSV 文件覆盖为 `rawdata.csv`（文件名统一为 `rawdata.csv`）
2. 刷新浏览器页面，数据自动更新

> CSV 文件已被 `.gitignore` 忽略，不会提交到 Git，确保不泄露敏感数据。

## 技术栈

| 项目 | 说明 |
|------|------|
| 前端 | 纯 HTML + CSS + JavaScript |
| 图表 | 原生 CSS Flexbox 柱状图 |
| 数据 | 前端直接解析 CSV |
| 字体 | Syne（标题）+ DM Mono（正文） |

## 开源协议

MIT

Developed by Agnes 2.0 Flash
