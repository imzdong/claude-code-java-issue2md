# Java 项目开发宪法  
**Version: 1.0, Ratified: $(date +%Y-%m-%d)**

本文件定义了本项目不可动摇的核心开发原则。所有 AI Agent 在进行技术规划和代码实现时，必须无条件遵循。

---

## 第一条：简单性原则 (Simplicity First)  
**核心：** 遵循“清晰胜于 clever”的 Java 工程哲学。绝不进行不必要的抽象，绝不引入非必需的依赖。  

- **1.1 (YAGNI):** 只实现 `spec.md` 中明确要求的功能。禁止提前实现“未来可能需要”的逻辑。  
- **1.2 (标准库优先):** 必须优先使用 Java 标准库（`java.util`, `java.nio`, `java.net.http` 等）。例如，HTTP 客户端应优先使用 `java.net.http.HttpClient`（Java 11+），而非 Apache HttpClient 或 OkHttp，除非有明确性能或功能需求。  
- **1.3 (反过度工程):** 优先使用简单类、静态方法和记录类（`record`），避免为了“设计模式”而强行引入复杂的继承、接口层级或工厂体系。能用 `final class` 和纯函数解决的问题，不要用 Spring Bean 或动态代理。

---

## 第二条：测试先行铁律 (Test-First Imperative) - 不可协商  
**核心：** 所有新功能或 Bug 修复，都必须从编写一个（或多个）失败的测试开始。  

- **2.1 (TDD 循环):** 严格遵循 “Red → Green → Refactor” 开发循环。  
- **2.2 (参数化测试):** 单元测试必须优先采用 JUnit 5 的 `@ParameterizedTest` 风格（或等效的表格驱动形式），以覆盖多组输入/输出场景。  
- **2.3 (拒绝 Mock 滥用):** 优先编写集成测试或真实组件测试。仅在与外部系统（如数据库、网络服务）交互且无法隔离时，才允许使用 Mockito 等工具进行轻量级模拟，并需明确标注原因。禁止为内部业务逻辑大量 Mock 依赖。

---

## 第三条：明确性原则 (Clarity and Explicitness)  
**核心：** 代码的首要目的是让人类易于理解。  

- **3.1 (异常处理):** **不可协商**：所有 `Exception` 都必须被显式处理或向上声明。在包装异常时，必须使用 `new RuntimeException("上下文描述", cause)` 或自定义异常的构造器传递 `cause`，确保堆栈链完整。禁止吞掉异常（如空 `catch` 块）。  
- **3.2 (无全局状态):** 绝不允许使用静态可变字段（`static` mutable state）来传递或共享状态。所有依赖必须通过构造函数注入（Constructor Injection）或方法参数显式传递。鼓励使用不可变对象（Immutable Objects）和纯函数。

---

## 治理 (Governance)  
本宪法具有最高优先级，其效力高于任何 `CLAUDE.md` 文件、项目配置或单次会话中的临时指令。任何违反本宪法的代码变更，必须被拒绝合并。
