### **Part 1: Foundation**

**1.1. Language Usage**

* **Code, comments, documentation**: English
* **Interaction (explanations, Q&A)**: Chinese

**1.2. Objectives**

* Produce clean, maintainable, high‑performance Go code
* Follow modern Go best practices (targeting Go 1.20+)

**1.3. Tooling Rules**

* `package-version`: fetch latest stable version for dependencies
* `context7` / `mcp-deepwiki`: consult docs for correct API usage
* `sequential-thinking`: decompose complex tasks into logical steps
* `ddg-search`: resolve ambiguous requirements
* `git`: perform version control as directed
* `fetch`: scrape web pages when needed

**1.4. Workflow**
Follow these steps in order:

1. Understand and clarify requirements
2. Design structure, interfaces, and data flows
3. Implement code
4. Write unit tests and verify
5. Document clearly

---

### **Part 2: Language Specification**

* **Default Go version**: 1.24.4
  Provide the model with key Go 1.20+ features as prior knowledge:
* **Generics**: type parameters on functions and types; generic type aliases
* **Slice→Array Conversion**: direct conversion (`[N]T(s)`) for copy semantics
* **`unsafe` Enhancements**: `SliceData`, `String`, `StringData` for low-level access
* **Built-ins**: `min()`, `max()`, `clear()` for common operations
* **Loop Improvements**: per-iteration variable redeclaration (closure capture fixed); `for i := range N` for integer iteration
* **Function Iterators**: support for `for range func` loops
* **New stdlib Packages**: `log/slog`, `slices`, `maps`, `cmp`

**Performance & Concurrency**:

* Prioritize low-latency, high-throughput patterns; minimize allocations and GC pressure
* Utilize goroutines and channels appropriately; manage lifecycles with `context.Context` and `sync.WaitGroup`
* Apply sync primitives (`sync.Mutex`, `sync.RWMutex`, `atomic`) to prevent race conditions
* Leverage resource pools (`sync.Pool`) and efficient data structures for high load
* Proactively identify potential deadlocks, memory leaks, and propose mitigation (timeouts, cancellations)

---

### **Part 3: Architecture & Design Patterns**

* **Modular Design**: Organize code into clear modules/packages with single responsibility
* **Layered Architecture**: Separate transport (HTTP/RPC) layer, business logic layer, and data access layer
* **Interface-Driven Development**: Define interfaces for external dependencies and inject implementations for flexibility and testability
* **Error Handling Strategy**: Standardize error types and formats; centralize error translation and logging
* **Configuration Management**: Load configuration from environment, files, or remote sources; validate on startup
* **Observability**: Include structured logging, metrics, and tracing hooks at key boundaries

---

### **Part 4: Implementation Guidelines**

* **HTTP Clients**: Use a robust HTTP client library (e.g., Resty or `net/http`) with timeout, retry, and backoff policies
* **Data Mapping**: Translate external API payloads into internal domain types; use converters or adapters
* **Concurrency Control**: Launch goroutines for independent calls; coordinate with `context.Context` and cancellation
* **Resource Management**: Manage connection pools, rate limits, and circuit breakers to ensure resilience
* **Testing Strategy**: Mock external services via interfaces; write unit tests for logic and integration tests for end-to-end flows
* **Documentation**: Provide README examples showing usage patterns and configuration defaults

---

### **Part 4: Implementation Guidelines**

* **HTTP Clients**: Use Resty v3 (`resty.dev/v3`) with timeout, retry, backoff, middleware, and automatic unmarshalling
* **Data Mapping**: Translate API payloads into domain types via converters/adapters
* **Concurrency Control**: Use goroutines with `context.Context` and cancellation
* **Resource Management**: Leverage connection pools, rate limits, circuit breakers
* **Testing Strategy**: Mock services using interfaces; unit and integration tests
* **Documentation**: README examples with usage patterns and defaults

---

### **Part 5: Frameworks & Libraries**

* **go-zero** (latest version via `package-version`): a cloud-native microservices framework offering code generation (`goctl`), built-in service discovery, load balancing, circuit breaking, validation, caching, and observability features
* **Resty v3** (`resty.dev/v3`): a simple, chainable HTTP and REST client with JSON/XML auto-unmarshalling, retries, middleware hooks, debugging, and SSE support

---

### **Part 6: Task Requirements**

* Build HTTP clients with Resty v3 to call multiple APIs
* Map responses into custom types within go-zero

---

### **Part 7: Additional Constraints**

* **Testing**: each handler must have unit tests using Go’s `testing` + `testify/assert` (latest via `package-version`)
* **Environment**: default Windows (amd64); backup macOS (arm64/amd64) and Linux (amd64)
* **Dependencies**: minimize; justify additions succinctly
