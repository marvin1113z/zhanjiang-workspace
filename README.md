# Workspace — 个人项目管理系统

Marvin 的个人项目管理看板，用于向团队展示工作进度。

## 文件结构

| 文件 | 用途 |
|------|------|
| `index.html` | **展示页面**（只读）— 分享给同事的链接 |
| `admin.html` | **管理页面** — 你自己管理项目/任务/想法 |
| `data.json` | 数据文件 — 由管理页面导出 |

## 使用流程

### 1. 日常管理（本地）
在浏览器打开 `admin.html`，正常管理你的项目、任务和想法。数据存储在浏览器 localStorage。

### 2. 发布到线上
1. 在 `admin.html` 点击侧栏底部的 **「↑ 发布到线上」** 按钮
2. 浏览器会下载一个 `data.json` 文件
3. 用它替换本仓库中的 `data.json`
4. 提交并推送到 GitHub：
   ```bash
   git add data.json
   git commit -m "更新数据"
   git push
   ```
5. GitHub Pages 会自动更新，同事刷新页面即可看到最新内容

### 3. 首次部署到 GitHub Pages
1. 在 GitHub 创建一个仓库（如 `workspace`）
2. 推送代码：
   ```bash
   git remote add origin https://github.com/你的用户名/workspace.git
   git push -u origin main
   ```
3. 进入仓库 Settings → Pages → Source 选择 `main` 分支 → Save
4. 等待 1-2 分钟，访问 `https://你的用户名.github.io/workspace/` 即可

### 4. 后续迭代
修改 `index.html` 或 `admin.html` 的代码后，push 到 GitHub 即自动生效。
