# Technical Profile: Python Applications & Engines

## 1. Environment & Dependency Management
- **Python Version Baseline**: Python >= 3.10 (leveraging modern pattern matching, union type operators `|`, and typed dicts).
- **Environment Isolation**: Always mandate virtual environment isolation (`.venv/`) using tools such as `venv`, `uv`, or `poetry`.
- **Dependency Specification**:
  - Declarative configuration in `pyproject.toml` (PEP 517 / PEP 621).
  - Pin strict lockfiles (`poetry.lock` or `requirements.txt` with hashes) for reproducible builds.

---

## 2. Modular Architecture & Project Layout
Adopt the standard `src/` layout to prevent accidental imports of uninstalled local files:

```text
my-python-project/
├── pyproject.toml
├── src/
│   └── my_project/
│       ├── __init__.py
│       ├── core/
│       ├── engine/
│       ├── adapters/
│       └── utils/
└── tests/
    ├── conftest.py
    ├── unit/
    └── integration/
```

---

## 3. Typing, Static Analysis, and Code Quality
- **Type Annotations**: Mandatory type hints on all public functions, classes, and method signatures.
- **Static Type Checking**: `mypy --strict` or `pyright` in CI pipeline.
- **Linting & Formatting**: Use `ruff` for ultra-fast, unified linting and formatting.
- **Structured Logging**:
  - Never use raw `print()` for system messages in production.
  - Use Python's `logging` module or `structlog` with standardized log levels (`DEBUG`, `INFO`, `WARNING`, `ERROR`, `CRITICAL`).

---

## 4. Exception Hierarchy & Error Handling
- Define a root domain exception class:
  ```python
  class ToolkitError(Exception):
      """Base exception for all domain errors."""
      pass

  class ValidationError(ToolkitError):
      """Raised when schema or input validation fails."""
      pass

  class HardwareCommunicationError(ToolkitError):
      """Raised when peripheral or serial communication drops."""
      pass
  ```
- Always catch specific exceptions; never use bare `except:` without re-raising or logging the backtrace.

---

## 5. Testing & Verification Standard
- **Test Runner**: `pytest` with fixtures in `tests/conftest.py`.
- **Test Coverage**: Maintain `pytest-cov` with minimum 80% coverage on core business logic modules.
- **Deterministic Tests**: Mock hardware interfaces, serial ports, and network calls in unit suites.
