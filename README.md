# 个人主页

我的作品集主页：一个静态页面，把我在用的几个投资工具收在一起，方便别人查看和使用。

线上地址：https://gyhok368519.github.io/

## 怎么改内容

**只需要改一个文件：`index.html`。**

页面里所有内容都由 `index.html` 底部的 `PROJECTS` 数组生成。新增一个作品，就在数组里加一段：

```js
{
  title: "作品名",
  desc:  "一句话说清楚它能干什么",
  tags:  ["标签1", "标签2"],
  url:   "https://线上地址",
  status: "live"        // live 已上线 / soon 待上线 / proto 原型
}
```

会出现的两种情况：

- `url` 填了地址 → 卡片可以点击，直接跳转过去
- `url` 留空 `""` → 卡片显示成灰色、不可点击，适合还没上线的作品

改完保存，刷新浏览器就能看到效果。

个人的名字、头像字、简介在文件靠上的 `<header>` 和 `<p class="bio">` 里，直接改文字即可。

## 怎么发布到 GitHub Pages

### 第一次发布

1. 登录 GitHub，点右上角 **+** → **New repository**
2. 仓库名必须填 `gyhok368519.github.io`（一字不差，这是 GitHub 的固定规则，用这个仓库名才能得到 `https://gyhok368519.github.io` 这个地址）
3. 可见性选 **Public**，不要勾选 "Add a README file"
4. 点 **Create repository**
5. 在本文件夹里打开命令行，依次执行：

```bash
git init
git add .
git commit -m "个人主页第一版"
git branch -M main
git remote add origin https://github.com/gyhok368519/gyhok368519.github.io.git
git push -u origin main
```

推送时如果要求输入密码，要填 **Personal Access Token**（不是 GitHub 登录密码）。

6. 等 1-2 分钟，打开 https://gyhok368519.github.io/ 就能看到页面

### 以后更新

改完 `index.html` 之后：

```bash
git add .
git commit -m "更新内容"
git push
```

等一分钟，线上自动更新。

## 文件说明

| 文件 | 作用 |
|---|---|
| `index.html` | 整个主页，包含样式、内容、逻辑 |
| `.nojekyll` | 告诉 GitHub Pages 不要用 Jekyll 处理，留着别删 |
| `README.md` | 本说明文件 |

## 为什么要保持单文件

整站只有一个 `index.html`，没有外部依赖、没有构建步骤。好处是：

- 任何地方双击就能打开，不需要装环境
- 想搬到别的平台（Cloudflare Pages、Vercel 等）直接拷过去就行
- 以后要绑定自己的域名，也不用改任何代码
