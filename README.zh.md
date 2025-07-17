<div align="center">

![Intro](./docs/assets/xpack/intro-bg.png)


</div>
<p align="center">
  <a href="https://github.com/ThinkInAIXYZ/deepchat/blob/main/LICENSE"><img src="https://img.shields.io/github/license/ThinkInAIXYZ/deepchat" alt="License Badge"/></a>
</p>
<div align="center">
  <a href="./README.zh.md">中文</a> / <a href="./README.md">English</a> / <a href="./README.jp.md">日本語</a>
</div>

## 介绍

本仓库展示了 **DeepChat** 与 **XPack.AI** 的强大集成，演示了如何通过连接全球数千个即用工具来扩展AI助手的功能。基于 [DeepChat](https://deepchat.thinkinai.xyz/) 的强大基础 - 一个功能丰富的开源AI聊天平台，支持多种云端和本地大语言模型 - 本项目提供了配置其模型上下文协议（MCP）服务以利用XPack广泛服务市场的实际示例。

## 什么是 DeepChat？

[DeepChat](https://deepchat.thinkinai.xyz/) 是一个强大的开源AI聊天平台，为与各种大语言模型交互提供统一界面。无论您使用的是OpenAI、Gemini、Anthropic等云端API，还是本地部署的Ollama模型，DeepChat都能提供具有高级功能的流畅用户体验。

**主要特性：**

- **统一多模型管理**：一个应用支持几乎所有主流LLM，无需在多个应用间切换
- **无缝本地模型集成**：内置Ollama支持，让您无需命令行操作即可管理和使用本地模型
- **高级工具调用**：内置MCP支持，无需额外配置即可实现代码执行、网络访问等工具功能
- **强大搜索增强**：支持多种搜索引擎，使AI响应更准确及时
- **隐私保护**：本地数据存储和网络代理支持，降低信息泄露风险
- **商业友好**：采用Apache License 2.0开源协议，适用于商业和个人使用

## 什么是 XPack.AI？

[XPack.AI](https://xpack.ai/) 是一个平台，通过统一的模型上下文协议（MCP）使AI代理能够连接到全球服务和工具的庞大生态系统。通过XPack，您可以轻松扩展AI代理的功能，在不到一分钟的时间内访问金融、物流、消息传递等各个领域的多样化API和服务。

## DeepChat + XPack：连接AI与全球服务

本项目专注于演示如何配置DeepChat以利用XPack作为MCP服务器。通过这样做，您的DeepChat实例可以立即访问XPack丰富的工具集合，让您能够：

- **访问多样化的服务**：从金融数据到图像处理，集成以前无法触及的功能
- **加速开发**：通过利用预构建工具快速原型设计和构建AI驱动的解决方案
- **简化工作流程**：通过结合DeepChat的智能和XPack的外部服务集成来自动化复杂任务
- **轻松扩展**：无需编写自定义集成代码即可连接到数千个全球服务

## 安装

### 下载并安装 DeepChat

首先，确保已安装DeepChat。从[GitHub发布页面](https://github.com/ThinkInAIXYZ/deepchat/releases)下载适用于您操作系统的最新版本。

**📥 快速下载：**

- **Windows**：下载 `.exe` 安装程序
- **macOS**：下载 `.dmg` 安装文件
- **Linux**：下载 `.AppImage` 或 `.deb` 安装文件

下载后，运行安装程序并按照屏幕上的说明完成安装。

<table align="center">
  <tr>
    <td align="center" style="padding: 10px;">
      <img src='https://github.com/user-attachments/assets/5df4ed93-e4b5-4430-a1e3-bd9beba79e64' alt="DeepChat Light Mode" width="400"/>
      <br/>
    </td>
    <td align="center" style="padding: 10px;">
      <img src='https://github.com/user-attachments/assets/79be4873-f80e-43a9-bfac-e1efb246ea99' alt="DeepChat Dark Mode" width="400"/>
      <br/>
    </td>
  </tr>
</table>

_有关开发、项目结构和架构的更详细指南，请参阅[开发者指南](./docs/developer-guide.md)。_

### XPack 集成

要将您的DeepChat连接到XPack，您需要配置MCP服务器。这允许DeepChat发现并利用通过XPack提供的工具。

#### 1. 获取您的 XPack 认证密钥：

- 访问 [XPack.AI](https://xpack.ai/) 并注册账户
- 从您的XPack仪表板生成认证密钥

![XPack.ai Dashboard](./docs/assets/xpack/xpack-dashboard.png)

#### 2. 在 DeepChat 中配置 XPack MCP

##### 选项A：通过 DeepChat 设置UI（推荐）

通过设置UI配置MCP：

- 打开DeepChat应用程序
- 导航到设置页面（⚙️ 设置）
- 切换到 **MCP设置** 选项卡并点击"添加"按钮
- 在 **添加服务器** 模态框中，在文本区域粘贴xpack mcp配置：

  ```json
  {
    "mcpServers": {
      "xpack-mcp-market": {
        "type": "sse",
        "url": "https://api.xpack.ai/v1/mcp?apikey={YOUR_XPACK_AUTH_KEY}",
        "autoApprove":"all"
      }
    }
  }
  ```
![mcp config](./docs/assets/ui-mcp-config-1.png)

##### 选项B：手动配置

如果您喜欢手动配置，也可以使用DeepChat的DeepLink功能进行一键MCP安装：

```
deepChat://mcp/install?code={base64Encode(JSON.stringify(jsonConfig))}
```

⚠️ 将 `YOUR_XPACK_AUTH_KEY` 替换为您从仪表板获得的实际XPack认证密钥。

有关详细的MCP配置说明，请参阅我们的[用户指南](./docs/user-guide.md)。

#### 3. 运行带有 MCP 的 DeepChat

配置完成后，它将自动连接到XPack MCP服务器并发现可用工具。

### 验证配置

要验证您的XPack MCP集成是否正常工作：
1. 通过在DeepChat MCP设置面板中切换开关来启用MCP服务器。
2. 检查工具列表：
    - 如果连接成功，可用工具将显示在下方。
    - 您可以点击任何工具查看更详细的信息。
    - 工具列表和详细工具信息的存在表明服务连接正常且可操作。

![verify configuration](./docs/assets/ui-mcp-config-2.png)

如果配置正确，DeepChat将显示可用的XPack工具并能够将它们用于各种任务。

#### 使用方法

然后您可以在DeepChat中输入您的想法和提示，它将利用XPack的工具来完成任务。只需在您的请求中提及"使用XPack"即可专门利用XPack服务。

## 热门任务

本节提供了如何利用DeepChat与XPack进行各种任务的实际示例。

### 分析YouTube评论并提供建议

轻松分析YouTube视频评论以了解观众情绪并获得改进内容的建议。

```
请使用xpack读取这个YouTube视频的评论：https://www.youtube.com/watch?v=LPZh9BOjkQs，分析反馈的情绪，并推荐视频的改进建议。
```

![Analyze YouTube comments Image](./docs/assets/xpack/demo-youtube-analysis.png)

### 当前黄金价格和影响因素

快速查看最新黄金价格并发现可能影响未来趋势的关键因素。

```
请使用xpack查询当前黄金的实时价格，并提供可能影响其未来价格的具体因素。
```

![Current Gold Price Image](./docs/assets/xpack/demo-gold-monitor.png)

### 生成自定义图像

通过XPack使用AI图像生成工具轻松创建自定义图像。

```
使用xpack生成一张奔跑的小狗图像
```

![Generated image of a cute puppy running in a park](./docs/assets/xpack/demo-running-puppy.png)

### 狗粮广告海报生成

轻松搜索灵感并生成结合热门促销元素的自定义狗粮广告海报。

```
请搜索关于狗粮热门促销海报的图像，然后帮我生成一张结合热门元素的狗粮广告海报
```

![Dog Food Hot Promotion Poster Example](./docs/assets/xpack/demo-dogfood-poster.png)

---

**准备好用全球服务为您的DeepChat增强功能了吗？** 立即开始使用XPack.AI，释放AI驱动助手的全部潜力！
