# Git工具安装与使用报告

## 学员GitHub用户名: savanna0425

## 1. Git安装过程

### 操作系统
macOS (darwin 24.5.0)

### 安装方法
macOS系统通常已经预装了Git，或者可以通过以下方式安装：

1. **使用Homebrew安装**（推荐）：
   ```bash
   brew install git
   ```

2. **使用Xcode Command Line Tools**：
   ```bash
   xcode-select --install
   ```

3. **从官网下载安装包**：
   访问 https://git-scm.com/download/mac 下载macOS安装包

### 验证安装
通过执行 `git --version` 命令验证Git是否已正确安装：

```bash
git --version
```

**安装结果**：Git已成功安装，当前版本为 **git version 2.39.5 (Apple Git-154)**

### 安装过程说明
由于macOS系统通常预装Git，或者通过Xcode Command Line Tools自动安装，本次安装过程较为简单，直接通过命令行验证即可确认Git已正确安装。

## 2. 遇到的问题及解决方法

### 问题1：Git未安装或版本过旧
**问题描述**：执行 `git --version` 时提示命令未找到

**解决方法**：
- 如果使用Homebrew：`brew install git`
- 如果使用Xcode工具：`xcode-select --install`
- 或者从官网下载安装包进行安装

### 问题2：Git配置问题
**问题描述**：首次使用Git时需要配置用户信息

**解决方法**：
```bash
# 配置用户名
git config --global user.name "savanna0425"

# 配置邮箱
git config --global user.email "your-email@example.com"

# 查看配置
git config --list
```

### 问题3：SSH密钥配置（用于GitHub认证）
**问题描述**：使用SSH方式连接GitHub时需要配置SSH密钥

**解决方法**：
```bash
# 生成SSH密钥
ssh-keygen -t ed25519 -C "your-email@example.com"

# 查看公钥
cat ~/.ssh/id_ed25519.pub

# 将公钥添加到GitHub账户的SSH Keys中
```

**本次实践**：未遇到上述问题，Git已正确安装并可以使用。

## 3. 版本信息截图

见gitversion.png

## 4. Git命令使用过程总结

### 4.1 Fork仓库并克隆到本地

#### 步骤1：Fork仓库
1. 访问 https://github.com/upstreamlabs/github101
2. 点击右上角的 "Fork" 按钮
3. 选择自己的GitHub账号，完成Fork操作

#### 步骤2：克隆仓库到本地
```bash
# 克隆Fork后的仓库（替换为你的GitHub用户名）
git clone https://github.com/savanna0425/github101.git

# 或者使用SSH方式（如果已配置SSH密钥）
git clone git@github.com:savanna0425/github101.git

# 进入仓库目录
cd github101
```

### 4.2 配置Git用户信息（如未配置）

```bash
# 设置全局用户名
git config --global user.name "savanna0425"

# 设置全局邮箱（使用GitHub注册邮箱）
git config --global user.email "your-email@example.com"

# 查看配置信息
git config --list
```

### 4.3 创建作业文件并提交

#### 步骤1：创建作业文件
```bash
# 确保在仓库根目录
cd /path/to/github101

# 创建作业文件（已在assignments/lesson2/目录下创建savanna0425.md）
# 文件路径：assignments/lesson2/savanna0425.md
```

#### 步骤2：查看文件状态
```bash
# 查看当前工作区状态
git status

# 输出示例：
# On branch main
# Untracked files:
#   assignments/lesson2/savanna0425.md
```

#### 步骤3：添加文件到暂存区
```bash
# 添加单个文件
git add assignments/lesson2/savanna0425.md

# 或者添加所有更改
git add .

# 查看暂存区状态
git status
```

#### 步骤4：提交更改到本地仓库
```bash
# 提交更改，并添加提交信息
git commit -m "完成第二课作业：Git工具实践报告"

# 查看提交历史
git log --oneline
```

#### 步骤5：推送到远程仓库
```bash
# 推送到远程仓库的main分支
git push origin main

# 如果是第一次推送，可能需要设置上游分支
git push -u origin main
```

### 4.4 创建Pull Request

#### 步骤1：在GitHub上创建PR
1. 访问Fork后的仓库：https://github.com/savanna0425/github101
2. 点击 "Pull requests" 标签
3. 点击 "New pull request" 按钮
4. 选择 base repository: `upstreamlabs/github101` (base: main)
5. 选择 head repository: `savanna0425/github101` (compare: main)
6. 填写PR标题和描述
7. 点击 "Create pull request"

#### 步骤2：等待审核和合并
- 等待仓库维护者审核
- 根据反馈进行修改（如有需要）
- PR合并后，作业完成

### 4.5 常用Git命令总结

#### 基础命令
- **git clone [url]**：克隆远程仓库到本地
- **git status**：查看工作区状态
- **git add [file]**：添加文件到暂存区
- **git commit -m "message"**：提交更改到本地仓库
- **git push**：推送本地提交到远程仓库
- **git pull**：从远程仓库拉取最新更改

#### 查看命令
- **git log**：查看提交历史
- **git log --oneline**：查看简化的提交历史
- **git diff**：查看工作区与暂存区的差异
- **git diff --staged**：查看暂存区与最后一次提交的差异

#### 分支命令
- **git branch**：查看所有分支
- **git branch [name]**：创建新分支
- **git checkout [branch]**：切换到指定分支
- **git merge [branch]**：合并指定分支到当前分支

#### 远程仓库命令
- **git remote -v**：查看远程仓库信息
- **git remote add [name] [url]**：添加远程仓库
- **git fetch**：从远程仓库获取最新信息（不合并）
- **git pull**：从远程仓库拉取并合并

### 4.6 Git工作流程理解

#### 三个区域
1. **工作区（Working Directory）**：当前编辑的文件
2. **暂存区（Staging Area）**：通过 `git add` 添加的文件
3. **本地仓库（Repository）**：通过 `git commit` 提交的文件

#### 基本工作流程
```
工作区 → git add → 暂存区 → git commit → 本地仓库 → git push → 远程仓库
```

#### 协作流程
1. **Fork**：从原始仓库创建自己的副本
2. **Clone**：将远程仓库克隆到本地
3. **Edit**：在本地进行修改
4. **Commit**：提交更改到本地仓库
5. **Push**：推送更改到自己的Fork仓库
6. **Pull Request**：向原始仓库提交合并请求

### 4.7 使用体验和心得

#### 优势
1. **版本控制**：可以追踪文件的每一次更改，方便回退和对比
2. **分支管理**：可以创建多个分支并行开发，不影响主分支
3. **协作便利**：多人协作时，通过Pull Request进行代码审查和合并
4. **分布式**：每个开发者都有完整的仓库副本，不依赖中央服务器

#### 注意事项
1. **提交信息要清晰**：使用有意义的提交信息，方便后续查看历史
2. **频繁提交**：建议频繁提交，每次提交解决一个小问题
3. **拉取最新代码**：在推送前先拉取最新代码，避免冲突
4. **分支管理**：合理使用分支，保持主分支稳定

#### 对开源协作的理解
通过Git和GitHub的使用，我深刻理解了开源协作的工作流程：
- **Fork & Pull Request模式**：这是开源项目协作的标准模式
- **代码审查**：通过PR进行代码审查，保证代码质量
- **社区贡献**：任何人都可以通过Fork和PR为开源项目做贡献
- **版本管理**：Git的强大版本管理能力是开源协作的基础

### 4.8 实际操作记录

#### 操作时间线
1. **安装验证**：执行 `git --version` 确认Git已安装（版本2.39.5）
2. **创建作业文件**：在 `assignments/lesson2/` 目录下创建 `savanna0425.md`
3. **编写报告**：完成Git安装过程、问题解决、命令使用等内容的撰写
4. **初始化Git仓库**：由于本地目录不是git仓库，执行 `git init` 初始化
5. **配置远程仓库**：执行 `git remote add origin https://github.com/savanna0425/github101.git`
6. **配置用户信息**：执行 `git config user.name "savanna0425"` 和 `git config user.email`
7. **添加文件**：执行 `git add .` 添加所有文件到暂存区
8. **提交更改**：执行 `git commit -m "完成第一课和第二课作业：开源商业模式分析报告和Git工具实践报告"`
9. **合并远程更改**：执行 `git pull origin main --allow-unrelated-histories --no-rebase` 合并远程仓库内容
10. **推送到远程**：执行 `git push origin main` 成功推送到远程仓库

#### 实际执行的Git命令记录

```bash
# 1. 初始化Git仓库
git init

# 2. 添加远程仓库
git remote add origin https://github.com/savanna0425/github101.git

# 3. 配置用户信息
git config user.name "savanna0425"
git config user.email "savanna0425@users.noreply.github.com"

# 4. 查看仓库状态
git status

# 5. 添加所有文件到暂存区
git add .

# 6. 提交更改
git commit -m "完成第一课和第二课作业：开源商业模式分析报告和Git工具实践报告"

# 7. 查看提交历史
git log --oneline
# 输出：c62806e 完成第一课和第二课作业：开源商业模式分析报告和Git工具实践报告

# 8. 拉取并合并远程仓库内容
git pull origin main --allow-unrelated-histories --no-rebase

# 9. 推送到远程仓库
git push origin main
# 输出：To https://github.com/savanna0425/github101.git
#       17b6cdd..a425c9a  main -> main
```

#### 遇到的问题及解决

**问题1：推送被拒绝**
- **错误信息**：`! [rejected] main -> main (fetch first)`
- **原因**：远程仓库已有内容，本地仓库是新建的，历史不相关
- **解决方法**：使用 `git pull origin main --allow-unrelated-histories --no-rebase` 合并远程内容

**问题2：需要指定合并策略**
- **错误信息**：`fatal: Need to specify how to reconcile divergent branches.`
- **解决方法**：使用 `--no-rebase` 参数指定使用merge策略

#### 下一步操作
1. ✅ 初始化Git仓库 - 已完成
2. ✅ 添加文件到暂存区 - 已完成
3. ✅ 提交到本地仓库 - 已完成
4. ✅ 推送到远程仓库 - 已完成
5. **创建Pull Request**：在GitHub上向原始仓库（upstreamlabs/github101）提交PR

---

