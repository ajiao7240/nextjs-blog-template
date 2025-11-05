---
title: 独立开发者 SaaS 模板
date: 2025-04-05T20:10:00+08:00
updated: 2025-04-05T20:10:00+08:00
keywords: ["hello", "world"]
featured: true
summary: "这篇文章包含markdown语法基本的内容。"
---
# 独立开发者 SaaS 模板

在过去两个月的时间里，我一直致力于开发一个让我自己满意的 Next.js 模板，到今天为止，这个模板已经非常接近我想要的样子，并且支持部署到所有云平台中。包括但不限于 Vercel, Cloudflare Workers, AWS, Railway, Fly.io, Zeabur, GCP, Azure 等。所以也是时候推出 [NextDevKit](https://nextdevkit.com/) 和大家见面啦🔥

![NextDevKit 模板](https://storage.guangzhengli.com/images/nextdevkit-screenshot.png)

其实现在优秀的 Next.js 模板挺多的，只要你在 Google 中搜索 `nextjs saas template` 或者 `nextjs starter kit`，你可以找到很多优秀的模板，包括但不限于开源项目的和商业付费的。

## 为什么我开发一个 Next.js 模板？

那为什么我还要自己重新开发一套 Nextjs 的模板呢，一方面是因为这些模板或多或少都存在一些问题，以一些开源的项目为例，例如 Vercel [官方的 Saas 模板](https://vercel.com/templates/saas)，这些模版的功能过于简单，我每次启动一个新的项目，我都需要手动添加一些功能，比如发送邮件，支付，连接我不同的数据库以应对不同的需求。

所以我之前每次启动新项目的时候，我都是去找不同的模板来满足我的需求，但是这样每次都要花费我很多时间，每次都有新的学习成本。

那么为什么我不直接购买一个商业付费的模板呢？其实我之前已经购买了 [https://supastarter.dev/](https://supastarter.dev/) 这个模板，这个模版其实挺好的，功能齐全，代码写的也不错，开发起来也还算丝滑。

### UI 样式问题

但是这个模板有几个问题是我一直比较在意的，第一个是这个模板的 demo 样式太简陋了，虽然后端功能齐全，但是前端样式太简陋了，大家可以对比[官网](https://supastarter.dev/) 和 [demo](https://demo.supastarter.dev/en) 的 landing page，可以发现很明显启动的 demo UI 样式太简陋了，导致每次我都需要重新设计 landing page。

其实这也是大部分商业付费模板的通病，比较出名的还有 [shipfast](https://shipfa.st/) 和 [makerkit](https://makerkit.dev/) 等，大家可以访问 demo 页面自行查看效果。

我猜测可能是因为大部分模板都是由开发者来主导，所以对于 UI/UX 等细节的打磨上，就比较放松。所以我这次在设计模板的 UI 上，也是花费了大量的时间，从 landing page 到博客，再到 dashboard 等，都花了很多的时间在 UI 调优上，大家可以访问 [nextdevkit demo](https://demo.nextdevkit.com/) 和 [nextdevkit workers demo](https://workers.nextdevkit.com/) 查看效果。

### 复杂度和功能性

第二个问题是复杂度的问题，这个模板虽然功能齐全，但是代码的复杂度挺高的，因为为了支持不同的平台和不同的功能，例如 Email 要支持 Resend，Plunk，Mailgun 等，所以这个模板采用的是 monorepo 的架构，并且使用了大量的第三方库，monorepo 的架构虽然可以方便的进行依赖管理，但是学习成本和维护成本都挺高的。

![NextDevKit 模板技术栈](https://storage.guangzhengli.com/images/nextdevkit-template.png)

所以，我这次在设计模板的时候，也是尽可能的简化代码的复杂度，使用传统的 Next.js 的项目结构，并且尽可能的减少第三方库的使用。

但说实话，从我开发这个模板的过程中，发现对于一个商业付费模板而言，复杂度和功能性的博弈是最难把握的一点，加入一些功能是很容易的，但是要保证学习成本和用户的维护成本在可控范围内，并且还要保证代码的易读性和可维护性，就很难了。

没有人想要购买到的是一个功能非常简单，样式非常简陋的模板，毕竟这意味着需要花费大量的时间重新造轮子和写代码。但我想的是，可能也没有人想要购买到的是一个功能和臃肿并存的模板，这意味着学习成本和维护成本都非常高，每次使用可能都要去删除一些不需要的功能和代码，并且还要花费大量的时间去理解使用不到的代码。

所以这次设计的代码，我的首要目标是保证完整的功能性，例如：

-   [数据库集成](https://nextdevkit.com/docs/database)
-   [认证](https://nextdevkit.com/docs/authentication)
-   [邮件](https://nextdevkit.com/docs/email)
-   [支付](https://nextdevkit.com/docs/payment)
-   [存储](https://nextdevkit.com/docs/storage)
-   [博客](https://nextdevkit.com/docs/blog)
-   [文档](https://nextdevkit.com/docs/docs)
-   [国际化](https://nextdevkit.com/docs/i18n)
-   [分析](https://nextdevkit.com/docs/analytics)
-   [多主题](https://nextdevkit.com/docs/themes)
-   [SEO 优化](https://nextdevkit.com/docs/seo)

至于还有其他的一些功能，例如 AI，更加丰富的组件，更加定制化的功能，虽然在后续版本中也会陆续支持，但是我会考虑以其它的方式进行支持，例如通过 Cursor，MCP 等方式进行支持，这样可以更加的灵活，不会在代码中无限制的添加功能。

### 部署的难题

第三个问题是现在市面上所有的 Next.js 模板，都存在一个共同的问题，那就是部署的难题。

因为 Next.js 的部署方式非常多样，包括但不限于 Vercel, Cloudflare Workers, AWS, Railway, Fly.io, Zeabur, GCP, Azure 等。

每个平台都有不同的优缺点，例如 Next.js 的官方部署平台 [Vercel](https://vercel.com/)，虽然部署非常方便，对于功能的支持也是最全面的，但是收费有时候需要额外注意，例如 Image Optimization 和 ISR 等，对于某些个人的开发项目，例如非盈利的项目和访问量非常大的项目，可能会进入价格和为爱发电的博弈中。

还有一大类是像 Cloudflare Workers 这样的平台，价格非常的便宜，每个月 $5 就可以放心大胆的使用 Workers, R2, D1, KV 等等资源，并且还有免费的 CDN 和 DNS 服务，对于个人开发者来说，是一个非常不错的选择。

但是 Cloudflare 的缺点也很明显，那就是社区和官方对于 Next.js 的支持到目前为止都一般，如果你要重头开发，基本一步一个坑，而且还很难找到解决方案，我在设计 NextDevKit Cloudflare workers 模板的时候，也是踩了很多的坑，因为对于很多库和第三方的不支持，然后又要保证每个模版的功能性一致，所以还重构了很多代码，替换了一些库。

> 特别是官方的 Cloudflare Pages 项目，因为只支持 Edge 环境，几乎没有办法支持这个 Next.js 模板的全部功能，所幸的是有 [Opennext](https://opennext.js.org/cloudflare) 这个项目，虽然也有一些小坑，但是最终还是支持了全部的功能。

最后还有一类是像 AWS, GCP, Azure 这样的云平台，因为有一些项目的合规性和隐私性问题，所以必须选择这些大的云平台来部署。

这些平台虽然功能支持的非常全面，但是部署起来非常麻烦，需要花费大量的时间去配置和优化，每次都需要从 Infra 开始搭建。

所以，我这次专门设计了 NextDevKit AWS 模板，也是尽可能的简化部署的难度，使用 [SST](https://sst.dev/) 来部署，不需要从 Infra as Code 开始，只需要使用 SST 的 CLI 工具，就可以非常方便的部署到 AWS 上。并且还支持 Serverless 的架构和 ECS 容器两种部署方式，对于企业级开发来说，是一个非常不错的选择。

最后，是对于容器部署的支持，本次设计的模板除了对 Cloudflare Workers 和 AWS 原生支持来减少部署的难度之外，其它平台都暂时仅支持容器部署，像 Railway, Fly.io, Dokploy 等。

其实上面的部署需求是我日常的开发难题，因为我的之前有些项目是非盈利的，并且访问量还挺大，部署在 Vercel 上一直需要担心账单，所以像 Cloudflare Workers 这样的平台就非常适合我。还有一些项目是企业级的，是直接管理在外国客户的 AWS 上，每次构建一个像 Next.js AI demo 这样的项目都要从 Infra 开始搭建，需要考虑安全和功能性等等，非常麻烦。

所以，我这次专门设计了三种不同的模板和部署方式，来满足不同的需求。其中 Cloudflare Workers 和 AWS 都是原生的平台支持的。

## 模板功能

### UI 和主题

上面介绍完了为什么我开发这个模板，以及我对于这个模板的设计理念，下面我来介绍一下这个模板的功能和遇到的一些难题。

首先是 Landing Page (落地页)的开发，因为对于启动一个新项目而言，Landing Page 是必不可少的一步，是用户了解你的项目的第一印象，所以对于 Landing Page 的开发，我也是花费了大量的时间来设计，包括但不限于调研高转化率的 Landing Page 的样式，实现这些组件，保持样式的统一等。

像下面的图片就是我之前调研过，发现一个高转化率的 Landing Page 的样式，所以这次我也参考了这些样式。大家可以访问 [nextdevkit demo](https://demo.nextdevkit.com/) 查看效果。

![Good Landing Page](https://storage.guangzhengli.com/images/landing-page.jpeg)

你可能会顾虑使用这个模板来开发不同的项目，对于每个项目的 Landing page 相同是不是会审美疲劳，对于这个问题我也进行了思考，我通过 [tweakcn](https://tweakcn.com/editor/theme) 这个项目支持不同的主题颜色和样式。只需要在这个网站中复制主题颜色的代码，粘贴到一个文件中，即可进行替换。大家可以访问下面的网站来查看效果。

-   [NextDevKit 官网主题](https://nextdevkit.com/)
-   [NextDevKit Demo 主题](https://demo.nextdevkit.com/)
-   [NextDevKit AWS Demo 主题](https://aws.nextdevkit.com/)
-   [NextDevKit Workers Demo 主题](https://workers.nextdevkit.com/)

可以看到除了颜色会进行变化外，有一些小组件的样式也会发生变化，例如 `button`，`input`，`card` 的样式，还有 `padding`，`margin`，`border-radius` 等，无论你喜欢哪种风格，这些组件都能做到保持相对的统一和好看。

还有包括但不限于登录注册页面，设置页面，Dashboard 页面，每个页面的 UI 样式我都尽量保持一致，不会出现很突兀的组件样式。后续你只需要让 AI IDE 模仿这些组件的样式进行开发即可，能够很大程度减少从头开发 UI 样式的焦虑和挫败。后续也会考虑将 UI 设计思路写到像 Cursor Rules 中，让 AI 自动保持样式统一。

当然对于暗黑模式和移动端支持也是无条件支持的，还有像 Blog 页面我都专门进行 Notion 的样式设计靠齐，尽量保持简洁和现代，不会很简陋或者复杂。甚至连 404 页面我都进行了专门的设计，可以想象我对这个模板倾注的时间，你可以访问 [nextdevkit demo 404](https://demo.nextdevkit.com/404) 查看效果。

但是我觉得对于这些组件的 UI/UX 花费的时间是值得的，除了能加快你的开发速度和 UI 焦虑，我自己后续也要用这个模版进行其它项目的开发哈哈。

### 技术选型

对于一个模板而言，最大的作用就是加快开发速度，所以对于技术选型，我也是尽可能的选用最流行和最好用的技术栈。

之前我有一篇博客是介绍 [独立开发技术栈](https://guangzhengli.com/blog/zh/indie-hacker-tech-stack-2024) 的，获得了大家的广泛关注和评价，这次的选型我除了参考当时的那篇博客，还根据 AI 友好性做了一些调整。

毕竟对于现在 2025 年的开发而言，对于开发者友好的技术栈还在其次，对于 AI 友好的技术栈才是王道。只要这个技术栈的生态能够被 AI 学习，开发者就能事半功倍。下面是选型技术栈的详细介绍。

-   框架使用 Next.js 最新版本，支持了 React 19 的特性，对于全栈开发而言，目前没有一个框架能比 AI 写 Next.js 更快更准确了。
-   使用 Tailwind CSS 4 版本，Tailwind CSS 是一种 AI 友好的代码风格。在 AI IDE 出现后，其它 CSS 框架都逐渐消亡。
-   使用 Shadcn UI 组件，Shadcn UI 目前生态广，组件也非常丰富，选型理由还是 AI First。并且后续会在社区分享到哪里找到好看的 组件，Shadcn 组件进行快速开发。
-   数据库 ORM 使用 Drizzle ORM，目前能够进行选择范围的只有 Drizzle ORM 和 Prisma ORM，其实我个人觉得 Prisma 的开发体验和代码设计都挺好的，但是架不住 Drizzle 的性能好，生态完善。因为模板需要部署到 Serverless 平台，所以需要选择一个面向 Edge 环境的 ORM，Drizzle 是最佳选择。
-   Auth 选择的是 Better Auth，没有选择 NextAuth(Auth.js) 的原因是因为文档不行，并且过去几年一直在变动。反而用过 Better Auth 后，发现开发体验和代码设计都很好，生态非常完善，对于 Auth 这种安全框架来讲，千万不要重复造轮子，选择一个生态完善，文档齐全，并且有社区支持的框架就是最好的选择。
-   Blog 和 Docs 我选择了 FumaDocs + FumaDocs MDX 来开发，FumaDocs 是我今年发现的一个非常好的文档框架，本来我以往都是使用 Content Collection 来开发，但是后来发现 FumaDocs 的代码设计和社区活跃度都很好，特别是 FumaDocs 的作者，在 Github 上非常活跃，并且对于文档的开发和维护也非常用心。如果你也需要维护文档或者博客，不妨试试 FumaDocs(看到好的项目总是忍不住分享)。
-   邮件服务使用 Resend，支付服务使用 Stripe，这两个服务都是目前最流行的服务，生态非常完善，并且对于开发者非常友好。后续也会支持其它的第三方，特别是支付，后续会对于一些支持国内开发者的支付服务进行优先支持。
-   Storeage 对象存储优先支持 AWS S3 和 Cloudflare R2，其实这两个使用的是同一个协议，只要是使用 S3 协议的理论上都支持。
-   i18n 国际化使用的是 next-intl，其实加上 i18n 功能后，整个项目的代码复杂度提高了一个级别，因为需要支持多语言，所以一些变量的抽取和跳转需要单独处理，但是 i18n 对于很多人来讲又是必要的，所以最后还是加上了。

除了上面的技术栈外，还有一些特殊的优化，例如对于 Cookie 和 Analytics 的优化，Analytics 目前支持 Google Analytics，Umami，Plausible 等，后续会支持更多。并且我针对于 GDPR 等隐私收集法规，在模板中进行了专门的优化，如果用户不同意收集数据，则不会收集任何数据。

其实现在大部分市场上的模板都没有在意 GDPR 等隐私收集，做好了这些细节可以让你的项目更加符合法规要求，更容易收获到用户的信任。

除此之外，对于 SEO，我也是进行了专门的优化，包括但不限于 sitemap 的生成，robots.txt 的生成，og:image 的生成，不同页面的 metadata 的生成等，博客的 keywords 优化等，最后通过 Google SpeedTest 测试得到 100 分。

如果你对于模板的功能还有一些疑惑，可以访问 [NextDevKit 官网文档](https://nextdevkit.com/docs) 查看详细的文档和功能介绍。

![NextDevKit 文档](https://storage.guangzhengli.com/images/nextdevkit-configuration.png)

目前的文档只支持英文，后续在稳定后会支持中文文档。

## Cloudflare Workers 模板

除了上面的模板功能外，这次开发的模板重点是解决大部分人的部署难题，对于我个人来讲，我常用的平台有四个。

第一个当然是 Vercel，我很多的 demo 或者个人使用的小项目都部署在上面，毕竟 Vercel 对于 Next.js 的支持没啥好说的，如果不考虑价格和团队资源管理的话，Vercel 是最佳选择。我也有部分小的商业项目也在 Vercel 上部署，不放一些大项目是因为 Vercel 的价格变动的还是比较频繁的，并且有一些你可能想象不到的地方收费，最经典的就比如 Image Optimization，如果你的项目访问量比价大并且有大量的图片渲染，没有关掉 Image Optimization 每个月几千刀的账单都很正常。

Cloudflare 在中文互联网一般被称为赛博菩萨，因为免费的 CDN 和防 DDOS 攻击的能力等，一直都很受个人开发者的欢迎，所以在 Cloudflare Pages 推出官方的 `@cloudflare/next-on-pages` 框架支持 Next.js 后，我就一直在探索如何使用 Cloudflare 来部署 Next.js 项目，并且支持所有常用的功能。

但是在去年我尝试过使用 Cloudflare Pages 来部署一个生产 Next.js 项目后，我实际上就已经放弃了这个框架，先不说几乎每一步都是坑，找不到框架资料，要从源码看起，官方社区的回复和支持也不够，最重要的是官方的 `@cloudflare/next-on-pages` 框架是基于纯 `Edge runtime` 的，对于一些需要使用 `Node.js` 的库支持的并不好，大量的库使用不了，很多 Next.js 的最佳实践都得跟着改，并且在未来看起来也不可能支持一些 Next.js 的新特性。

所幸今年年初我发现了 [Opennext](https://opennext.js.org/cloudflare) 这个项目，这个项目是基于 Cloudflare Workers 的，通过 Cloudflare Workers runtime 支持 Node.js APIs，几乎支持所有的 Next.js 特性，并且这个框架后续也由官方支持了，所以我就决定使用这个框架来开发 Cloudflare Workers 模板。

你可以通过购买 [NextDevKit Cloudflare Workers 模板](https://nextdevkit.com/) 来获得两个代码库的权限，包含 Next.js 和 NextDevKit Cloudflare Workers Next.js 模板，并且获得后续的更新和社区支持。

单独拆分成一个代码库的原因是，Cloudflare Workers 模板除了集成 Opennext 之外，我还同时集成了 Cloudflare D1，KV，Durable Objects 等资源，数据库默认使用 D1，缓存默认使用 KV，并且使用 KV 来支持 ISR 等，在构建期间就自动生成缓存放入 KV 中，这些资源都是 Worker Standard Plan 支持的资源，并且 Cloudflare 的资源价格非常便宜，我的目标是让用户可以完美利用这些资源。

大家可以通过下面的 Cloudflare Dashboard 图看到所有的 Worker 的绑定。

![Cloudflare Worker Binding](https://storage.guangzhengli.com/images/cloudflare-worker-bingding.png)

当我我目前还没有大规模使用 KV 来作为系统内部数据缓存，例如用户数据等，因为目前要保持三个代码库的同步，后续有时间可能会进行更深度的优化。

当然你也可以修改代码，集成其它的数据库和缓存库，后续也会在社区分享使用 Opennext 和 Cloudflare Workers 的开发经验。

需要特别注意的是，因为 Cloudflare Worker 的免费版本限制 3MB 的代码打包，所以如果你要使用 Workers 版本的模板，必须购买 Cloudflare Workers 每月 5 刀的 Standard 版本，从而将限制提高到 10MB，目前模板在集成所有功能后打包的大小大概是 3MB - 3.5 MB 之间，对于 Standard 版本来说，只要不是超大型项目，应该是游刃有余的。并且 Standard 版本还支持 D1, KV 等额度，可以放心大胆的使用。

## AWS 模板

对于企业级的项目开发来讲，NextDevKit AWS 模板支持通过 [SST](https://sst.dev/) 管理 AWS 的 Infra 资源，并且支持 Serverless 和 ECS 容器两种部署方式。

其实 AWS 在国内是被开发者忽视的一个选项，如果你申请了国外的公司准备开启你的创业之旅，例如申请的是 Stripe Atlas 公司，你可以直接申请到 `$5000` 的云服务额度，如果你是直接申请 AWS 创业扶持，最高可以申请到 `$100000` 的云服务额度。可以直接覆盖你的一年内的云服务费用。而且 AWS 的云服务是最全面的，只要你有需求，AWS 都能满足你。

并且有一些项目因为隐私和地区合规性要求，是要求托管在 AWS 这种大公司的云上的，所以这个模板针对 AWS 也是原生支持，完全利用 AWS 的资源，例如 RDS，S3，Lambda，CloudFront，CloudWatch 等，数据库使用 RDS 和 Proxy 等，外部访问数据库需要通过 EC2 SSH 连接和白名单 IP 等，在安全和隐私性上更加有保障。

除此外，通过 SST 这个项目，不需要从头搭建自己的 Infra as Code，SST 基于的是 Pulumi 的框架，一行命令做到从创建资源，到部署，到更新，到删除，完全自动化，并且 SST 的社区非常活跃，有大量的资源和教程可以参考。

其实在选型时候考虑是否使用 AWS 官方自己的 Amplify 框架来部署 Next.js 项目，但是在我花费了大量的时间去研究 Amplify 的文档和社区后，并且亲自部署了一个生产项目后，发现 Amplify 在生产环境几乎处于不可用的状态，后面有时间我会单独的分享 AWS 的一些知识。

## 关于 AI 功能

目前 NextDevKit 的 AI 功能是以前端 AI 组件的形式在代码中，暂时没有集成 Vercel AI SDK 和 LLM 的 API，因为关于 AI 的功能每个人都需要的点不一样，如果都集成的话，又略显臃肿，暂时没有想到一种好的方式来集成这些功能，所以暂时以前端组件的形式在代码中。

后续会花一些时间来研究是否可以通过 Prompt 或者 RAG，亦或者是 MCP 的方式来集成 AI 功能，当然后续是不会进行二次收费的。可能以非代码的方式进行支持。所以你购买后得到的不仅仅是代码，可能还有后续的服务支持，且在 Discord 社区会分享一些开发的思路和方法。

## 写在最后

如果你有我类似的痛点，或者是想通过 Next.js 来开发 SaaS 服务，亦或者是来构建一个全栈项目，那么这个模板绝对能帮助你省下一两个月的时间，个人在代码调优和配置上花费了大量的时间，可以通过简单的配置就完成项目的初始化。并且通过 AI 和 Cursor 的后续辅助，绝对的大大加快你的想法到项目落地的速度。

目前大家可以通过 [NextDevKit](https://nextdevkit.com/) 官网通过 Stripe 渠道购买，目前的定价是调研了一圈同类产品得出的定价策略，如果是国内的 IP 会自动跳转到 CNY 通过支付宝支付，也可以通过信用卡支付。国外 IP 会自动跳转到 USD 通过信用卡支付。

> 08/28 更新：除了文档更新完毕，目前模版教程也已经写的差不多了，大家可以到 [NextDevKit 教程](https://nextdevkit.com/zh/tutorials) 查看完整的教程，可以跟着教程快速上手 Next.js 和 NextDevKit 模版。