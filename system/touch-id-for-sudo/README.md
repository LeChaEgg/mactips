# macOS: 用 Touch ID 启用 sudo（Sonoma 14+ 持久配置）

## 背景
新款 MacBook 将 Touch ID 与电源键集成后，在授权场景里体验很好。过去常见做法是直接编辑 `/etc/pam.d/sudo`，但系统升级后该文件可能被覆盖，需要重复修改。

从 macOS Sonoma 14.0 开始，官方提供了更稳定的本地个性化方式：使用 `/etc/pam.d/sudo_local`，避免升级后丢失配置。

## 使用前提
- macOS Sonoma 14.0 或更新版本
- 设备支持并已启用 Touch ID
- 当前用户有管理员权限（可执行 `sudo`）

## 如何使用
1. 打开终端，执行：

```bash
sudo cp /etc/pam.d/sudo_local.template /etc/pam.d/sudo_local
```

2. 继续执行：

```bash
sudo nano /etc/pam.d/sudo_local
```

3. 在打开的文件中，找到最后一行 `#auth       sufficient     pam_tid.so`，去掉最前面的 `#`
4. 保存并退出（nano 中按 `Ctrl + O` 回车保存，再按 `Ctrl + X` 退出）
5. 重新打开一个终端窗口，执行任意 `sudo` 命令验证是否会触发 Touch ID

完成后，这个配置会作为本地个性化设置保留，后续系统升级通常不需要再重复改 `sudo` 主配置文件。
