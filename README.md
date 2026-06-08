# Real Madrid Stats - Product Package

## 产品概述

面向全球皇马球迷的深度数据中枢App，差异化定位为「硬核球迷的数据大脑」。

---

## 项目结构

```
rm-data-hub/
├── pwa/                          # 立即可用的PWA版本
│   ├── index.html               # 主应用（完整功能）
│   ├── manifest.json            # PWA配置
│   ├── sw.js                    # Service Worker
│   └── README.md                # 本文件
│
├── react-native/                 # App Store上架版本（React Native）
│   ├── App.js                   # 入口文件
│   ├── package.json             # 依赖配置
│   └── src/
│       ├── screens/             # 5个Tab页面
│       │   ├── MatchCenterScreen.js
│       │   ├── SquadScreen.js
│       │   ├── PlayerDetailScreen.js
│       │   ├── TacticsScreen.js
│       │   ├── DataScreen.js
│       │   └── CommunityScreen.js
│       └── services/
│           └── api.js           # API客户端 + 缓存层
│
└── backend/                      # Python后端API
    ├── app.py                   # Flask REST API
    ├── scraper.py               # 皇马官网数据爬虫
    └── requirements.txt         # Python依赖
```

---

## PWA版本 - 立即使用

### 使用方法

1. 在浏览器中打开 `index.html`
2. 点击顶部弹出的 "Add to Home Screen" 提示（或浏览器菜单 → 添加到主屏幕）
3. 像原生App一样从主屏幕打开使用

### PWA特性
- 离线缓存（Service Worker）
- 添加到主屏幕
- 深色模式
- localStorage数据持久化（预测记录、投票、收藏）

---

## React Native版本 - App Store上架

### 快速开始

```bash
cd react-native
npm install
npx expo start
```

### iOS上架
```bash
npx expo run:ios
# 或构建release版本
npx expo prebuild --platform ios
cd ios && fastlane beta
```

### Android上架
```bash
npx expo run:android
```

---

## 后端API

### 本地运行

```bash
cd backend
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
python app.py
```

### API端点

| 端点 | 方法 | 说明 |
|------|------|------|
| `/api/health` | GET | 健康检查 |
| `/api/players` | GET | 全部球员 |
| `/api/players/<id>` | GET | 单个球员 |
| `/api/matches` | GET | 比赛列表 |
| `/api/news` | GET | 新闻资讯 |
| `/api/rankings?type=goals` | GET | 排行榜 |
| `/api/topics` | GET | 社区话题 |
| `/api/predictions` | POST | 提交预测 |
| `/api/votes` | POST | 提交投票 |

---

## 数据源

- **主数据源**: https://www.realmadrid.com/es-ES
- **补充数据**: SofaScore API（实时比分）、Transfermarkt（估值）
- **数据更新频率**: 球员信息每2小时、比赛结果实时、新闻每小时

---

## 版权合规

- App为非官方球迷应用，不隶属皇马俱乐部
- 不使用官方队徽作为App图标
- 数据来源为官网公开信息（事实数据，不受版权保护）
- App描述中明确标注 "This is an unofficial fan app"

---

## 技术栈

| 层级 | 技术 |
|------|------|
| PWA前端 | React 18 + Tailwind CSS |
| App Store版 | React Native + Expo |
| 后端 | Python + Flask |
| 数据抓取 | BeautifulSoup + Requests |
| 缓存 | localStorage / AsyncStorage / Redis |
