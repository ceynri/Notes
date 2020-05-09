---
title: Git commit 规范
date: 2020-05-08
---

# Git commit 规范

## 前言

观察别人的项目，有时候会发现好的项目的commit记录都遵循着`<header>: <subject>`的规则。

好处显而易见：`header`能够第一时间了解到该commit的性质，`subject`则是对该commit的简短描述。

保持该规范对commit的整洁性有着很大的帮助😄

## 规范

不过在具体的规范中，我们到底要不要对`header`的种类进行限制呢？首字母到底要不要大写呢？

其实在这方面，早就有人做好了 Git Commit 的自动化代码提交规范工具，比较常见的是 [Commitlint](https://www.npmjs.com/package/@commitlint/config-conventional)，它提出了一些简单的规范：

- feat：新功能（feature）
- fix：修补bug
- docs：文档（documentation）
- style：格式方面的优化
- refactor：重构
- test：测试
- chore：构建过程或辅助工具等无关紧要的变动

如果 commit 的 header 不存在于以上的 type 中，则该 commit 会被拦截下来提交失败。

当然了，如果觉得这些 type 不够，或者想增加更多的规则，也可以修改其配置文件。

比如加个 publish、breaking 等，也不是不行，但最好能在一开始约定好，频繁地变动会导致规范变得没有意义。

## 后记

如果是个人项目，我觉得自己私底下定一下规则就好了，比如我们可以在每个 header 前加上 emoji 表情，甚至用 emoji 代替 header 我觉得都是不错的方案。

只要达到了规范的目的，项目就会变得更加整洁。

上面的规范都是针对有代码的项目的，这里我自己简单地定一个面向文档笔记项目的 commit 规范，供大家参考：

- new：新文章
- feat：旧文档增加新内容
- fix：错误内容的修正
- typo：拼写错误
- modify：部分内容修改
- move：文件结构的变动
- rename：文件名更改所引起的相关变动
- remove：删除文件
- chore：其他无关紧要的变动

毕竟是个人项目，适合自己，看起来舒服就好啦。