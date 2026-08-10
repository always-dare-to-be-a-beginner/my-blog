# 部署到 Cloudflare Pages（几乎免费）

脚手架已在本地跑通。下面这 3 步把博客真正上线，需要你自己的账号：

## 1. 推到 GitHub
```bash
git remote add origin git@github.com:你的名/my-blog.git
git branch -M main
git push -u origin main
```

## 2. Cloudflare Pages 连接仓库
1. 登录 Cloudflare 控制台 → **Workers & Pages → Create → Pages → Connect to Git**
2. 授权并选择 `my-blog` 仓库
3. 构建设置：
   - Build command: `npm run build`
   - Output directory: `dist`
4. 点 **Save and Deploy**，得到 `xxx.pages.dev` 临时域名，立刻可访问

## 3. 买域名并绑定（≈$10/年）
1. Cloudflare **Registrar** 搜索购买域名（如 `yourname.com`）
2. Pages 项目 → **Custom domains** → 输入域名 → 自动加 DNS + 免费 SSL
3. 等几分钟到几小时生效，之后用 `https://yourname.com` 访问

## 可选：本地预览与构建
```bash
npm run dev      # 本地预览 http://localhost:4321
npm run build    # 产出 dist/，可交给任意静态托管
```

## 备选：Vercel
- 导入 GitHub 仓库，Framework 选 Astro，Build `npm run build`、Output `dist`
- 同样支持自定义域名；免费额度大但有构建/带宽限额

## 提示
- `astro.config.mjs` 里的 `site` 改成你的正式域名，RSS / sitemap 才会生成绝对链接
- 想脱离 Git 在网页后台写文章，可接 Decap CMS 或 Astro Studio

## 排错：构建报 `bun run build failed`
Cloudflare Pages 靠锁文件判断包管理器：仓库里**没有 `package-lock.json`** 时会默认用 bun，跑 `bun run build` 导致构建失败。
- 修法：确保 `package-lock.json` 已提交进仓库（本项目已提交），并在 Cloudflare 项目 **Settings → Build & deployments** 把 Build command 显式设为 `npm run build`（输出目录 `dist`）。
- 若控制台菜单改名/找不到，直接 `git push` 任意改动即可触发一次新构建来复现/验证。
