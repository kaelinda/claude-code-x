# Claude Code X (ccx) - 中文文档

一个强大的命令行工具，用于在 Claude Code 中管理和切换不同的 API 提供商，支持高级配置管理和连接测试功能。

## 🚀 快速开始

```bash
# 全局安装
npm install -g claude-code-x

# 本地使用
npm install claude-code-x
npx ccx
```

## 📋 主要功能

- **多提供商支持**：无缝切换 Anthropic、OpenAI、Google 和自定义提供商
- **安全配置**：加密存储 API 密钥和敏感数据
- **连接测试**：内置所有提供商的 API 连接测试
- **备份恢复**：更改配置前自动创建备份
- **跨平台**：Windows、macOS 和 Linux 原生可执行文件
- **交互式 CLI**：用户友好的提示和全面帮助

## 🛠️ 安装方法

### 通过 NPM 安装（推荐）
```bash
npm install -g claude-code-x
```

### 从源码安装
```bash
git clone https://github.com/your-repo/claude-code-x.git
cd claude-code-x
npm install
npm run build
npm link
```

### 预编译二进制文件
从 [发布页面](https://github.com/your-repo/claude-code-x/releases) 下载适合您平台的最新版本。

## 🎯 使用方法

### 基本命令

```bash
# 列出所有已配置的提供商
ccx list

# 显示当前激活的提供商
ccx current

# 切换到不同的提供商
ccx use anthropic

# 添加新的提供商
ccx add openai

# 测试提供商连接
ccx test anthropic

# 打开配置文件
ccx config
```

### 高级用法

```bash
# 添加自定义配置的提供商
ccx add custom --name "我的提供商" --url "https://api.example.com" --model "gpt-4"

# 测试所有提供商
ccx test --all

# 移除提供商
ccx remove openai

# 导出配置
ccx config export --output backup.json

# 导入配置
ccx config import backup.json
```

## 🔧 配置说明

### 提供商类型

#### Anthropic Claude
```json
{
  "name": "Anthropic Claude",
  "type": "anthropic",
  "api_key": "sk-ant-...",
  "base_url": "https://api.anthropic.com",
  "model": "claude-3-5-sonnet-20241022"
}
```

#### OpenAI GPT
```json
{
  "name": "OpenAI GPT",
  "type": "openai",
  "api_key": "sk-...",
  "base_url": "https://api.openai.com",
  "model": "gpt-4-turbo"
}
```

#### Google Gemini
```json
{
  "name": "Google Gemini",
  "type": "google",
  "api_key": "...",
  "base_url": "https://generativelanguage.googleapis.com",
  "model": "gemini-1.5-flash"
}
```

#### Kimi (月之暗面)
```json
{
  "name": "Kimi",
  "type": "kimi",
  "api_key": "sk-...",
  "base_url": "https://api.moonshot.cn/v1",
  "model": "moonshot-v1-32k"
}
```

#### 自定义提供商
```json
{
  "name": "自定义提供商",
  "type": "custom",
  "api_key": "...",
  "base_url": "https://api.custom.ai",
  "model": "custom-model",
  "headers": {"Authorization": "Bearer {api_key}"}
}
```

### 配置文件

- **用户配置**: `~/.claude/providers.json`
- **设置**: `~/.claude/settings.json`
- **备份**: `~/.claude/backups/`

## 🧪 开发指南

### 前置要求
- Node.js 16+
- npm 7+

### 设置开发环境
```bash
git clone https://github.com/your-repo/claude-code-x.git
cd claude-code-x
npm install
```

### 开发命令
```bash
# 开发模式运行
npm run dev

# 运行测试
npm test

# 代码检查
npm run lint

# 构建 TypeScript
npm run build

# 创建可执行文件
npm run pkg
```

## 🧪 测试

```bash
# 运行所有测试
npm test

# 带覆盖率的测试
npm run test:coverage

# 运行特定测试文件
npm test -- --testPathPattern=cli.test.ts

# 监听模式运行测试
npm run test:watch
```

## 🔒 安全特性

- API 密钥加密存储
- 更改配置前自动创建备份
- 安全输入处理（密码掩码）
- 不记录敏感信息

## 📦 分发

### 构建跨平台可执行文件
```bash
npm run pkg
```

这会创建以下可执行文件：
- Windows (ccx.exe)
- macOS (ccx)
- Linux (ccx)

## 🤝 贡献指南

1. Fork 仓库
2. 创建功能分支：`git checkout -b feature/amazing-feature`
3. 进行更改
4. 为新功能添加测试
5. 运行测试：`npm test`
6. 提交更改：`git commit -m 'Add amazing feature'`
7. 推送到分支：`git push origin feature/amazing-feature`
8. 创建 Pull Request

## 🐛 故障排除

### 常见问题

**提供商连接失败**
```bash
# 检查 API 密钥
ccx test <provider>

# 验证配置
ccx config

# 重置配置
ccx config reset
```

**配置损坏**
```bash
# 从备份恢复
ccx config restore

# 重置为默认值
ccx config reset --force
```

**权限问题**
```bash
# 修复文件权限
chmod +x ~/.claude/providers.json
```

## 📄 许可证

MIT 许可证 - 详见 [LICENSE](LICENSE) 文件。

## 🆘 支持

- **问题反馈**: [GitHub Issues](https://github.com/your-repo/claude-code-x/issues)
- **讨论**: [GitHub Discussions](https://github.com/your-repo/claude-code-x/discussions)
- **文档**: [Wiki](https://github.com/your-repo/claude-code-x/wiki)

## 🔄 更新日志

详见 [CHANGELOG.md](CHANGELOG.md) 了解版本历史和更新内容。