<h1  align="center">DevEco Toolbox</h1>

`DevEco Toolbox`是一个工具集(依赖于[`DevEco Studio`](https://developer.huawei.com/consumer/cn/download/))。在不打开`DevEco Studio`的情况下，你可以用它在`Trae`、`Curosr`、`Visual Studio Code`等AI IDE中完成鸿蒙应用开发的大多数工作。

<br>

`DevEco Toolbox`当前包含两个可执行文件：
* `deveco-toolbox` 用于可视化配置
* `deveco-mcp-server` 主要的mcp服务


## mcp tools合集

| tool_name  | 主要功能  |
|---|---|
|`build_project`|进行项目构建|
|`check_ets_files`|对ets文件进行语法检查|
|`start_app`|在模拟器或者真机中启动应用，支持启动模拟器或选择已连接的真机|
|`get_uidump`|获取app当前页面的ui树|
|`execute_uitest`|在已启动的app页面中执行点击或者输入动作|

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

### 卸载

1. Windows 版本可直接删除，所有数据仅存在该应用所在目录下 
2. mac 版本在此基础上还需额外执行如下指令：
  ```bash
  rm -r ~/Library/Application\ Support/deveco-toolbox
  ```


