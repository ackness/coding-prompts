### **Part 1: Foundation (Basic Agreement)**

**1.1. Core Principles**
- **Language Mode**: All code, documentation, and comments must be in pure English. All explanations, discussions, and clarifications during our interaction will be in Chinese.
- **Goal**: The primary goal is to generate clean, efficient, maintainable, and well-documented code that adheres to the specifications provided and follows Go best practices.

**1.2. MCP Tools Usage**
You are expected to use the following tools to ensure code quality and accuracy:
- `pacakge-version`: Before importing any third-party library, use this tool to query its latest stable version.
- `context7` & `mcp-deepwiki`: When dealing with third-party libraries, use these tools to consult the latest documentation to ensure correct implementation and usage of APIs.
- `sequential-thinking`: For complex problems or logic, use this tool to break down the problem into smaller, manageable steps before writing code.
- `ddg-search`: If you encounter ambiguous requirements or concepts, use this tool to search the web for clarification to prevent hallucinations.
- `git`: Use this tool for version control operations as instructed.
- `fetch`: Use this tool for web page scraping.

**1.3. Development Workflow**
Follow this general development process:
1.  **Understand & Clarify**: Analyze the requirements. If anything is unclear, ask for clarification.
2.  **Plan & Design**: Use `sequential-thinking` for complex tasks. Outline the structure, define interfaces, and plan the data flow.
3.  **Code**: Write the code according to the plan, adhering to all specified agreements.
4.  **Test**: Provide test cases as specified in the "Supplementary Conditions".
5.  **Document**: Write clear comments and documentation for the generated code.

---

### **Part 2: Language (Modern Go Features)**

**2.1. Version**
- **Go Version**: `1.24.4`

**2.2. Modern Idiomatic Go (1.21+)**
Your code should be written in an idiomatic, modern Go style, combining the key features introduced since version 1.21 for improved clarity, safety, and power.

**Key Features to Utilize:**

*   **Enhanced `net/http.ServeMux` (High Priority)**:
    *   For all HTTP services, use the modern `http.ServeMux`. Define routes with HTTP methods and path wildcards (e.g., `"GET /items/{id}"`) for more robust and RESTful routing directly within the standard library.
*   **Safer and Simpler Loops**:
    *   The `for` loop variable capture issue is resolved by default (Go 1.22+). You can safely use goroutines inside loops without needing to create a shadow variable.
    *   When iterating a fixed number of times, prefer the concise `for i := range N` syntax.
*   **New Built-in Functions**:
    *   Use the built-in `min()` and `max()` for comparing ordered types and `clear()` for resetting slices and maps without reallocating memory.
*   **Function Iterators (`range` over func)**:
    *   For custom iteration logic, such as streaming data or generating sequences, implement a function iterator that can be used directly in a `for-range` loop.
*   **Performance Awareness**:
    *   Be aware that Go 1.24+ benefits from significant runtime performance improvements (e.g., faster map implementation) that require no code changes.

---

### **Part 3: Framework (e.g., Go-zero)**

- **Primary Framework**: We will use `go-zero`.
- **Version**: Use the `pacakge-version` tool to find and use the latest stable version of `github.com/zeromicro/go-zero`.
- **Style**: Follow standard `go-zero` project structure and best practices. Use `goctl` for boilerplate generation where appropriate.

---

### **Part 4: Task (Specific Requirements)**

- **[Please provide your detailed requirements here. For example:]**
- **Example Task**:
    - "I need a simple API service using Go-zero."
    - "It should have one endpoint: `POST /api/user/create`."
    - "The request body should have `name` (string) and `email` (string)."
    - "The handler should validate that `name` and `email` are not empty."
    - "If valid, return a `user_id` (a generated UUID) and a success message."
    - "If invalid, return an appropriate error."

---

### **Part 5: Constraints (Supplementary Conditions)**

- **Testing**:
    - All logic handlers must have corresponding unit tests.
    - Use the standard `testing` package.
    - For assertions, use the `testify/assert` library (`github.com/stretchr/testify`). Please use `pacakge-version` to get its latest version.
- **Operating System**: The target environment is `Linux/amd64`. Ensure code is compatible.
- **Error Handling**: Use `go-zero`'s error handling mechanisms (`xerror`). All errors returned to the client should be in a structured format.
- **Dependencies**: Minimize external dependencies. For any new dependency, justify its necessity.
