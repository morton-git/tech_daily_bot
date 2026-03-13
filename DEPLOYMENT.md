# 🌐 雲端部署指南

## 部署選擇比較

| 方案 | 成本 | 複雜度 | 可靠性 | 推薦度 |
|------|------|--------|--------|--------|
| VPS 部署 | 中低 | 中 | 高 | ⭐⭐⭐⭐⭐ |
| Docker 容器 | 中 | 中高 | 高 | ⭐⭐⭐⭐ |
| 雲端函數 | 低 | 低 | 中 | ⭐⭐⭐ |
| 純 Web API | 低 | 低 | 高 | ⭐⭐⭐⭐ |

## 🚀 推薦部署方式

### 方案 1：VPS 部署 (最穩定)

**優點：**
- 完全控制
- 可運行 Ollama
- 24/7 運行
- 支援所有功能

**步驟：**
```bash
# 1. 購買 VPS (推薦：DigitalOcean, Linode, Vultr)
# 2. 執行部署腳本
chmod +x deploy_vps.sh
./deploy_vps.sh

# 3. 上傳專案檔案
scp -r tech_daily_bot/ root@your-vps:/opt/

# 4. 設定環境變數
nano /opt/tech_daily_bot/.env

# 5. 啟動服務
pm2 start ecosystem.config.js
```

**成本：** $5-15/月

### 方案 2：雲端函數 (最便宜)

**優點：**
- 按使用付費
- 無需維護
- 自動擴展

**限制：**
- 無法運行 Ollama
- 只能用 Gemini API
- 功能受限

**步驟：**
```bash
# 1. 部署到 Vercel/Netlify
npm install -g vercel
vercel --prod

# 2. 設定環境變數
vercel env add GEMINI_API_KEY
vercel env add TELEGRAM_BOT_TOKEN
```

**成本：** $0-10/月

### 方案 3：純 Web API (最簡單)

**優點：**
- 部署簡單
- Web 介面
- 可分享連結

**步驟：**
```bash
# 1. 部署到 Render/Fly.io
# 2. 設定環境變數
# 3. 訪問 Web 介面
```

**成本：** $0-7/月

## 🔧 快速部署到 Vercel (推薦新手)

```bash
# 1. 安裝 Vercel CLI
npm i -g vercel

# 2. 部署雲端版本
cd cloud_version
vercel --prod

# 3. 設定環境變數
vercel env add GEMINI_API_KEY
vercel env add TELEGRAM_BOT_TOKEN

# 4. 獲得 Web 介面連結
# 類似：https://tech-daily-bot.vercel.app
```

## 📱 使用雲端版本

### Web 介面版：
1. 訪問部署後的 URL
2. 點擊按鈕獲取新聞
3. 無需安裝任何軟體

### Telegram Bot 版本：
1. 設定 Webhook
2. Bot 24/7 在線
3. 隨時對話獲取新聞

## 🎯 最終推薦

**新手：** Vercel 雲端函數 (免費開始)
**進階：** VPS 部署 (功能最完整)
**企業：** Docker + Kubernetes (高可用)

## 📊 運行成本比較

- **Vercel Serverless**: $0-10/月
- **DigitalOcean VPS**: $5/月
- **AWS EC2**: $8-15/月
- **Google Cloud Run**: $0-20/月

選擇適合你需求和預算的方案！
