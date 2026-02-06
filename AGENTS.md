# AGENTS.md - Development Guidelines for MyMoltbot

## Project Overview
New repository. Determine language/framework from existing patterns or create a modern structure.

## Build, Lint, and Test Commands

### Running the Application
```bash
# Python: python -m src.main
# Node.js: npm run dev / npm start
# Go: go run .
```

### Linting
```bash
# Python: ruff check . / pylint .
# Node.js: npm run lint / eslint .
# Go: golangci-lint run
```

### Running Tests
```bash
# All tests: pytest / npm test / go test ./...
# Single test file: pytest tests/test_module.py / npm test -- tests/module.test.ts
# Single test function: pytest tests/test_module.py::test_function_name
# With coverage: pytest --cov=src / npm test -- --coverage
```

## Code Style Guidelines

### Imports
```python
# Python: stdlib → third-party → local
import os
from typing import Optional
import requests
from .models import User
```

```typescript
// TypeScript: absolute → relative imports
import { useState } from 'react'
import { api } from '@/lib/api'
import { Component } from './component'
```

### Formatting
- 4 spaces for indentation (2 for JS)
- Max line length: 100-120 chars
- Consistent spacing around operators

### Types
```python
from typing import Dict, List, Optional

def process(items: List[Dict]) -> Optional[Dict]:
    if not items:
        return None
    return {"count": len(items)}
```

```typescript
interface User {
  id: string
  name: string
  role: 'admin' | 'user' | 'guest'
}
function getUser(id: string): Promise<User>
```

### Naming Conventions
- **Files**: `snake_case.py`, `kebab-case.ts`
- **Classes**: `PascalCase`
- **Functions/Variables**: `snake_case` (Python), `camelCase` (JS/TS)
- **Constants**: `UPPER_SNAKE_CASE`
- **Booleans**: `is_valid`, `has_permission`

### Error Handling
```python
class AppError(Exception):
    def __init__(self, message: str, code: str):
        super().__init__(message)
        self.code = code

def fetch_user(user_id: str) -> User:
    try:
        user = database.get(user_id)
        if not user:
            raise AppError(f"User {user_id} not found", "NOT_FOUND")
        return user
    except DatabaseConnectionError:
        raise AppError("Service unavailable", "SERVICE_ERROR")
```

### Code Organization
- Keep related code together (colocation)
- Separate business logic from I/O operations
- Feature-based directory structure

### Testing
- Write tests for all business logic
- Descriptive test names: `test_user_creation_with_valid_data`
- Follow Arrange-Act-Assert pattern
- Mock external dependencies

## Git Workflow
1. Make changes in `/workspaces/MyMoltbot`
2. Commit with descriptive messages
3. Push to: https://github.com/sacallenandroid-coder/MyMoltbot
4. Use: `/home/codespace/.openclaw/workspace/scripts/git-push.sh`

## Communication
- Current branch: `main`
- Be concise
- Ask for clarification when requirements are ambiguous
