<h1  align="center">DevEco Toolbox</h1>

`DevEco Toolbox`是一个工具集(依赖于[`DevEco Studio`](https://developer.huawei.com/consumer/cn/download/))。在不打开`DevEco Studio`的情况下，你可以用它在`Trae`、`Curosr`、`Visual Studio Code`等AI IDE中完成鸿蒙应用开发的大多数工作。

<br>

`DevEco Toolbox`当前包含两个可执行文件：
* `deveco-toolbox` 用于可视化配置
* `deveco-mcp-server` 主要的mcp服务


## mcp tools合集 [![npx deveco-mcp-server](https://img.shields.io/badge/npx-deveco--mcp--server-CB3837?logo=npm)](https://www.npmjs.com/package/deveco-mcp-server)

| tool_name  | 主要功能  |
|---|---|
|`harmonyos_knowledge_search`|查询鸿蒙云端知识库（已实时更新api22)|
|`check_ets_files`|对ets文件进行语法检查|
|`build_project`|进行项目构建|
|`start_app`|在模拟器或者真机中启动应用，支持启动模拟器或选择已连接的真机|
|`get_uidump`|获取app当前页面的ui树|
|`execute_uitest`|在已启动的app页面中执行点击或者输入动作|
|`create_harmony_project`|创建鸿蒙模板工程|

## 使用npx安装MCP服务
* `PROJECT_PATH` 工程路径
* `DEVECO_PATH` `DevEco Studio`的安装路径
```json
{
  "mcpServers": {
    "deveco-mcp": {
      "command": "npx",
      "args": [
        "-y",
        "deveco-mcp-server"
      ],
      "env": {
        "PROJECT_PATH": "${workspaceFolder}",
        "DEVECO_PATH": "path to deveco studio"
      }
    }
  }
}
```
faq：
* 如果使用 npx 配置失败且提示 "Platform package deveco-mcp-server-xxx not found"，通常是由于用户/IDE使用了国内 npm 镜像源，而国内镜像源未及时同步导致的。请将 MCP 配置文件修改为：
```json
{
  "mcpServers": {
    "deveco-mcp": {
      "command": "npx",
      "args": [
        "--registry=https://registry.npmjs.org",
        "-y",
        "deveco-mcp-server"
      ],
      "env": {
        "PROJECT_PATH": "${workspaceFolder}",
        "DEVECO_PATH": "path to deveco studio"
      }
    }
  }
}
```
## 下载二进制安装并使用

### 下载

- [github](https://github.com/open-deveco/deveco-mcp/releases)


### 下载安装

#### MacOS

1. 下载并安装dmg程序；
2. 终端执行如下命令
   ```bash
   xattr -cr /Applications/DevEco\ Toolbox.app
   ```

#### Windows
1. 下载zip包并解压；

特别注意：
* 尽量避免在安装路径中包含特殊字符或中文，部分AI IDE不支持解析此类路径。


### 快速启动
* MacOS上，可点击`DevEco Toolbox` app图标快速启动；
* Windows上，可点击`deveco-toolbox.exe`图标快速启动；

启动后会自动探测本机安装的`DevEco Studio`路径，若未检测到，需要手动指定。

在可选配置中，可单独配置模拟器路径和镜像路径，如有需要可手工指定路径。

界面上已经放置了添加到`Trae`和`Cursor`的按钮，点击即可将MCP配置添加到`Trae`或`Cursor`中。
如果是其他IDE，可通过复制MCP JSON配置的方式添加到对应的IDE中。
```json
{
  "mcpServers": {
    "deveco-mcp": {
      "command": "cmd",
      "args": [
        "/C",
        "D:\\program_files\\deveco-mcp_x64_windows\\deveco-mcp-server.exe"
      ],
      "env": {
        "PROJECT_PATH": "${workspaceFolder}"
      }
    }
  }
}
```


特别注意：
* 如果IDE不支持`${workspaceFolder}`变量替换，需要手动替换为指定路径。

### ArkTS语法校验插件
本插件基于鸿蒙官方DevEco Studio编辑器的LSP语言服务器开发，更贴近官方，检查错误更加全面

### 安装方式

安装方式一：在 Toolbox 中直接一键安装 ArkTS 高亮插件
<img width="440" height="660" alt="image-28" src="https://github.com/user-attachments/assets/fc4d8802-c459-4aad-880f-604572877bab" />

安装方式二：手动安装 ArkTS 高亮插件
若本地没有配置对应IDE的bin路径为环境变量，需要手动安装 ArkTS 插件。
打开Toolbox所在目录，找到 ArkTS 高亮插件 vsix，将插件拖到对应 IDE 插件市场进行安装，安装好后，重启ide。

<img width="1829" height="1188" alt="image-22" src="https://github.com/user-attachments/assets/2e3d4290-5ab1-4076-bd45-938acd50af00" />

### 使用方式

打开ide后，右下角有一个状态，表示插件正在初始化，当插件初始化完成后，会变为白色，表示可以正常校验ArkTS语法

<img width="1834" height="1190" alt="image-23" src="https://github.com/user-attachments/assets/a1551d42-fba9-4abc-9f5d-4b9921c3e092" />
<img width="1834" height="1190" alt="image-24" src="https://github.com/user-attachments/assets/a9ee6d4a-ba7d-4520-9058-3eaac953fd0a" />


### 卸载

1. Windows 版本可直接删除，所有数据仅存在该应用所在目录下 
2. mac 版本在此基础上还需额外执行如下指令：
  ```bash
  rm -r ~/Library/Application\ Support/deveco-toolbox
  ```
### 问题/需求反馈

如果你在配置或使用[鸿蒙MCP工具箱」时遇到任何阻碍，欢迎随时联系我们：

1️⃣ GitHub Issue（技术/需求/缺陷均可）
[https://github.com/open-deveco/deveco-toolbox/issues](https://github.com/open-deveco/deveco-toolbox/issues)

2️⃣ 飞书指导文档
[https://my.feishu.cn/wiki/E19rwYUtbiJtnlkPFBVcvnuUnBd](https://my.feishu.cn/wiki/E19rwYUtbiJtnlkPFBVcvnuUnBd)

3️⃣ 飞书答疑群（实时互动）
搜索「鸿蒙 MCP 官方交流群」或扫码加入，群内可快速定位问题、获取最新版本、参与功能投票。
![084150c18fb06e0a2ee2e2c62a07110a](https://github.com/user-attachments/assets/a8a1329a-1e5b-42b6-8677-766d72eb34e7)
我们珍视每一条反馈——你的 issue & 群消息，就是下一个版本更新的源头！

