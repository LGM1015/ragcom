# RAG Agent

企业级 Agentic RAG 平台，基于 Spring Boot 与 React 构建，覆盖从文档解析、智能分块、多路检索到流式问答的完整链路。

## 核心特性

- **多路检索引擎**：多通道并行检索 + 后处理流水线，支持向量检索与关键词混合策略，通过 RRF 算法融合多路结果
- **意图识别体系**：树形多级分类，置信度不足时主动引导澄清
- **模型路由容错**：多候选路由 + 首包探测 + 自动降级，模型故障用户无感知
- **MCP 协议集成**：检索与业务工具无缝融合，支持扩展工具生态
- **会话记忆管理**：滑动窗口 + 自动摘要压缩，避免多轮对话 Token 爆炸

## 技术栈

| 分层 | 技术选型 |
|------|----------|
| 后端 | Java 17, Spring Boot 3.5, Spring AI, MyBatis-Plus |
| 数据库 | PostgreSQL + pgvector, Milvus 向量数据库 |
| 缓存/队列 | Redis, RocketMQ |
| 认证 | Sa-Token |
| 前端 | React 18, TypeScript, Vite, TailwindCSS, Radix UI |
| 协议 | MCP (Model Context Protocol), SSE |

## 架构设计

```
bootstrap/     # 业务逻辑层
framework/      # 基础设施层（异常、幂等、线程池、追踪）
infra-ai/       # AI 模型集成层（ChatClient、Embedding、Rerank）
mcp-server/     # MCP 协议服务层
```

各层职责清晰，换模型供应商不改业务代码，换业务逻辑不动基础设施。

## 快速启动

```bash
# 后端编译
./mvnw compile

# 前端启动
cd frontend && npm install && npm run dev
```

详细启动文档：https://ragcom.com/ragcom/local-dev/

## 鸣谢

本项目基于 [Ragcom](https://github.com/ragcom/ragcom) 开源项目改编，感谢原作者的开源贡献。

## 项目规模

- 后端 Java 代码：约 4 万行，400+ 源文件
- 前端 TypeScript/React：约 1.8 万行
- 数据库：20 张业务表
- 前后端页面：22 个页面与组件

## License

Apache-2.0