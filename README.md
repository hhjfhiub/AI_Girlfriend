# AI女友微信机器人

一个接入微信平台并对接DeepSeek的AI女友机器人，可以和你进行自然、温馨的对话。

## 功能特点

- 🤖 **微信平台接入**：通过Wechaty实现微信消息的接收和发送
- 🧠 **DeepSeek驱动**：使用DeepSeek API生成智能、自然的回复
- 🎭 **个性化设定**：可配置AI女友的名字、性格和对话风格
- 💬 **对话历史管理**：记忆对话上下文，提供连贯的对话体验
- 📱 **群聊和私聊**：支持在群聊中@机器人或私聊机器人
- 📝 **日志系统**：完整记录系统运行日志，便于问题排查
- 🔐 **登录状态持久化**：支持微信登录状态持久化，即使微信客户端清理数据后机器人仍能运行

## 技术栈

- Node.js
- Wechaty + Wechat4u Puppet
- DeepSeek API
- Express
- Winston (日志)
- Dotenv (环境变量)

## 快速开始

### 1. 安装依赖

```bash
cd AI_Girlfriend
npm install
```

### 2. 配置环境变量

复制`.env.example`文件为`.env`，并填写以下配置：

```bash
# DeepSeek配置
DEEPSEEK_API_KEY=your_deepseek_api_key
DEEPSEEK_MODEL=deepseek-chat
DEEPSEEK_TEMPERATURE=0.7

# 应用配置
PORT=3000
DEBUG=false

# AI女友配置
AI_GIRLFRIEND_NAME=小女友
AI_GIRLFRIEND_PERSONALITY=可爱、温柔、善解人意的女朋友
```

#### 配置说明：

- **DEEPSEEK_API_KEY**：DeepSeek API密钥，可从[DeepSeek官网](https://platform.deepseek.com/)获取
- **DEEPSEEK_MODEL**：使用的DeepSeek模型，默认为deepseek-chat
- **DEEPSEEK_TEMPERATURE**：生成回复的随机性，0-2之间，值越高回复越随机
- **AI_GIRLFRIEND_NAME**：AI女友的名字
- **AI_GIRLFRIEND_PERSONALITY**：AI女友的性格描述

### 3. 启动机器人

```bash
# 启动机器人
npm start

# 或使用开发模式（自动重启）
npm run dev
```

### 4. 扫码登录

首次启动后，会在控制台显示微信登录二维码，使用微信扫码登录即可。登录状态会自动持久化保存，后续启动无需重新扫码。

## 使用方法

### 私聊

直接向机器人发送消息，机器人会以AI女友的身份回复你。

### 群聊

在群聊中@机器人并发送消息，机器人会在群聊中回复你。

## 项目结构

```
AI_Girlfriend/
├── src/
│   ├── wechat/          # 微信平台接入模块
│   │   └── handler.js   # 微信事件处理器
│   ├── openai/          # AI API对接模块（兼容DeepSeek）
│   │   └── client.js    # AI客户端
│   ├── ai/              # AI女友核心模块
│   │   ├── character.js # 角色配置
│   │   ├── chatHistory.js # 对话历史管理
│   │   └── manager.js   # AI管理器
│   └── utils/           # 工具模块
│       └── logger.js    # 日志工具
├── logs/                # 日志文件
├── .env                 # 环境变量配置
├── .env.example         # 环境变量示例
├── AI-Girlfriend.memory-card.json # 登录状态持久化文件
├── package.json         # 项目配置
└── index.js             # 主入口文件
```

## 注意事项

1. 请遵守微信的使用规范，不要滥用机器人功能
2. 保护好你的API密钥，不要泄露给他人
3. 机器人的回复内容由DeepSeek生成，请确保使用合法合规的内容
4. 定期检查日志文件，及时发现和解决问题
5. 登录状态持久化文件`AI-Girlfriend.memory-card.json`包含敏感的登录信息，请妥善保管

## 常见问题

### Q: 机器人无法登录微信？
A: 请检查网络连接是否正常，以及是否已正确安装Wechat4u依赖。

### Q: 机器人没有回复？
A: 请检查DEEPSEEK_API_KEY是否正确，以及DeepSeek服务是否正常。

### Q: 如何修改AI女友的性格？
A: 可以在.env文件中修改AI_GIRLFRIEND_PERSONALITY参数，或直接修改src/ai/character.js文件。

### Q: 微信客户端清理数据后机器人还能运行吗？
A: 可以，机器人的登录状态已通过`AI-Girlfriend.memory-card.json`文件持久化保存，清理微信数据后仍能正常运行。

## 许可证

MIT License

## 贡献

欢迎提交Issue和Pull Request！