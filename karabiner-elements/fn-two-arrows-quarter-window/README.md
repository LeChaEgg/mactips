# Karabiner-Elements: Fn + 双方向键做 1/4 窗口管理

## 背景
四分屏管理最常用的就是左上、右上、左下、右下四个位置。这个 tip 用 `Fn + 两个方向键` 直接映射到一组低冲突快捷键（`⌥⌃⌘ + 1/2/3/4`），直觉且高效。

## 使用前提
- 已安装 Karabiner-Elements
- 已安装支持窗口管理快捷键的软件（如 Raycast、Moom、Rectangle Pro、Hammerspoon）
- 窗口管理软件中可自定义 `⌥⌃⌘ + 1/2/3/4`

## 如何使用
1. 将 `fn-two-arrows-quarter-window.json` 的规则加入 `~/.config/karabiner/karabiner.json` 的 `profiles[].complex_modifications.rules`
2. 在 Karabiner-Elements 启用该规则
3. 在窗口管理软件中绑定：
- `⌥⌃⌘ + 1` -> 左上
- `⌥⌃⌘ + 2` -> 右上
- `⌥⌃⌘ + 3` -> 左下
- `⌥⌃⌘ + 4` -> 右下

对应手势：
- `Fn + ↑ + ←` -> 左上
- `Fn + ↑ + →` -> 右上
- `Fn + ↓ + ←` -> 左下
- `Fn + ↓ + →` -> 右下
