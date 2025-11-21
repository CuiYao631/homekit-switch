
# Homekit Switch

基于 ESP32 和 HomeSpan 库的 HomeKit 智能开关，支持物理按钮和 HomeKit 控制，适用于智能家居照明场景。

## 项目简介

本项目实现了一个可通过 Apple HomeKit 控制的智能开关，支持物理按钮切换、远程控制、状态指示灯等功能。适用于 DIY 智能家居、灯光自动化等应用。

## 硬件需求

- ESP32 开发板
- 继电器模块或 LED 灯
- 物理开关按钮
- LED 指示灯

## 功能特性

- HomeKit 支持（通过 HomeSpan 库）
- 物理按钮短按切换灯光，长按恢复出厂设置
- 灯光状态同步指示
- 设备信息展示（名称、厂商、序列号等）

## 快速开始
### 配网方式

1. 通电后，设备会自动进入配网模式，创建名为 `HomeSpan-Setup` 的 WiFi 热点。
2. 使用手机或电脑连接该热点，密码为 `homespan`。
3. 连接成功后，访问 `192.168.4.1`，进入配网页面。
4. 在页面中选择或输入要连接的 WiFi（仅支持 2.4GHz 网络），完成配网。



1. 克隆本仓库，将 `homekit-switch.ino` 上传至 ESP32 开发板。
2. 按照下方引脚定义连接硬件。
3. 通电后，设备会自动进入 HomeKit 配对模式。
4. 打开 Apple 家庭 App，扫描下方二维码或输入配对码 `46637726` 添加设备。

### HomeKit 配对二维码

![HomeKit 配对二维码](/lightbulb_qr.png)

> 若二维码无法识别，可手动输入配对码：`46637726`

## 引脚说明
## LED状态指示灯说明

设备上的 LED 指示灯（GPIO32）用于显示当前状态：

- **快闪**：未连接 Wi-Fi
- **慢闪**：正在配对 HomeKit
- **配对完成**：LED 用作开关指示灯（灯亮表示开，灯灭表示关）

| 引脚      | 功能           | 说明                 |
|-----------|----------------|----------------------|
| GPIO4     | 灯光控制       | 低电平触发开启       |
| GPIO0     | 物理开关按钮   | 短按开关/长按重置    |
| GPIO32    | 状态指示 LED   | 显示 HomeKit 状态    |

## 主要依赖

- [HomeSpan](https://github.com/HomeSpan/HomeSpan)
- [EasyButton](https://github.com/evert-arias/EasyButton)

## 许可证

本项目采用 Apache License 2.0，详见 LICENSE 文件。
