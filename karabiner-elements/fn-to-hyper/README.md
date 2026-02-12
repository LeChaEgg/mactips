# Karabiner-Elements: Fn 映射为 Hyper 组合键

## 背景
很多效率工具会使用 Hyper（通常是 `⌘⌃⌥⇧` 或其子集）作为全局快捷键前缀，因为冲突概率低。这个 tip 把 `Fn + 任意常用键` 映射成 `⌥⌃⌘ + 对应键`，可以作为稳定的“第二层快捷键”。

## 使用前提
- 已安装 Karabiner-Elements
- 已授予 Karabiner-Elements 必要权限（Input Monitoring 等）
- 你使用的其他软件（如 Raycast、Hammerspoon、Keyboard Maestro）支持自定义快捷键

## 如何使用
1. 打开 `~/.config/karabiner/karabiner.json`
2. 在 `profiles[].complex_modifications.rules` 中新增一个规则，并将 `fn-to-hyper.json` 的 `manipulators` 粘贴进去
3. 在 Karabiner-Elements 中启用该规则
4. 到你的效率工具里绑定快捷键，例如把 `⌥⌃⌘ + J/K` 绑定到常用动作

说明：
- 当前规则包含数字区、字母区、常用符号、方向键和回车键
- 若你希望加入 `shift` 形成四键 Hyper，可把每个 `modifiers` 增加 `left_shift`
