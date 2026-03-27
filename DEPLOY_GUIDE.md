# 🚀 部署指南 — 从零到上线

> 这是你第一次操作，按顺序来就行，总共大约 10 分钟。

---

## 概念说明（30 秒看懂）

```
你的电脑（admin.html 管理数据）
        ↓ 点击「发布」导出 data.json
        ↓ 用 git push 上传到 GitHub
GitHub 服务器（自动生成网址）
        ↓
同事打开链接（看到 index.html 只读页面）
```

就这么简单：你管理 → 导出 → 上传 → 别人看到。

---

## 第一部分：首次部署（只做一次）

### 步骤 1：配置 Git 身份

打开「终端」应用（在 Mac 的 启动台 → 其他 → 终端），输入以下两行命令（把引号里的内容改成你自己的）：

```bash
git config --global user.name "你的名字"
git config --global user.email "你的GitHub注册邮箱"
```

例如：
```bash
git config --global user.name "Marvin"
git config --global user.email "marvin@example.com"
```

### 步骤 2：在 GitHub 上创建仓库

1. 打开浏览器，访问 https://github.com/new
2. 填写：
   - **Repository name**（仓库名）：填 `workspace`（或你喜欢的名字）
   - **Description**：随便写，比如「个人项目管理」
   - 选择 **Public**（公开，这样别人才能看到页面）
   - ⚠️ **不要勾选** 「Add a README file」（因为我们已经有了）
3. 点击绿色的 **Create repository** 按钮
4. 创建完成后，页面会显示一个地址，类似：
   ```
   https://github.com/你的用户名/workspace.git
   ```
   **复制这个地址**，下一步要用。

### 步骤 3：上传代码到 GitHub

在终端中，依次输入以下命令：

```bash
# 进入项目目录
cd ~/Documents/蘸酱的个人助手

# 添加远程仓库（把地址替换成你刚复制的）
git remote add origin https://github.com/你的用户名/workspace.git

# 把所有文件加入版本控制
git add .

# 创建第一个提交
git commit -m "首次发布"

# 上传到 GitHub
git push -u origin main
```

> 💡 第一次 push 时，系统可能会弹出 GitHub 登录窗口，正常登录即可。

### 步骤 4：开通 GitHub Pages

1. 打开你的仓库页面：`https://github.com/你的用户名/workspace`
2. 点击顶部的 **Settings**（设置）
3. 左侧菜单找到 **Pages**，点击进入
4. 在 **Source** 下面：
   - Branch 选择 `main`
   - 文件夹选择 `/ (root)`
5. 点击 **Save**
6. 等 1~2 分钟，页面顶部会出现你的网址：
   ```
   https://你的用户名.github.io/workspace/
   ```

✅ **这就是你分享给同事的链接！** 打开它应该能看到只读的展示页面。

---

## 第二部分：日常更新数据（以后每次都这样）

当你在 `admin.html` 里增删改了项目、任务或想法后，想让线上同步更新：

### 步骤 1：导出数据
1. 打开 `admin.html`（双击本地文件或在浏览器打开）
2. 点击侧栏底部的 **「↑ 发布到线上」** 按钮
3. 浏览器会自动下载一个 `data.json` 文件（通常在「下载」文件夹）

### 步骤 2：替换并上传
在终端中输入：

```bash
# 进入项目目录
cd ~/Documents/蘸酱的个人助手

# 用下载的文件替换旧的 data.json
cp ~/Downloads/data.json ./data.json

# 上传更新
git add data.json
git commit -m "更新数据"
git push
```

等 30 秒左右，同事刷新页面就能看到最新内容了。

---

## 常见问题

**Q：同事能修改我的数据吗？**
不能。他们看到的 `index.html` 是纯只读页面，没有任何编辑功能。

**Q：admin.html 别人能看到吗？**
技术上可以（如果他们猜到地址），但里面的编辑操作只改本地 localStorage，不会影响线上数据。你可以在 `.gitignore` 中加入 `admin.html` 来彻底隐藏它。

**Q：我改了页面的代码（样式/功能），怎么更新？**
和更新数据一样：
```bash
git add .
git commit -m "更新样式"
git push
```

**Q：忘记仓库地址了？**
```bash
git remote -v
```
