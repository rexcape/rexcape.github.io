---
title: Rsbuild 添加 MDX 支持
date: 2024-11-01 11:20:59
tags:
  - rsbuild
  - mdx
categories:
  - 实用
---

让 Rsbuild 支持导入 .mdx/.md 文件

<!--more-->

## 基础支持

使用 `npm add @rsbuild/plugin-mdx -D` 命令安装 rsbuild 的 mdx 插件，修改 `rsbuild.config.ts` 配置

```typescript
import { defineConfig } from "@rsbuild/core";
import { pluginMdx } from "@rsbuild/plugin-mdx";

export default defineConfig({
  // ...
  plugins: [pluginMdx()],
});
```

## GFM 支持

GitHub Flavored Markdown 是 GitHub 推出的 Markdown 扩展，里面有对表格等等的扩展支持（基础里不支持表格等部分特性）。添加 GFM 支持的方法：使用 `npm add remark-gfm` 安装 remark 的 GFM 扩展，修改 `rsbuild.config.ts` 配置

```typescript
import { defineConfig } from "@rsbuild/core";
import { pluginMdx } from "@rsbuild/plugin-mdx";
import remarkGfm from "remark-gfm";

export default defineConfig({
  // ...
  plugins: [
    pluginMdx({
      mdxLoaderOptions: {
        remarkPlugins: [remarkGfm],
      },
    }),
  ],
});
```

## 相关文章

- [rspack-contrib/rsbuild-plugin-mdx](https://github.com/rspack-contrib/rsbuild-plugin-mdx)
- [GitHub flavored markdown (GFM)](https://mdxjs.com/guides/gfm/#github-flavored-markdown-gfm)
