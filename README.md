# Stable Diffusion WebUI - Google Colab Pro 版 (Fast Deployment)

![GitHub](https://img.shields.io/github/license/yourusername/fast-sd-colab?style=flat-square)
![Colab](https://img.shields.io/badge/Google-Colab-%23F9AB00?style=flat-square&logo=google-colab)
![Stable Diffusion](https://img.shields.io/badge/Stable%20Diffusion-AUTOMATIC1111-blue?style=flat-square)

> 一鍵部署 **AUTOMATIC1111 Stable Diffusion WebUI** 到 Google Colab Pro，支援：
> - SD 1.5 / SDXL / 自訂模型
> - LoRA 自動下載
> - ControlNet 全模型支援
> - Cloudflare Tunnel 免費穿透（替代 ngrok）
> - 完整 Google Drive 持久化儲存

> 基於 [TheLastBen/fast-stable-diffusion](https://github.com/TheLastBen/fast-stable-diffusion) 優化改良

---

## 特色功能

| 功能 | 說明 |
|------|------|
| **Cloudflare Tunnel** | 免費、無限流量、穩定穿透（無 ngrok 限制） |
| **Google Drive 持久化** | 模型、LoRA、ControlNet 儲存在雲端，關閉後不遺失 |
| **SDXL / 1.5 / Inpaint** | 一鍵切換主流模型 |
| **ControlNet v1/v2/XL** | 完整支援 Canny、Depth、OpenPose 等 |
| **LoRA 自動下載** | 支援 CivitAI、Google Drive、HuggingFace |
| **自訂模型路徑** | 可指定任意資料夾或單一檔案 |
| **中文化介面** | 按鈕、提示全中文化 |

---

## 快速開始

### 1. 開啟 Colab Notebook

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/yourusername/fast-sd-colab/blob/main/Fast_Stable_Diffusion_Colab.ipynb)

> 根據Google現行規範，Stable Diffusion WebUI僅在 **Colab Pro / Pro+** 使用 ，否則無法正常安裝。  

---

### 2. 執行順序

按順序執行以下區塊：

| 步驟 | 說明 |
|------|------|
| 1. Connect Google Drive | 掛載你的 Google Drive |
| 2. Install/Update AUTOMATIC1111 repo | 下載並更新 WebUI |
| 3. 安裝需求 | 安裝相容性修復與加速庫 |
| 4. Model Download/Load | 選擇 SDXL 或自訂模型 |
| 5. Download LoRA *(選填)* | 下載 LoRA 模型 |
| 6. ControlNet *(選填)* | 下載 ControlNet 模型 |
| 7. Start Stable-Diffusion | 啟動 WebUI |

---

## Cloudflare Tunnel 使用說明

### 方法 A：使用自有域名（推薦）

1. 前往 [Cloudflare Zero Trust](https://one.dash.cloudflare.com)
2. 建立 Tunnel → 選擇 `Cloudflared`
3. 複製生成的 **Token**
4. 在 Colab 中勾選 `use_cloudflare_tunnel = True`
5. 貼上 Token 到 `cf_token` 欄位
6. 執行 → 成功後會顯示：

   Cloudflare Tunnel 已啟動，等「Connected」出現後，即可連到你在 Cloudflare 儀表板所設定的網域

### 方法 B：匿名快速鏈接（免設定）

- 不填 `cf_token`，系統會自動產生 `*.trycloudflare.com` 網址
- 適合快速測試

---

## 模型下載來源支援

| 來源 | 支援格式 |
|------|----------|
| Civitai | 自動解析檔名 |
| Google Drive | 分享連結（需啟用「任何人可下載」） |
| HuggingFace | 直接下載連結 |
| 本機路徑 | `/content/gdrive/MyDrive/...` |

---

## 資料夾結構（Google Drive）

MyDrive/  
└── sd/  
    └── stable-diffusion-webui/  
        ├── models/  
        │   ├── Stable-diffusion/  ← 主模型  
        │   └── Lora/             ← LoRA 模型  
        └── extensions/  
            └── sd-webui-controlnet/  
                └── models/       ← ControlNet 模型  

---

## 常見問題

### Q：為什麼我看不到 WebUI？
> 請等待 `Running on local URL: http://127.0.0.1:7860` 出現，再點擊 Cloudflare 連結。

### Q：模型下載很慢？
> 使用 **Colab Pro+** + **靠近美國/歐洲的時段** 會較快。

### Q：Cloudflare Tunnel 連不上？
> 檢查 Token 是否正確，或嘗試匿名模式。

### Q：想用 ngrok？
> 取消勾選 `use_cloudflare_tunnel`，系統會自動切回 `--share`。

---

## 鳴謝

TheLastBen - 原始 fast-stable-diffusion
AUTOMATIC1111
Mikubill/sd-webui-controlnet
Cloudflare Zero Trust

授權MIT License (LICENSE)
