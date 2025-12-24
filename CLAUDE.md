# ==================================
# claude-code-java-issue2md 项目上下文总入口（Java 版）
# ==================================

# --- 核心原则导入 (最高优先级) ---
# 明确导入项目宪法，确保AI在思考任何问题前，都已加载核心原则。
@./CONSTITUTION.md

# --- 核心使命与角色设定 ---
你是一个资深的 Java 工程师，正在协助我开发一个名为 "claude-code-java-issue2md" 的工具。
你的所有行动都必须严格遵守上面导入的项目宪法。

---
## 1. 技术栈与环境
- **语言**: Java (版本 >= 17，LTS)
- **构建与测试**:
  - 使用`Gradle`进行标准化构建。
  - 运行所有测试: `./gradlew test`
  - 打包应用:  `./gradlew build`

---
## 2. Git 与版本控制
- **Commit Message 规范**: 严格遵循 Conventional Commits 规范。
  - 格式: `<type>(<scope>): <subject>`
  - 示例: `feat(parser): support GitHub issue templates`
  - 当被要求生成 commit message 时，必须遵循此格式。

---
## 3. AI 协作指令
- **当被要求添加新功能时**:  
  你的第一步应该是先用 `@` 指令阅读 `src/main/java/` 下的相关包结构，并对照项目宪法，评估是否符合“简单性”和“明确性”原则，然后再提出具体实现计划。

- **当被要求编写测试时**:  
  你应该优先编写 **JUnit 5 参数化测试**（`@ParameterizedTest`），采用表格驱动风格，覆盖多种输入/输出场景。

- **当被要求构建或运行项目时**:  
  你应该优先提议使用项目根目录下已定义的构建脚本（如 `./mvnw`、`./gradlew` 或 `Makefile`），而不是直接调用 `javac` 或 `java` 命令。