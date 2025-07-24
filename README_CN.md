### 简介
Astro Cactus是一个基于[Astro](https://astro.build)构建的简单且有主见的起始模板。使用它来创建一个易于使用的博客或网站。

### 目录
1. [主要特性](#主要特性)
2. [演示](#演示-💻)
3. [快速开始](#快速开始)
4. [预览](#预览)
5. [命令](#命令)
6. [配置](#配置)
7. [更新](#更新)
8. [添加文章](#添加文章)
    - [前置内容](#前置内容)
    - [前置内容片段](#前置内容片段)
9. [Pagefind搜索](#pagefind搜索)
10. [分析](#分析)
11. [部署](#部署)
12. [致谢](#致谢)

### 主要特性
- Astro v5 速度快🚀
- Tailwind v4
- 可访问的、语义化的HTML标记
- 响应式且对SEO友好
- 黑暗与明亮模式
- MD及[MDX](https://docs.astro.build/en/guides/markdown-content/#mdx-only-features)文章与笔记
    - 包括[警告](https://astro-cactus.chriswilliams.dev/posts/markdown-elements/admonistions/)
- [Satori](https://github.com/vercel/satori)用于创建开放图png图像
- [自动RSS提要](https://docs.astro.build/en/guides/rss)
- [Webmentions](https://webmention.io/)
- 自动生成：
    - [网站地图](https://docs.astro.build/en/guides/integrations-guide/sitemap/)
    - [robots.txt](https://github.com/alextim/astro-lib/blob/main/packages/astro-robots-txt/README.md)
    - [网络应用清单](https://github.com/alextim/astro-lib/blob/main/packages/astro-webmanifest/README.md)
- [Pagefind](https://pagefind.app/)静态搜索库集成
- [Astro Icon](https://github.com/natemoo-re/astro-icon) svg图标组件
- [Expressive Code](https://expressive-code.com/)代码块和语法高亮器

### 演示💻
查看[演示](https://astro-cactus.chriswilliams.dev/)，托管在Netlify上

### 快速开始
从此模板[创建一个新仓库](https://github.com/chrismwilliams/astro-theme-cactus/generate)。

```bash
# npm 7+
npm create astro@latest -- --template chrismwilliams/astro-theme-cactus

# pnpm
pnpm dlx create-astro --template chrismwilliams/astro-theme-cactus
```

[![使用Netlify部署](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/chrismwilliams/astro-theme-cactus) [![使用Vercel部署](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fchrismwilliams%2Fastro-theme-cactus&project-name=astro-theme-cactus)

### 预览
![Astro主题仙人掌在明亮主题模式下](https://github.com/chrismwilliams/astro-theme-cactus/assets/12715988/84c89d42-4525-4674-b10c-6d6ebdc06382)

![Astro主题仙人掌在黑暗主题模式下](https://github.com/chrismwilliams/astro-theme-cactus/assets/12715988/e0e575e2-445f-4c2d-a812-b5b53d2d9031)

### 命令
将pnpm替换为你选择的npm/yarn

| 命令 | 操作 |
| :-- | :-- |
| `pnpm install` | 安装依赖项 |
| `pnpm dev` | 在`localhost:3000`启动本地开发服务器 |
| `pnpm build` | 将你的生产网站构建到`./dist/` |
| `pnpm postbuild` | Pagefind脚本，用于构建你的博客文章的静态搜索 |
| `pnpm preview` | 在部署前本地预览你的构建 |
| `pnpm sync` | 根据`src/content/config.ts`中的配置生成类型 |

### 配置
- 编辑模板的配置文件`src/site.config.ts`
    - **重要**：使用你自己的域名设置`url`属性。
    - 修改由[Expressive Code](https://expressive-code.com)生成的markdown代码块的设置。Astro Cactus有黑暗（dracula）和明亮（github-light）两种主题。你可以在[这里](https://expressive-code.com/guides/themes/#available-themes)找到更多选项。
- 更新文件`astro.config.ts`
    - [astro-webmanifest选项](https://github.com/alextim/astro-lib/blob/main/packages/astro-webmanifest/README.md)
- 替换并更新`/public`文件夹中的文件：
    - icon.svg - 用作创建favicon和清单图标的源
    - social-card.png - 用作默认的og:image
- 使用你自己的明亮和黑暗样式修改文件`src/styles/global.css`，并自定义[Tailwind的主题设置](https://tailwindcss.com/docs/theme#customizing-your-theme)。
- 在`src/components/SocialList.astro`中编辑社交链接，以添加/替换你的媒体资料。图标可以在[icones.js.org](https://icones.js.org/)找到，按照[Astro Icon的说明](https://www.astroicon.dev/guides/customization/#find-an-icon-set)。
- 在`src/content/post/`和`src/content/note/`中使用.md/mdx文件为你的博客创建/编辑文章和笔记。有关更多详细信息，请参阅[下文](#添加文章和笔记)。
    - 阅读[这篇文章](http://astro-cactus.chriswilliams.dev/posts/webmentions/)，了解如何在你的网站上添加Webmentions。
- OG图像：
    - 如果你想更改Satori库生成的图像样式，打开`src/pages/og-image/[slug].png.ts`到标记函数，在那里你可以根据需要编辑html/tailwind类。你可以使用这个[游乐场](https://og-playground.vercel.app/)来辅助你的设计。
    - 你也可以创建自己的og图像，并通过在前置内容中添加一个指向资产的链接的ogImage属性来跳过satori为你生成它，一个示例可以在`src/content/post/social-image.md`中找到。有关前置内容的更多信息可以在[这里](#前置内容)找到。
- 可选：
    - 字体：此主题在`src/layouts/Base.astro`中的`<body>`上将body元素设置为字体家族`font-mono`。你可以通过删除变体`font-mono`来更改字体，之后TailwindCSS将默认为`font-sans` [字体家族堆栈](https://tailwindcss.com/docs/font-family)。

### 更新
如果你已经分叉了模板，你可以将分叉与你自己的项目[同步](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/syncing-a-fork)，记住不要点击“丢弃更改”，因为你会丢失自己的更改。

如果你有一个模板仓库，你可以按照[这里](https://stackoverflow.com/questions/56577184/github-pull-changes-from-a-template-repository)讨论的那样，将此模板添加为远程仓库。

### 添加文章和笔记
此主题使用[内容集合](https://docs.astro.build/en/guides/content-collections/)来组织本地Markdown和MDX文件，并使用模式`src/content.config.ts`对前置内容进行类型检查。

添加文章/笔记就像将你的.md(x)文件添加到`src/content/post`和/或`src/content/note`文件夹一样简单，文件名将用作slug/url。此模板中包含的文章是前置内容结构的示例。此外，[Astro文档](https://docs.astro.build/en/guides/markdown-content/)有关于markdown页面的详细部分。

#### 文章前置内容
| 属性（*必填） | 描述 |
| :-- | :-- |
| title * | 不言自明。用作文章的文本链接、文章页面上的h1以及页面的标题属性。最大长度为60个字符，在`src/content/config.ts`中设置 |
| description * | 与上述类似，用作SEO描述属性。最小长度为50，最大长度为160个字符，在文章模式中设置 |
| publishDate * | 同样很简单。要更改日期格式/区域设置，目前是**en-GB**，在`src/site.config.ts`中更新日期选项。请注意，如果需要，你也可以将其他选项传递给`<FormattedDate>`组件 |
| updatedDate | 这是一个可选日期，表示文章何时更新，格式与publishDate相同 |
| tags | 任何创建的文章都可以使用标签。任何新标签将显示在`yourdomain.com/posts`和`yourdomain.com/tags`中，并生成页面`yourdomain.com/tags/[yourTag]` |
| coverImage | 这是一个可选对象，将在文章顶部添加封面图像。包括`src`：“_图像路径_”和`alt`：“_图像替代文本_”。你可以在`src/content/post/cover-image.md`中查看示例 |
| ogImage | 这是一个可选属性。如果未提供此属性，将为每篇文章自动生成一个OG图像。如果你想为特定文章创建自己的图像，包括此属性并链接到你的图像，然后主题将跳过自动生成 |
| draft | 这是一个可选属性，因为它在模式中默认设置为false。通过添加true，文章将在许多地方从生产构建中过滤掉，包括getAllPosts()调用、og图像、rss提要和生成的页面 |

#### 笔记前置内容
| 属性（*必填） | 描述 |
| :-- | :-- |
| title * | 字符串，最大长度60个字符 |
| description | 用于头部元描述属性 |
| publishDate * | ISO 8601格式，允许有偏移量 |

#### 前置内容片段
Astro Cactus包括一个有用的VSCode片段，用于为文章和笔记创建前置内容“存根”，可以在这里找到 -> `.vscode/post.code-snippets`。在新创建的.md(x)文件上开始输入单词“frontmatter”以触发它。Visual Studio Code片段通过mac上的(⌃Space)、windows上的(Ctrl+Space)出现在IntelliSense中。

### Pagefind搜索
此集成带来了一个用于搜索博客文章和笔记的静态搜索功能。在当前形式下，Pagefind仅在网站构建后才起作用。此主题添加了一个postbuild脚本，应在Astro构建网站后运行。你可以通过运行build && postbuild在本地进行预览。

搜索结果仅包括文章和笔记中的页面。如果你想包括其他/所有页面，请将属性`data-pagefind-body`从`src/layouts/BlogPost.astro`和`src/components/note/Note.astro`中的article标签中删除/重新定位。

它还允许你通过博客文章前置内容中添加的标签过滤文章。如果你想删除此功能，请从`src/components/blog/Masthead.astro`中的链接中删除数据属性`data-pagefind-filter="tag"`。

如果你不想包括此集成，只需删除组件`src/components/Search.astro`，并从package.json中卸载`@pagefind/default-ui`和`pagefind`。你还需要从这里删除postbuild脚本。

你可以通过延迟加载Web组件样式来减少CSS的初始有效负载，如[这里](https://github.com/chrismwilliams/astro-theme-cactus/pull/145#issue-1943779868)所示。

### 分析
你可能想跟踪你的博客/网站收到的访问者数量，以了解趋势和你创建的热门文章/页面。有许多提供商可供使用，包括网络主机，如[Vercel](https://vercel.com/analytics)、[Netlify](https://www.netlify.com/products/analytics/)和[Cloudflare](https://www.cloudflare.com/web-analytics/)。

由于有许多用例和/或选项，有些人可能会使用，有些人可能不会使用，此主题/模板不包括特定的解决方案。

在设置网站时，你可能会被要求在网站的**HEAD**标签中包含一个代码片段，该代码片段可以在`src/layouts/Base.astro`中找到。或者，你可以在`src/components/BaseHead.astro`中添加代码片段。

### 部署
[Astro文档](https://docs.astro.build/en/guides/deploy/)有一个很棒的部分，详细介绍了如何在各种平台上部署你自己的Astro网站及其特点。

默认情况下，网站将被构建（见上文[命令](#命令)部分）到`/dist`目录。

### 致谢
此主题受[Hexo主题仙人掌](https://github.com/probberechts/hexo-theme-cactus)的启发

### 许可证
MIT
