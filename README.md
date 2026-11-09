# Backend & Security Portfolio
> Personal resume projects. Focusing on **Java Web Development, Business Architecture, and Basic Security Practices**.
> 后端开发方向（校招）个人作品集。注重扎实的业务架构设计，良好的代码规范，并具备基础的安全防御意识。

## 💼 Business Application & Architecture
*核心业务与架构：展现扎实的后端开发基本功与复杂业务处理能力*

### 1. resource-booking-platform
**Resource Scheduling Platform｜企业内部资源预约中台**
Tech Stack: SpringBoot, MyBatis, MySQL, Vue3, Element Plus
- **业务解耦与设计模式**：抽象「资源类型 / 资源实例 / 调度插件」三层模型，运用策略模式实现 `TIME_EXCLUSIVE` 独占校验插件，使新增资源类型无需修改核心逻辑（符合开闭原则）。
- **复杂生命周期管理**：完整实现预约生命周期（提交、审批、取消、失效）；结合定时任务扫描回收超时未审批预约，提高资源利用率。
- **数据库设计与审计**：合理设计业务表与资源抽象层的解耦；使用软删除与审计字段保障数据可追溯。
- **前后端分离**：独立完成后端 RESTful API 设计与 Vue3 前端页面开发。
👉 [View Repo](https://github.com/zhang56589/resource-booking-platform)

### 2. swift-link-service
**Distributed Short Link Service｜分布式短链接跳转服务**
Tech Stack: Java17, SpringBoot3.2, MySQL8, Redis7, MyBatis-Plus
- **高并发标识生成**：使用雪花算法 + Base62 生成短码；利用 MySQL 唯一索引兜底并发场景下的短码全局唯一。
- **缓存与性能优化**：采用 Cache-Aside 缓存方案提升读取性能；针对性实现空值缓存与布隆过滤器（可选），有效防止缓存穿透。
👉 [View Repo](https://github.com/zhang56589/swift-link-service)

### 3. offline-report-service
**Offline Report Task Service｜大数据离线报表任务服务**
Tech Stack: SpringBoot 2.7, EasyExcel, Quartz, Redis, MySQL
- **定时任务调度**：基于 Quartz 实现定时任务，引入 Redis 分布式锁避免集群环境下的任务重复调度。
- **大数据量导出优化**：运用 EasyExcel 流式读写技术，解决大批量数据导出导致的内存溢出（OOM）问题。
- **高可用容错**：实现任务状态持久化，设计失败重试机制与异常捕获，保障后台任务稳定运行。
👉 [View Repo](https://github.com/zhang56589/offline-report-service)

---

## 🧰 Backend Middleware & Components
*进阶组件：展现对框架底层的探索与造轮子能力（加分项）*

### 4. distributed-idempotent-starter
**High-Concurrency Idempotent Starter｜高并发幂等与防重放组件**
Tech Stack: Java 17, Spring Boot 3, Spring AOP, Redis, Redisson, Lua
- **无侵入式设计**：基于 Spring AOP 开发轻量级 Starter，业务方只需添加 `@Idempotent` 注解即可实现接口防重，解耦业务逻辑。
- **多种防重策略**：支持基于 Redis Token 防重、基于 SpEL 参数指纹防重，以及基于 Redisson 的分布式锁防重。
- **底层并发控制**：采用 Redis + Lua 脚本保证操作的原子性，并编写多线程测试用例模拟验证。
👉 [View Repo](https://github.com/zhang56589/distributed-idempotent-starter)

### 5. api-gateway-auth
**Lightweight API Gateway & Unified Auth｜轻量级 API 网关与统一认证授权**
Tech Stack: Java 17, Spring Cloud Gateway, JWT, Redis, MySQL
- **统一入口鉴权**：基于 Spring Cloud Gateway 全局过滤器实现网关级鉴权，拦截伪造请求头，业务服务零侵入接入。
- **Token 管理**：设计 JWT 双 Token 机制，结合 Redis 实现 `jti` 黑名单管理，解决 Token 主动失效问题。
- **接口限流**：利用 Redis + Lua 实现令牌桶算法，提供基础的网关限流能力。
👉 [View Repo](https://github.com/zhang56589/api-gateway-auth)

---

## 🛡️ Security Practices & Legacy Systems
*安全实践与传统底层：展现代码安全底线与框架原理解析*

### 6. vuln-lab
**Web Vulnerability Lab & Defense｜经典 Web 漏洞靶场与防御对照系统**
Tech Stack: Java 17, Spring Boot 3, MyBatis-Plus, H2, JUnit5
- **安全编码习惯**：深入理解 SQLi、XSS、越权、CSRF 等漏洞原理，并在项目中实践参数化查询、Jsoup 过滤等防御方案。
- **自动化验证**：编写 MockMvc 自动化测试用例发送恶意 Payload，验证防御策略的有效性。
👉 [View Repo](https://github.com/zhang56589/vuln-lab)

### 7. game-guide-community
**Game Strategy Sharing Platform｜游戏攻略分享社区 (Legacy SSM)**
Tech Stack: Spring5, SpringMVC5, JdbcTemplate, MySQL8, Druid, JSP
- **框架底层实践**：纯 XML 声明式配置，深入理解 IoC 与 AOP；解决 AOP 自调用导致拦截失效的问题。
- **安全防护机制**：自定义 XSS、CSRF 校验 Filter，实现加盐 MD5 密码方案，搭建内容人工审核流程。
👉 [View Repo](https://github.com/zhang56589/game-guide-community)

### 8. secure-react-agent
**Secure Controllable ReAct Agent｜安全可控 ReAct 智能体**
Tech Stack: Python, pytest
- 从零实现 ReAct 推理主循环，了解大模型工具调用协议；内置文件路径穿越防护。
👉 [View Repo](https://github.com/zhang56589/secure-react-agent)

---

## About Me
Undergraduate student focusing on **Java Backend Development & Business Architecture**. 
If you are interested, welcome to contact me.
