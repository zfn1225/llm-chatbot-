=======
# llm-chatbot-
llm chatbot 项目重构
>>>>>>> 1d7954a889076d71166f8ca9f25cd3293eab969a
## 📦 项目结构

```bash
src/
├── assets/ # 静态资源
├── components/ # 组件
│ ├── ChatInput.vue # 聊天输入框组件
│ ├── ChatMessage.vue # 消息显示组件
│ ├── DialogEdit.vue # 对话编辑弹窗
│ ├── PopupMenu.vue # 侧边菜单组件
│ ├── SearchDialog.vue # 搜索对话框组件
│ └── SettingsPanel.vue # 设置面板组件
├── stores/ # Pinia 状态管理
│ ├── chat.js # 聊天相关状态
│ └── setting.js # 设置相关状态
├── utils/ # 工具函数
│ ├── api.js # API 请求封装
│ ├── markdown.js # Markdown 处理
│ └── messageHandler.js # 消息处理
├── views/ # 页面
│ ├── HomePage.vue # 首页
│ └── ChatView.vue # 主聊天页面
└── App.vue # 根组件
```