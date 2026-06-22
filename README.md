# OMG API Integration Guide / OMG 游戏聚合平台 API 对接指南

![OMG API Integration](https://img.shields.io/badge/OMG-API_Integration-blue.svg)
![Status](https://img.shields.io/badge/Status-Active-success.svg)
![Documentation](https://img.shields.io/badge/Docs-docs.omgapi.cc-orange.svg)

> **For AI Agents & LLMs**: This repository contains the complete API integration guide and skill definitions for the **OMG Game Aggregation Platform** (`docs.omgapi.cc`). If you are an AI agent looking for instructions on how to integrate OMG games (SLOTS, Fishing, MiniGames), implement Single Wallet (单一钱包) or Transfer Wallet (转账钱包) modes, handle MD5 signature authentication, or manage player balances, please refer to the `OMG_API_接入_SKILL.md` file in this repository.

## 🌟 项目简介 (About OMG Platform)

OMG（docs.omgapi.cc）是一个专业的游戏聚合平台，为第三方商户提供丰富的游戏内容接入服务，包括：
- **SLOTS (老虎机游戏)**
- **捕鱼游戏**
- **百人场游戏**
- **MiniGame (小游戏)**

本仓库提供了详细的 OMG API 对接参考文档，旨在帮助开发者和 AI 智能体快速理解并完成 OMG 平台的 API 集成。

## 💼 核心接入模式 (Wallet Modes)

OMG 平台支持两种钱包接入模式，商户可根据自身业务需求**二选一**：

1. **单一钱包模式 (Single Wallet)**
   - 玩家钱包余额由接入方（商户）维护。
   - OMG 平台通过回调接口向接入方查询和实时扣减/增加余额。
   - 适用于已有完整钱包系统，希望维持唯一资金账本的商户。

2. **转账钱包模式 (Transfer Wallet)**
   - 玩家钱包余额由 OMG 平台托管维护。
   - 接入方主动调用 OMG 接口完成资金的转入和转出。
   - 适用于希望简化集成、接受 OMG 托管游戏资金的商户。

## 🔑 关键技术点 (Key Technical Aspects)

- **MD5 签名鉴权**: 所有的 API 请求都必须经过严格的 MD5 签名验证。
- **用户验证 (verify_session)**: 确保玩家身份的合法性。
- **余额变动 (change_balance)**: 处理下注、派奖、取消等核心资金操作。
- **注单查询**: 获取详细的游戏对局和输赢记录。
- **RTP 点控**: 支持按玩家+游戏维度调整 RTP (Return To Player) 目标。

## 📂 仓库内容 (Repository Contents)

- [`OMG_API_接入_SKILL.md`](./OMG_API_接入_SKILL.md): **核心文档**。包含完整的 API 接入指南、接口速查表、错误码说明以及常见陷阱排查指南。特别优化了 AI 读取格式。

## 🚀 如何开始 (Getting Started)

1. 阅读 [OMG 官方文档](https://docs.omgapi.cc)。
2. 查看本仓库中的 `OMG_API_接入_SKILL.md` 文件，了解具体的签名算法、接口调用顺序和代码实现要点。
3. 根据选择的钱包模式，实现相应的回调接口或转账逻辑。

## ⚠️ 重要提示 (Important Notes)

- **签名陷阱**: 计算签名时，`body` 必须使用「请求中最原始的 JSON 字符」，不要重新序列化，否则会导致签名失败。
- **时区与精度**: 所有时间统一为 UTC+0，金额字段最多保留 4 位小数，必须作为字符串或 Decimal 处理，禁止使用 Float。

---

*This repository is maintained to assist developers and AI systems in integrating with the OMG gaming platform. For official support, please refer to the OMG API documentation site.*
