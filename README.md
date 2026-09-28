# MINI GT INDEX

MINI GT 1:64 车型资料站。`worker/index.js` 是当前站点的完整源码，包含页面、1200 条车型资料及官网图片代理。`wrangler.toml` 指向 Cloudflare Worker `mini-gt-index`。

## 连接自动部署

在 Cloudflare 的 **Workers & Pages → mini-gt-index → Settings → Builds → Connect** 中连接 GitHub 仓库 `TeaganRicardo/MiniGTIndex`，选择 `main` 分支。根目录留空，Build command 留空，Deploy command 使用 `npx wrangler deploy`。连接完成后，向 `main` 推送新提交即自动部署到现有 Worker。首次连接时确认控制台 Worker 名称为 `mini-gt-index`。

## 修改网站

编辑 `worker/index.js`，提交并推送到 `main`。文件开头的 `PAGE` 字符串包含网页 HTML、样式、脚本和车型数据；文件末尾是 Worker 路由与 MINI GT 官网代理。数据与图片问题应在源码中修复，再由 Cloudflare 构建发布，避免只在控制台临时修改。

现有动态官网图片依赖 `/__minigt_proxy` 与 MINI GT 官网请求；仓库接入自动部署本身不会修复上游图片失败。
