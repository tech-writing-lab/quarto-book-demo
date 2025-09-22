# quarto-book-demo

## 於本機建置

作業環境：Windows 11

- Visual Studio Code
- [Visual Studio Code extension for Quarto](https://marketplace.visualstudio.com/items?itemName=quarto.quarto)
- [Quarto CLI](https://quarto.org/docs/get-started/)
- [Noto Serif 繁體中文字型](https://fonts.google.com/noto/specimen/Noto+Serif+TC) - 若沒有安裝此字型，生成的 pdf 檔案裡面的中文會是亂碼或豆腐（方塊字/口口口）。

> 備註：安裝完成 Quarto CLI 之後，須重新啟動 Visual Studio Code。

安裝好上述工具後，為了在本機執行 `quarto render` 來測試生成 pdf，還需要使用以下命令來安裝 tinytex：

```shell
quarto install tinytex
```

欲生成書籍檔案，在此專案根目錄下執行：

```shell
quarto render
```

若執行成功，專案根目錄下的 `_output` 資料夾裡面會有三種格式的電子書：HTML、EPUB、PDF。

## GitHub Workflow 部署流程

> 備註：這個部分尚未測試。

Workflow 檔案：.github/workflows/quarto.yml

說明：

1. Build job

    - 負責產生 PDF 與 HTML，並保存 PDF 成果（artifact）。

2. Deploy job

    - 只產生 HTML（比較快），並部署到 GitHub Pages。

3. GitHub Pages 設定

    - 進入 GitHub 專案 → Settings → Pages
    - Source 選擇 GitHub Actions
    - 完成後，書籍會自動發佈在 https://你的帳號.github.io/你的專案名/