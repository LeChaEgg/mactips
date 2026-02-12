# Karabiner-Elements: 精准输入法切换

## 背景
macOS 默认的输入法切换通常是“循环切换”，当你同时启用多种输入法时，很容易切错并打断输入节奏。这个 tip 用 Karabiner-Elements 把特定快捷键直接映射到目标语言，实现一次到位的输入法切换。

## 使用前提
- 已安装 [Karabiner-Elements](https://karabiner-elements.pqrs.org/)
- macOS 中已添加并启用目标输入法（英文、简体中文、日文、希腊文）
- 允许 Karabiner-Elements 所需系统权限（Input Monitoring 等）

## 如何使用
1. 打开 Karabiner-Elements，进入 `Modifications -> Complex Modifications`
2. 点击 `Add your own rule`，把 `switch-input-sources.json` 的完整内容粘贴进去并保存
3. 回到 `Complex Modifications` 列表，启用这条规则

默认快捷键：
- `Right Command + E` 切到英文
- `Right Command + C` 切到简体中文
- `Right Command + J` 切到日文
- `Right Command + G` 切到希腊文

如果你的输入法 `input_source_id` 不同，可先用 Karabiner-EventViewer 查看并替换 JSON 中对应字段。
