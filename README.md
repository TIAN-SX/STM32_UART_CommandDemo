# STM32 UART Command Demo

本项目为基于 STM32F103C8T6（蓝丁板）的串口通信命令识别与执行示例。

## ✅ 项目功能

- 使用 USART1 实现串口收发
- 支持中断接收单字节数据
- 可识别字符串命令，如：
  - `led on` → 点亮 PA5 控制的 LED
  - `led off` → 熄灭 PA5 控制的 LED
- 支持回显输入内容，便于调试

## 📦 项目结构

- `STM32_UART_CommandDemo.ioc`：CubeMX 工程配置文件
- `Core/`：用户主代码目录（main.c）
- `Drivers/`：HAL 库和外设驱动代码
- `MDK-ARM/`：Keil 工程目录
- `Startup/`：启动文件（如有）

## 💡 串口命令解析逻辑说明

1. 每收到一个字节，保存到 `rx_buffer` 中
2. 当收到换行符 `\r` 或 `\n` 时，认为一条命令输入完毕
3. 将命令字符串传给 `process_command()` 进行识别与处理

## 🧪 测试环境

- 板卡：STM32F103C8T6（最小系统板）
- IDE：Keil uVision5 + STM32CubeMX
- 串口工具：SSCOM V5.13.1
- 波特率：115200，8-N-1，无流控

## 🛠️ 后续可扩展方向

- 支持更多串口命令（如 `status`、`help` 等）
- 添加 OLED 显示模块
- 拓展为自由指令控制终端（CLI）

---

项目作者：[@TIAN-SX](https://github.com/TIAN-SX)  
如有建议欢迎 PR 或 issue！

