# Karabiner-Elements: 精准输入法切换（Stack Flip 方案）

## 背景
在 macOS 里，输入法状态存在“系统层”和“应用层”两个层面。`select_input_source` 这类 API 方式有时只能让系统顶栏图标切换成功，但当前活跃输入上下文不一定立即同步。

这在 Raycast、Chrome 地址栏、部分 Electron 浮动窗口里更容易出现：看起来输入法已经切换，实际输入仍停留在英文。

## 解决思路
这个方案不只做 API 切换，而是做一次 Stack Flip：
1. 先把输入法瞬间切到目标语言
2. 再瞬间切回英文，改写“上一个输入源”历史
3. 插入一个极短延迟（`vk_none` + `50ms`），等待 macOS 写入输入法历史栈
4. 最后触发系统原生“切换到上一个输入源”快捷键

这样最终切换由系统原生机制完成，当前活跃窗口的输入上下文会被更强力地刷新和同步，稳定性明显高于纯 API 切换。

## 使用前提
- 已安装 [Karabiner-Elements](https://karabiner-elements.pqrs.org/)
- macOS 中已添加并启用目标输入法（英文、简体中文、日文、希腊文）
- 允许 Karabiner-Elements 所需系统权限（Input Monitoring 等）
- 在 `系统设置 -> 键盘 -> 键盘快捷键 -> 输入源` 中，先配置好 `切换到上一个输入源`
- 当前 JSON 使用的是 `Control + Space`（`"modifiers": ["left_control"] + "spacebar"`）

如果你的系统把“切换到上一个输入源”设成 `Option + Space`，请把 JSON 里对应两处 `"left_control"` 改为 `"left_option"`。

## 如何使用
1. 打开 Karabiner-Elements，进入 `Modifications -> Complex Modifications`
2. 点击 `Add your own rule`，把 `switch-input-sources.json` 的完整内容粘贴进去并保存
3. 回到 `Complex Modifications` 列表，启用这条规则

默认快捷键：
- `Right Command + E` 切到英文（直接切换）
- `Right Command + C` 切到简体中文（Stack Flip）
- `Right Command + J` 切到日文（Stack Flip）
- `Right Command + G` 切到希腊文（直接切换）

如果你的输入法 `input_source_id` 不同，可先用 Karabiner-EventViewer 查看并替换 JSON 中对应字段。
