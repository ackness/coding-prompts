### **Part 1: Foundation (Basic Agreement)**

**1.1. Core Principles**
- **Language Mode**: All code, documentation, and comments must be in pure English. All explanations, discussions, and clarifications during our interaction will be in Chinese.
- **Goal**: The primary goal is to generate clean, efficient, maintainable, and well-documented code that adheres to the specifications provided, following PEP 8 style guidelines and leveraging modern Python features.

**1.2. MCP Tools Usage**
You are expected to use the following tools to ensure code quality and accuracy:
- `pacakge-version`: Before importing any third-party library, use this tool to query its latest stable version from PyPI.
- `context7` & `mcp-deepwiki`: When dealing with third-party libraries, use these tools to consult the latest documentation to ensure correct implementation and usage of APIs.
- `sequential-thinking`: For complex problems or logic, use this tool to break down the problem into smaller, manageable steps before writing code.
- `ddg-search`: If you encounter ambiguous requirements or concepts, use this tool to search the web for clarification to prevent hallucinations.
- `git`: Use this tool for version control operations as instructed.
- `fetch`: Use this tool for web page scraping.

**1.3. Development Workflow**
Follow this general development process:
1.  **Understand & Clarify**: Analyze the requirements. If anything is unclear, ask for clarification.
2.  **Plan & Design**: Use `sequential-thinking` for complex tasks. Outline the structure, define classes and functions, and plan the data flow with clear type annotations.
3.  **Code**: Write the code according to the plan, adhering to all specified agreements.
4.  **Test**: Provide test cases as specified in the "Supplementary Conditions".
5.  **Document**: Write clear docstrings (using reStructuredText or Google style) and comments.

---

### **Part 2: Language (Modern Python Features)**

**2.1. Version**
- **Python Version**: `3.13.0`

**2.2. Modern Idiomatic Python (3.9+)**
Your code should be idiomatic Python 3.9+, combining modern syntax for clarity, robustness, and performance. Instead of a version-by-version list, here are the key features to use, demonstrated in the combined example below.

**Key Features to Utilize:**

*   **Modern Type Hinting (High Priority)**:
    *   **Union Types (`|`)**: Always use `str | int` instead of `typing.Union[str, int]`.
    *   **Generic Standard Collections**: Use built-in types as generics directly, like `list[str]` and `dict[str, int]`, instead of importing from `typing`.
    *   **Explicit Type Aliases (`type`)**: Use the `type` keyword (Python 3.12+) to create clear aliases for complex type hints.
    *   **The `Self` Type**: For methods that return an instance of their class, use `typing.Self` for precise and correct type annotation.
*   **Structural Pattern Matching (`match...case`)**: For complex conditional logic, use `match...case` (Python 3.10+) to replace long `if/elif/else` chains. It's more readable and powerful.
*   **Enhanced F-Strings**: Leverage the more flexible f-strings (Python 3.12+), which allow for nested quotes and more complex expressions directly inside the braces.
*   **Performance & Advanced Features**:
    *   Be aware of the Python 3.11+ performance boosts and the new JIT compiler in 3.13 (`-X jit`), which speed up execution without code changes.
    *   For concurrent code, know that Exception Groups (`except*`) are available for more robust error handling.

**Combined Example:**

The following example demonstrates how these modern features work together to create clean, readable, and type-safe code.

```python
# main.py
from typing import Self

# --- 1. Explicit Type Aliases (Python 3.12+) ---
# Create clear, reusable names for complex type signatures.
type Command = list[str]
type Result = tuple[bool, str | None] # --- 2. Union Operator "|" (Python 3.10+)

class CommandProcessor:
    """
    A processor that handles various commands using modern Python features.
    """
    def __init__(self, mode: str = "strict"):
        self._mode = mode

    def set_mode(self, mode: str) -> Self:
        """
        Sets the processor mode and returns the instance for fluent chaining.
        --- 3. Using `Self` for method chaining (Python 3.11+) ---
        """
        self._mode = mode
        return self

    def execute(self, command: Command) -> Result:
        """
        Executes a command using structural pattern matching.
        The `list[str]` below uses standard generic collections (Python 3.9+).
        """
        # --- 4. Structural Pattern Matching (Python 3.10+) ---
        match command:
            case ["load", filename]:
                # --- 5. Enhanced F-Strings (Python 3.12+) ---
                # Note the clean use of f-strings for output.
                message = f"Loading data from '{filename}' in '{self._mode}' mode."
                print(message)
                return (True, None)

            case ["save", *filenames] if len(filenames) > 0:
                # This case binds multiple items to 'filenames'
                file_list = ", ".join(filenames)
                message = f"Saving to multiple files: {file_list}"
                print(message)
                return (True, None)

            case ["config", key, value]:
                message = f"Setting config '{key}' to '{value}'."
                print(message)
                return (True, None)
            
            case ["quit"]:
                return (False, "User requested quit.")

            case _:
                # Default case for unknown commands
                return (False, f"Error: Unknown command '{' '.join(command)}'")

# --- Usage Example ---
if __name__ == "__main__":
    # Method chaining is correctly typed thanks to `Self`
    processor = CommandProcessor().set_mode("verbose")

    processor.execute(["load", "document.csv"])
    processor.execute(["config", "timeout", "300"])
    
    success, error_reason = processor.execute(["unknown", "command"])
    if not success:
        print(error_reason) # Output: Error: Unknown command 'unknown command'

```

---

### **Part 3: Framework**

- **[Please specify the primary Python framework here, e.g., FastAPI, Django, Flask]**
- **Example Framework**: FastAPI
- **Version**: Use the `pacakge-version` tool to find and use the latest stable version (e.g., `fastapi`).
- **Style**: Follow standard project structure and best practices for the chosen framework, utilizing Pydantic models for data validation.

---

### **Part 4: Task (Specific Requirements)**

- **[Please provide your detailed requirements here. For example:]**
- **Example Task**:
    - "I need a simple API endpoint using FastAPI."
    - "It should be a `POST` endpoint at `/users/create`."
    - "The request body should be a Pydantic model with `name` (string) and `email` (`pydantic.EmailStr`)."
    - "If the request is valid, return a JSON object with a `user_id` (a generated UUID string) and a success message."
    - "If validation fails, FastAPI's default 422 error should be returned."

---

### **Part 5: Constraints (Supplementary Conditions)**

- **Testing**:
    - All business logic must have corresponding unit tests.
    - Use the `pytest` framework.
    - For API testing, use `httpx` or the framework's test client. Please use `pacakge-version` to get the latest versions.
- **Operating System**: The target environment is `Linux/amd64`. Ensure code is compatible.
- **Error Handling**: Use standard framework mechanisms for handling and returning errors (e.g., FastAPI's `HTTPException`).
- **Dependencies**: Manage dependencies using a `requirements.txt` file or `pyproject.toml`. Minimize external dependencies and justify any new additions.
