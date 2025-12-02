# 3DOF-Robotic-Arm-xiaozhi-server

基于[小智 AI](https://github.com/xinnan-tech/xiaozhi-esp32-server)的 RRR 构型三自由度机械臂的语音控制服务端

用于将自然语言转换到具体机器指令，具体的命令说明可以参照 [LanternCX/ZhiGrip-Controller](https://github.com/LanternCX/ZhiGrip-Controller) 的 websocket 接口说明以及本项目小智框架中 [ZhiGrip-xiaozhi-server/plugins_func/functions](https://github.com/LanternCX/ZhiGrip-xiaozhi-server/tree/main/plugins_func/functions) 以 `robotic_arm` 开头的插件文件中的说明

## Environment

部署可以完全参照小智AI文档的本地源码部署部分：[xiaozhi-esp32-server/docs/Deployment.md](https://github.com/xinnan-tech/xiaozhi-esp32-server/blob/main/docs/Deployment.md)

 - Python version: Python 3.10

需要自行下载 `opus` 库，Windows 平台可能需要自行编译构建

然后添加环境变量到 Python 环境

```bash
export DYLD_LIBRARY_PATH="$(brew --prefix opus)/lib:$DYLD_LIBRARY_PATH"
```
## Quick Start
在 Web 端测试：

```bash
cd test
python -m http.server 8006
```

然后访问 `http://localhost:8006/test_page.html` 就好

目前通讯 Demo 基于本地虚拟串口，安装 `socat` 之后运行下面的命令启动虚拟串口

```bash
socat -d -d PTY,link=/tmp/ttyV0,raw,echo=0 PTY,link=/tmp/ttyV1,raw,echo=0
```