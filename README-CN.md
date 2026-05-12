<a href="https://chatbot.ai-sdk.dev/demo">
  <img alt="Chatbot" src="app/(chat)/opengraph-image.png">
  <h1 align="center">Chatbot</h1>
</a>

<p align="center">
    Chatbot（原 AI Chatbot）是一个基于 Next.js 与 AI SDK 构建的免费开源模板，帮助你快速搭建功能完善的聊天机器人应用。
</p>

<p align="center">
  <a href="https://chatbot.ai-sdk.dev/docs"><strong>阅读文档</strong></a> ·
  <a href="#功能特性"><strong>功能特性</strong></a> ·
  <a href="#模型提供商"><strong>模型提供商</strong></a> ·
  <a href="#自行部署"><strong>自行部署</strong></a> ·
  <a href="#本地运行"><strong>本地运行</strong></a>
</p>
<br/>

## 功能特性

- [Next.js](https://nextjs.org) App Router
  - 高级路由，兼顾导航体验与性能
  - React Server Components（RSC）与 Server Actions，用于服务端渲染并提升性能
- [AI SDK](https://ai-sdk.dev/docs/introduction)
  - 统一 API：生成文本、结构化对象以及 LLM 工具调用
  - 用于构建动态聊天与生成式界面的 Hooks
  - 通过 AI Gateway 支持 OpenAI、Anthropic、Google、xAI 等模型提供商
- [shadcn/ui](https://ui.shadcn.com)
  - 使用 [Tailwind CSS](https://tailwindcss.com) 进行样式设计
  - 基于 [Radix UI](https://radix-ui.com) 的可访问、可组合的组件原语
- 数据持久化
  - [Neon Serverless Postgres](https://vercel.com/marketplace/neon) 保存聊天记录与用户数据
  - [Vercel Blob](https://vercel.com/storage/blob) 高效存储文件
- [Auth.js](https://authjs.dev)
  - 简洁且安全的身份认证

## 模型提供商

本模板使用 [Vercel AI Gateway](https://vercel.com/docs/ai-gateway)，通过统一接口访问多种 AI 模型。模型在 `lib/ai/models.ts` 中配置，并支持按模型路由到不同提供商。内置模型包括：Mistral、Moonshot、DeepSeek、OpenAI 与 xAI。

### AI Gateway 身份验证

**在 Vercel 上部署**：通过 OIDC 令牌自动完成身份验证。

**在非 Vercel 环境部署**：需要在 `.env.local` 中设置环境变量 `AI_GATEWAY_API_KEY`，提供 AI Gateway 的 API 密钥。

借助 [AI SDK](https://ai-sdk.dev/docs/introduction)，你也可以用少量代码切换到直连 LLM 提供商，例如 [OpenAI](https://openai.com)、[Anthropic](https://anthropic.com)、[Cohere](https://cohere.com/) 以及[更多提供商](https://ai-sdk.dev/providers/ai-sdk-providers)。

## 自行部署

你可以一键将 Chatbot 部署到自己的 Vercel 项目：

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/templates/next.js/chatbot)

## 本地运行

运行 Chatbot 需要使用 [`.env.example`](.env.example) 中说明的环境变量。建议使用 [Vercel 环境变量](https://vercel.com/docs/projects/environment-variables) 管理；仅使用本地 `.env` 文件也可以。

> 注意：请勿将 `.env` 提交到版本库，否则会泄露密钥，他人可能借此控制你的 AI 与认证相关账户。

1. 安装 Vercel CLI：`npm i -g vercel`
2. 将本地项目与 Vercel、GitHub 账户关联（会生成 `.vercel` 目录）：`vercel link`
3. 拉取环境变量：`vercel env pull`

```bash
pnpm install
pnpm db:migrate # 初始化数据库或应用最新迁移
pnpm dev
```

完成后，模板应用应在 [localhost:3000](http://localhost:3000) 运行。
