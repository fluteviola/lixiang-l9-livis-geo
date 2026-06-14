# GEO 首推形成机制分析 · 理想L9 Livis

单页静态 dashboard（`index.html`，自包含，仅依赖 CDN 的 Chart.js）。数据为 2026-06-13 单日快照。

## 部署到 GitHub Pages

### 方式 A：网页上传（最简单，无需命令行）
1. 在 GitHub 新建一个仓库，例如 `geo-dashboard`（Public）。
2. 进入仓库 → Add file → Upload files → 把本文件夹里的 `index.html`、`.nojekyll`、`README.md` 拖进去 → Commit。
3. 仓库 Settings → Pages → Source 选 `Deploy from a branch` → Branch 选 `main` / 根目录 `/ (root)` → Save。
4. 等 1–2 分钟，访问 `https://<你的用户名>.github.io/geo-dashboard/`。

### 方式 B：命令行（本文件夹已初始化好 git）
本文件夹已 `git init` 并完成首次 commit。在你本地（已登录 GitHub）执行：
```bash
# 1. 在 GitHub 先建好空仓库 geo-dashboard，然后：
cd geo-dashboard-deploy
git remote add origin https://github.com/<你的用户名>/geo-dashboard.git
git branch -M main
git push -u origin main
# 2. 到仓库 Settings → Pages 开启（Branch: main / root）
```
若装了 GitHub CLI（`gh`），可一步到位：
```bash
cd geo-dashboard-deploy
gh repo create geo-dashboard --public --source=. --push
gh api -X POST repos/<你的用户名>/geo-dashboard/pages -f source.branch=main -f source.path=/
```

## 说明
- `.nojekyll`：让 Pages 跳过 Jekyll，直接当静态站点服务（避免文件名/下划线问题）。
- 页面联网加载 Chart.js（cdnjs），目标环境需能访问 cdnjs.cloudflare.com。
- 数据口径：首推=车型层（理想L9）；Livis 为目标版本，提及率单列。
