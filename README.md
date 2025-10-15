#### COMP3104 – Developer Operations
-- Bryan Paul Yabut

# GitHub Action Status Badge
[![CI](https://github.com/bryanyabut/COM3104-DEVOPS/actions/workflows/ci.yml/badge.svg)](https://github.com/bryanyabut/COM3104-DEVOPS/actions/workflows/ci.yml)


# Commit Msg Hook (Enforce commit Message format)
#!/bin/sh
COMMIT_MSG_FILE=$1
COMMIT_MSG=$(cat $COMMIT_MSG_FILE)
Hello world
```

if ! echo "$COMMIT_MSG" | grep -Eq "^(feat|fix|docs|style|refactor|test|chore): .+"; then
  echo "Commit message must follow the format: <type>: <description>"
  echo "Example: feat: add user authentication"
  exit 1
fi
```

Pre-Commit Hook
ensures that code is linted before committing
```
#!/bin/sh
echo "Running pre-commit hook: Linting code..."
npm --version
# npm run lint
if [ $? -ne 0 ]; then
  echo "Linting failed. Fix errors before committing."
  exit 1
fi
```

Pre-Push hook
#!/bin/sh
echo "Running pre-push hook: Running tests..."
npm test
if [ $? -ne 0 ]; then
  echo "Tests failed! Fix them before pushing."
  exit 1
fi