<p align="center">
  <a href="../README.md">仓库首页</a> · <a href="../en/README.md">English</a> · <strong>简体中文</strong>
</p>

# 把这份指南交给 AI Agent，避开那些会造成数小时返工的 UI 设计错误

*Vibe Coding 进行得很快，UI 错误叠加得更快。*

在 AI Agent 设计、实现或修复界面之前，直接把这份指南交给它。Agent 可以在当前任务中读取并应用其中的防错经验，处理布局、交互状态、源码修改、视觉资产和完整验证。

它不是应用程序，也不是固定的设计模板，而是一份可以直接投入开发任务的工作指南。内容来自真实 UI 迭代中反复发生的问题：用新图层遮盖旧样式、误解交互行为、CSS 相互冲突、前端状态没有更新、滚动和定位失效，以及把局部检查误当成完整验证。

> **一步使用：**开始 AI 编码任务时，把 [`GUIDE.md`](GUIDE.md) 附上一次，并告诉 Agent：“请先阅读这份指南，在本次 UI 工作中采用相关防错规则，但不要限制视觉探索。”

**[阅读中文完整指南](GUIDE.md)** · **[Read in English](../en/README.md)**

**[一键下载简体中文包（.zip）](https://github.com/cherliangvisual/human-ai-ui-collaboration-guide/releases/download/v1.0.0/%E4%BA%BA%E6%9C%BA%E5%8D%8F%E4%BD%9CUI%E8%AE%BE%E8%AE%A1%E4%B8%8E%E5%BC%80%E5%8F%91%E7%BB%8F%E9%AA%8C%E9%81%BF%E9%9B%B7%E6%8C%87%E5%8D%97-v1.0.0-zh-CN.zip)** · [Download the English package](https://github.com/cherliangvisual/human-ai-ui-collaboration-guide/releases/download/v1.0.0/Human-AI-UI-Collaboration-Guide-v1.0.0-EN.zip)

## 一个任务窗口，只需交一次

| 当前情况 | 应该怎样做 |
|---|---|
| 开始新的任务或聊天 | 把 `GUIDE.md` 与产品目标或当前 UI 材料一起附上一次。 |
| 继续使用同一个任务窗口 | 正常继续开发，不需要重复上传指南。 |
| 后续修改开始偏离意图 | 提醒 Agent 继续遵循指南，或指出相关章节。 |
| 打开独立的新任务或新聊天 | 再次附上指南；如果项目共享 Sources 或工作区说明已经提供该文件，则无需重复上传。 |

## 它主要帮助避免什么

- 用新色块、伪元素或重复图层掩盖旧设计。
- 修复一个局部问题时，意外改动已经确认的界面部分。
- 把交互或状态问题误判为单纯的 CSS 问题。
- 空状态、加载、成功、失败、刷新和重启恢复彼此不一致。
- 只打开独立组件或结果页，就声称整个产品已经验证完成。
- 没有确定结构性根因，便反复进行主观视觉微调。
- 把已废弃的实验稿和视觉资产一起带入正式版本。

## 仓库结构

```text
human-ai-ui-collaboration-guide/
├── README.md                       双语仓库总入口
├── en/
│   ├── README.md                   英文使用说明
│   ├── GUIDE.md                    英文指南与提示词
│   ├── CHANGELOG.md                英文版本记录
│   └── COPYRIGHT-AND-PERMISSIONS.md
└── zh-CN/
    ├── README.md                   中文使用说明
    ├── GUIDE.md                    中文指南与提示词
    ├── CHANGELOG.md                中文版本记录
    └── COPYRIGHT-AND-PERMISSIONS.md
```

## 两个下载包里分别有什么

英文包：

```text
Human-AI-UI-Collaboration-Guide-v1.0.0-EN/
├── README.md                       英文使用入口
├── GUIDE.md                        英文完整指南与可复制提示词
├── CHANGELOG.md                    英文版本记录
└── COPYRIGHT-AND-PERMISSIONS.md    英文版权与使用权限
```

简体中文包：

```text
人机协作UI设计与开发经验避雷指南-v1.0.0-zh-CN/
├── README.md                       中文使用入口
├── GUIDE.md                        中文完整指南与可复制提示词
├── CHANGELOG.md                    中文版本记录
└── COPYRIGHT-AND-PERMISSIONS.md    中文版权与使用权限
```

两个语言包相互独立。英文使用者不需要在中文文件中寻找入口，中文使用者也不需要进入英文优先的压缩包。

## 选择阅读路径

| 任务 | 先读 | 继续阅读 |
|---|---|---|
| 从 0 到 1 的全新设计 | 第 1–5 节 | 第 18–19 节，以及第 23 节中适用的部分 |
| 现有产品大改版 | 第 2.2、5、8–10 节 | 第 17–20 节 |
| 局部 UI 修复 | 第 2.3、6–16 节 | 第 19–20 节与第 23 节中对应的高风险模块 |
| 准备提示词 | 第 21–22 节 | 只补充当前任务需要的防错条件 |

## 在线阅读

- [简体中文版](GUIDE.md)
- [English edition](../en/GUIDE.md)

## 下载 1.0.0 版

| 版本 | 独立出版包 |
|---|---|
| 简体中文 | [下载简体中文 ZIP](https://github.com/cherliangvisual/human-ai-ui-collaboration-guide/releases/download/v1.0.0/%E4%BA%BA%E6%9C%BA%E5%8D%8F%E4%BD%9CUI%E8%AE%BE%E8%AE%A1%E4%B8%8E%E5%BC%80%E5%8F%91%E7%BB%8F%E9%AA%8C%E9%81%BF%E9%9B%B7%E6%8C%87%E5%8D%97-v1.0.0-zh-CN.zip) |
| English | [下载英文 ZIP](https://github.com/cherliangvisual/human-ai-ui-collaboration-guide/releases/download/v1.0.0/Human-AI-UI-Collaboration-Guide-v1.0.0-EN.zip) |

## 推荐使用流程

1. 在开始 UI 工作前附上指南。
2. 提供产品目标或当前界面，以及本次修改的边界。
3. 让 Agent 只采用与当前任务有关的防错规则。
4. 重大视觉决策先看草稿，再允许 Agent 修改正式代码。
5. 完成前验证完整用户链路，而不是只检查局部页面。

## 出版信息

- 版本：1.0.0
- 发布日期：2026 年 9 月 26 日
- 作者：**梁卓滢（Cher Liang）**
- GitHub：[@cherliangvisual](https://github.com/cherliangvisual/)
- 变更记录：[CHANGELOG.md](CHANGELOG.md)

## 版权与使用权限

版权所有 © 2026 梁卓滢（Cher Liang）。保留所有权利。

本出版物可供阅读和个人非商业参考，也可以作为私密任务上下文交给您自行使用的 AI 助手，辅助您自己的项目。读者与 AI 均不得公开上传、传播、转载、翻译、改写本指南，或发布可替代本指南的版本。本出版物未采用开源、开放内容或 Creative Commons 许可证。

请阅读完整的[版权与使用权限说明](COPYRIGHT-AND-PERMISSIONS.md)。
