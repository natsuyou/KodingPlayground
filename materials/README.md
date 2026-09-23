# 延伸教材素材放置處

把每筆教材的截圖（screenshot）、hover預覽影片/GIF（hoverPreview）檔案放在這個資料夾底下，**用教材id當檔名前綴**，扁平放置即可，不用每個教材開資料夾：

```
public/materials/google-rabbit-coding.png          ← 截圖
public/materials/google-rabbit-coding-preview.mp4  ← hover預覽（用 -preview 字尾區分）
```

然後在 `src/data/extensionMaterials.json` 裡填**相對路徑（不要加開頭的斜線 `/`）**：

```json
"screenshot": "materials/google-rabbit-coding.png",
"hoverPreview": "materials/google-rabbit-coding-preview.mp4",
```

**為什麼不能用開頭斜線的絕對路徑？** 因為網站部署在 `https://natsuyou.github.io/KodingPlayground/` 這種子路徑下，寫死開頭斜線（例如 `/materials/xxx.png`）會被瀏覽器誤認為根目錄 `https://natsuyou.github.io/materials/xxx.png`（少了 `/KodingPlayground/`），圖片就會抓不到。改用不加斜線的相對路徑，程式（`MaterialCard.vue` 的 `resolvePublicAsset()`）會自動幫你補上正確的子路徑前綴。
