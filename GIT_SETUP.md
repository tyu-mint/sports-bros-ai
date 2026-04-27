# Git Setup

```bash
cd sports-bros-ai-repo
git init
git add .
git commit -m "v0.4 editable context single html"
git tag v0.4-editable-context
```

下一步功能分支：

```bash
git checkout -b feature/memory-settings
```

完成后：

```bash
git add .
git commit -m "add memory settings"
git checkout main
git merge feature/memory-settings
git tag v0.5-memory-settings
```
