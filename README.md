# Backend & Security Portfolio
> Personal resume projects. Focusing on **Java Backend Architecture, High Concurrency, and Distributed Systems**.
> 后端开发方向个人作品集，具备扎实的分布式架构能力，并将 Web 安全防御深度融入后端开发实践。

## 🚀 Core Backend Infrastructure
*核心基建：高并发、中间件与架构设计（后端面试绝对主力）*

### 1. api-gateway-auth
**Lightweight API Gateway & Unified Auth｜轻量级 API 网关与统一认证授权**
Tech Stack: Java 17, Spring Cloud Gateway, JWT, Redis, MySQL, Docker
- **架构设计**：基于 Spring Cloud Gateway 过滤器链自研轻量 API 网关，实现统一鉴权与安全防护，业务服务零侵入接入。
- **高并发限流**：基于 Redis + Lua 脚本实现令牌桶算法，保证限流原子性；支持按 `userId`、`IP`、`API Path` 三维度联合限流，超限统一返回 429。
- **会话与状态管理**：设计 JWT 双 Token 机制，结合 Redis 实现 `jti` 黑名单动态 TTL 管理，解决无状态 Token 的主动失效难题。
- **工程化实践**：基于 Testcontainers 启动真实 Redis 容器进行集成测试，Docker Compose 一键部署，配置 GitHub Actions CI 自动构建。
👉 [View Repo](https://github.com/zhang56589/api-gateway-auth)

### 2. distributed-idempotent-starter
**High-Concurrency Idempotent Starter｜高并发幂等与防重放组件**
Tech Stack: Java 17, Spring Boot 3, Spring AOP, Redis, Redisson, Lua
- **无侵入组件设计**：基于 AOP 自研轻量级 Starter 组件，业务方仅需添加 `@Idempotent` 注解即可实现接口防重，解耦业务逻辑。
- **多策略适配**：设计策略模式（Strategy Pattern），支持基于 Redis Token 客户端防重、基于 SpEL 参数指纹防重、基于 Redisson 分布式锁防重。
- **底层并发保证**：采用 Redis + Lua 保证“查-删”操作原子性；编写 JUnit5 多线程测试，验证 100 并发下相同参数仅成功执行 1 次。
👉 [View Repo](https://github.com/zhang56589/distributed-idempotent-starter)

### 3. offline-report-service
**Offline Report Task Service｜大数据离线报表任务服务**
Tech Stack: SpringBoot 2.7, EasyExcel, Quartz, Redis, MySQL
- **分布式定时任务**：基于 Quartz 实现分布式定时任务，使用分布式锁避免集群节点重复调度。
- **大数据量调优**：引入 EasyExcel 流式读写解决大批量导出 OOM 问题；Redis 缓存统计中间结果，显著降低数据库压力。
- **高可用设计**：任务状态持久化，支持失败重试机制，完善异常捕获与容错处理。
👉 [View Repo](https://github.com/zhang56589/offline-report-service)

### 4. swift-link-service
**Distributed Short Link Service｜分布式短链接跳转服务**
Tech Stack: Java17, SpringBoot3.2, MySQL8, Redis7, MyBatis-Plus
- **分布式 ID 生成**：基于雪花算法 + Base62 生成短码，利用 MySQL 唯一索引兜底并发场景下的短码全局唯一性。
- **缓存高可用**：采用 Cache-Aside 缓存方案，增加空值缓存防止缓存穿透，保障热点数据读取性能。
👉 [View Repo](https://github.com/zhang56589/swift-link-service)

---

## 💼 Business Architecture & Design
*业务架构：设计模式与企业级复杂业务落地*

### 5. resource-booking-platform
**Resource Scheduling Platform｜企业内部资源预约中台**
Tech Stack: SpringBoot, MyBatis, MySQL, Vue3, Element Plus
- **插件化架构**：设计插件化资源调度模型，抽象「资源类型 / 资源实例 / 调度插件」三层架构，统一承载会议室、工位等资源。
- **开闭原则实践**：实现 `TIME_EXCLUSIVE` 时段独占校验插件，新增同类资源无需修改核心调度逻辑，提升系统横向扩展能力。
- **复杂生命周期**：完整实现预约生命周期（提交、审批、取消、失效）；数据库分层设计，软删除保证审计可追溯。
👉 [View Repo](https://github.com/zhang56589/resource-booking-platform)

---

## 🛡️ Security-Driven Backend (Bonus)
*安全加成：以防御性编程思维构建后端系统（体现你的代码严谨度）*

### 6. vuln-lab
**Web Vulnerability Lab & Defense｜经典 Web 漏洞靶场与防御对照系统**
Tech Stack: Java 17, Spring Boot 3, MyBatis-Plus, H2, JUnit5, MockMvc
- **自动化测试验证**：编写 29 个 JUnit5 + MockMvc 测试用例，发送真实恶意 Payload 验证防御有效性，实现 CI 自动化回归。
- **生产级防御编码**：覆盖 SQLi、XSS、越权、SSRF、CSRF 攻击；实现 Jsoup 过滤、自研双提交 CSRF 验证、防御 DNS 重绑定的 SSRF 拦截器。
- **开箱即用**：内置 H2 内存数据库与 Console，一键启动，降低代码审计与复现成本。
👉 [View Repo](https://github.com/zhang56589/vuln-lab)

### 7. game-guide-community
**Game Strategy Sharing Platform｜游戏攻略分享社区 (Legacy SSM)**
Tech Stack: Spring5, SpringMVC5, JdbcTemplate, MySQL8, Druid, JSP
- **底层原理实践**：纯 XML 声明式配置（零注解），自定义安全 Filter 与 AOP 拦截。
- **AOP 难点攻克**：解决 AOP 自调用导致拦截失效的问题，通过暴露代理对象重构调用链。
- **安全机制**：实现加盐 MD5 密码方案，搭建内容人工审核流程。
👉 [View Repo](https://github.com/zhang56589/game-guide-community)

### 8. secure-react-agent
**Secure Controllable ReAct Agent｜安全可控 ReAct 智能体**
Tech Stack: Python, pytest
- 从零实现 ReAct 推理主循环，自定义工具调用协议，轻量无重型框架依赖。
- 内置路径穿越防护模块，对文件访问能力做权限隔离；基于 pytest 编写单元测试覆盖安全校验。
👉 [View Repo](https://github.com/zhang56589/secure-react-agent)

---

## About Me
Java Backend Developer focusing on **High Concurrency, Distributed Systems, Middleware, and Defensive Programming**. 
If you are interested, welcome to contact me.
