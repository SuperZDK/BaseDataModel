# Git 提交指南

本指南适用于本项目（BaseDataModel）的日常 Git 使用。

## 一、基本流程

```bash
# 1. 查看当前状态（改动、暂存情况）
git status

# 2. 查看具体改动内容
git diff                 # 未暂存的改动
git diff --cached        # 已暂存的改动

# 3. 添加改动到暂存区
git add <文件名>          # 添加单个文件
git add -A              # 添加全部改动（推荐日常使用）

# 4. 提交
git commit -m "提交说明"

# 5. 推送到远程
git push
```

## 二、提交信息规范

推荐使用「类型 + 中文描述」格式，类型可选：

| 类型     | 含义                           | 示例 |
|----------|--------------------------------|------|
| feat     | 新功能                         | `feat: 新增积分计算模块` |
| fix      | 修复 Bug                       | `fix: 修复待审标签错乱问题` |
| update   | 更新内容（日常迭代）           | `update: 更新综合矩阵v4.0待审8` |
| docs     | 文档类改动                     | `docs: 更新使用说明` |
| refactor | 重构代码（不改变功能）         | `refactor: 重构计算工具结构` |
| style    | 格式调整（不改逻辑）           | `style: 调整页面样式` |

> 本项目以模型文档/网页为主，日常使用 `feat`、`update`、`fix` 三种即可。

## 三、常用操作

```bash
# 查看提交历史
git log --oneline -10

# 撤销暂存（不删除改动）
git reset HEAD <文件名>

# 撤销最近一次提交（保留改动在工作区）
git reset --soft HEAD~1

# 拉取远程最新代码
git pull

# 查看远程分支
git branch -r
```

## 四、注意事项

1. **提交前先 `git status` 确认改动范围**，避免误提交文件。
2. **提交信息用中文、简洁明了**，说明「做了什么」而非流水账。
3. **每个提交只包含一个逻辑改动**，方便回溯。
4. **不要在提交信息中写无关内容**，如日期、心情等。
5. **推送前先 `git pull`**，避免冲突。
6. 如遇冲突，先解决冲突文件，再 `git add` 并 `git commit`。

## 五、分支说明

- `main` 为主分支，保持稳定可用。
- 新功能建议在独立分支开发，完成后合并回 `main`：
  ```bash
  git checkout -b feature/xxx   # 新建分支
  git checkout main             # 切回主分支
  git merge feature/xxx         # 合并分支
  ```

## 六、快速参考

| 需求               | 命令 |
|--------------------|------|
| 全部提交并推送     | `git add -A; git commit -m "update: ..."; git push` |
| 只提交某个文件     | `git add 文件名; git commit -m "..."` |
| 查看历史           | `git log --oneline` |
| 丢弃工作区改动     | `git checkout -- <文件名>` |
| 丢弃未提交的全部改动 | `git reset --hard HEAD`（谨慎使用） |
