# Realities Image with AI Watermark (真實照片 + AI 浮水印)

> 「這年頭，拿真實照片假裝是 AI 算出來的，才是最高段的諷刺——或者，只是攝影愛好者最後的溫柔。」

一個為攝影愛好者量身打造的「甩鍋型」輕量級網頁工具。本專案致力於將你拍壞的真實照片，打上各大 AI 繪圖平台的官方浮水印。

## 專案由來 (Origin)

網路上那些「高大上」的反思虛擬與真實、諷刺當代科技趨勢的理論，通通不是本專案的核心。

本專案的真正誕生原因非常純粹：
**我只是一個要技術沒技術的攝影愛好者，但我拍壞了照片不想承認。**

- 當相機對焦失敗，畫面一片模糊時 → **「這叫 AI 的迷焦感，演算法還不夠成熟。」**
- 當高光過曝、暗部死黑、甚至手震時 → **「嘖嘖，Midjourney 貼圖感太重，雜訊控制得真差。」**
- 當構圖詭異、路人被切到身體時 → **「AI 生成就是這樣，邊緣常常運算出錯。」**

只要把拍爛的照片通通賴到 AI 頭上，假裝這些是 AI 算出來的圖，就再也沒有人能質疑你的攝影技術。

## 技術棧 (Tech Stack)

本專案堅持 **Clean Code** 與**高擴充性架構**，杜絕拼湊式的 Vibe Coding，純前端運算，零後端伺服器成本。

- **Core Framework:** Vue 3 (TypeScript) + Vite
- **Build Tool:** Vite
- **Graphics Engine:** HTML5 Canvas API
- **Design Pattern:**
  - 將各個 AI 平台的浮水印（如 Midjourney、DALL-E 3）封裝為獨立的 `WatermarkStrategy` 類別。
  - 利用 `Path2D` 抽離 SVG Path 向量資料，確保 Logo 在 4K 高解析度真實照片下依然絕對銳利、不失真，並支援依據背景明暗動態變色。

## 快速啟動 (Getting Started)

### 前置準備

請確保你的開發環境已安裝 [Node.js](https://nodejs.org/) (建議 v18+) 與包管理器（`npm`）。

### 1. 複製專案庫

```bash
git clone https://github.com/GANSOONLEE/realities-image-with-ai-watermark.git
cd realities-image-with-ai-watermark
```

### 2. 安裝依賴套件

```bash
npm install
```

### 3. 啟動本地開發伺服器

```bash
npm run dev
```

### 4. 打包生產環境

```bash
npm run build
```

## 核心設計架構預覽

專案內部的浮水印渲染核心採用物件導向設計，若想擴充新的 AI 平台（例如 Adobe Firefly 或 Stable Diffusion WebUI 邊框），只需實作以下介面：

```typescript
export interface WatermarkStrategy {
  readonly name: string;
  readonly description: string;
  draw(ctx: CanvasRenderingContext2D, width: number, height: number): void;
}
```
