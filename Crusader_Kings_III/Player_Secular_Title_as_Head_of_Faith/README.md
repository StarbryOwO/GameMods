# Player_Secular_Title_as_Head_of_Faith

**Author / 作者:** StarbryOwO  
**Mod Version / 模组版本:** 1.0.0  
**Tested Game Version / 测试游戏版本:** Crusader Kings III 1.19.0.6 (Scribe)

---

# 中文说明

## 模组功能

当真人玩家角色同时担任信仰领袖时，本模组让角色继续使用游戏原版对应的世俗称谓，而不是“教宗”“牧首”“哈里发”等宗教领袖称谓。

例如，满足原版条件的罗马帝国统治者可以继续显示“奥古斯都／奥古斯塔”等世俗称谓。

- 只改变真人玩家信仰领袖的称谓显示；
- AI 信仰领袖，包括 AI 世俗信仰领袖，继续使用原版宗教称谓；
- 非信仰领袖玩家不受影响；
- 不修改信仰领袖机制、政体、头衔归属、继承、AI 行为或游戏数值；
- 不主动授予“奥古斯都”等称谓，角色仍须满足原版的头衔、等级、政体等条件；
- 不修改任何 CK3 原版文件。

## 安装教程

GitHub 下载内容是模组文件夹的 ZIP 压缩包。不要把 `.zip` 文件直接放进 CK3 的 `mod` 目录；启动器不会把它当作可用的本地模组。

### 第一步：解压压缩包

右键下载的 ZIP 文件并选择“全部解压”，或使用 7-Zip、WinRAR 等工具解压。

解压后应得到以下模组文件夹：

```text
Player_Secular_Title_as_Head_of_Faith
```

打开该文件夹后，应能直接看到 `descriptor.mod`、`common` 和 `README.md`。如果解压软件额外创建了一层同名文件夹，请使用真正包含 `descriptor.mod` 的内层文件夹，不要保留重复嵌套。

### 第二步：移动解压后的模组文件夹

将解压得到的整个 `Player_Secular_Title_as_Head_of_Faith` 文件夹放入：

```text
Documents\Paradox Interactive\Crusader Kings III\mod
```

常见 Windows 路径为：

```text
C:\Users\你的用户名\Documents\Paradox Interactive\Crusader Kings III\mod
```

如果“文档”位于 OneDrive 或其他磁盘，请使用 CK3 实际用户数据目录。

最终结构应为：

```text
Crusader Kings III
└─ mod
   ├─ Player_Secular_Title_as_Head_of_Faith.mod
   └─ Player_Secular_Title_as_Head_of_Faith
      ├─ descriptor.mod
      ├─ common
      │  ├─ flavorization
      │  └─ on_action
      └─ README.md
```

不要把 ZIP 本身放入该目录，也不要形成重复嵌套结构：

```text
mod\Player_Secular_Title_as_Head_of_Faith\Player_Secular_Title_as_Head_of_Faith\...
```

### 第三步：准备启动器描述文件

复制模组文件夹内的 `descriptor.mod` 到上一层 `mod` 目录，并将复制出来的文件重命名为：

```text
Player_Secular_Title_as_Head_of_Faith.mod
```

保留模组文件夹内原来的 `descriptor.mod`。外部 `.mod` 文件应正确指向解压后的模组文件夹，例如：

```text
path="mod/Player_Secular_Title_as_Head_of_Faith"
```

也可以使用指向该文件夹的有效绝对路径。

### 第四步：在启动器中启用

在 Paradox Launcher 的播放集（Playsets）中添加并启用 **Player Secular Title as Head of Faith**。修改或更新模组后，应完全退出游戏再重新启动；flavorization 不能在运行中的游戏里可靠热更新。

## 使用方法

本模组不需要额外决议、事件按钮或游戏规则。启用后可以直接读取已有存档。

- 真人玩家兼任信仰领袖时，使用原版世俗 holder 称谓；
- AI 信仰领袖继续使用原版宗教领袖称谓；
- 多人模式下所有参与者应使用相同模组版本和加载顺序。

## 实现与引擎限制

CK3 1.19.0.6 的 flavorization 结构不能直接使用 `is_ai` 条件，但支持一个角色 `flag` 条件。

本模组通过追加式 on-action 给 AI 信仰领袖维护专用 flag，并用模组条目替换当前版本的三个原版 `special = head_of_faith` 入口：只有带 AI flag 的角色能够命中宗教领袖称谓；真人玩家不带该 flag，因此会回落到未经修改的原版 `special = holder` 世俗称谓规则。

标记会在退出大厅读取游戏后统一刷新，也会在头衔转移和季度可玩角色脉冲时维护。若真人信仰领袖在正在运行的多人游戏中断线并立即转为 AI，该角色可能暂时保留世俗显示，直到下一次季度刷新；重新经过大厅读取存档也会立即规范标记。该限制仅涉及显示，不影响任何机制或数值。

## 兼容性

可能冲突的模组包括：

- 覆盖 `common/flavorization` 中 `head_of_faith_male`、`head_of_faith_female` 或 `head_of_faith_pope` 的模组；
- 修改信仰领袖称谓的模组；
- 修改皇帝、霸主、奥古斯都或其他 holder 称谓的模组；
- 大型全面改造模组。

CK3 更新后，应重新检查当前版本的原版 flavorization 文档和上述三个信仰领袖入口。

---

# English Instructions

## What This Mod Does

When a human-controlled ruler is also a head of faith, this mod keeps the ruler's normal vanilla secular holder title instead of displaying a religious-head title such as Pope, Patriarch, or Caliph.

For example, a Roman imperial ruler who meets the normal vanilla requirements can continue to display an Augustus/Augusta-style secular title.

- Only the displayed title of human-controlled heads of faith is changed.
- AI heads of faith, including AI secular heads of faith, retain their vanilla religious titles.
- Players who are not heads of faith are unaffected.
- Head-of-faith mechanics, government, title ownership, succession, AI behavior, and game values are unchanged.
- The mod does not grant titles such as Augustus; the character must still meet the relevant vanilla title, tier, government, and other requirements.
- No vanilla CK3 file is modified.

## Installation Guide

The GitHub download is a ZIP archive containing the complete mod folder. Do not place the `.zip` file itself in CK3's `mod` directory; the launcher will not treat it as an installed local mod.

### Step 1: Extract the Archive

Extract the downloaded ZIP with Windows, 7-Zip, WinRAR, or another archive tool.

After extraction, the actual mod folder must be named:

```text
Player_Secular_Title_as_Head_of_Faith
```

Opening that folder should immediately show `descriptor.mod`, `common`, and `README.md`. If the extraction tool creates an additional outer folder, use the inner folder that directly contains `descriptor.mod`; do not keep a duplicated nested structure.

### Step 2: Move the Extracted Mod Folder

Move the entire extracted `Player_Secular_Title_as_Head_of_Faith` folder into:

```text
Documents\Paradox Interactive\Crusader Kings III\mod
```

The final structure should be:

```text
Crusader Kings III
└─ mod
   ├─ Player_Secular_Title_as_Head_of_Faith.mod
   └─ Player_Secular_Title_as_Head_of_Faith
      ├─ descriptor.mod
      ├─ common
      │  ├─ flavorization
      │  └─ on_action
      └─ README.md
```

Do not copy the ZIP itself into this directory and do not create an extra nested folder.

### Step 3: Create the Launcher Descriptor

Copy `descriptor.mod` from inside the mod folder to the parent `mod` directory. Keep the original file inside the mod folder, and rename the copied file to `Player_Secular_Title_as_Head_of_Faith.mod`.

The external file must contain a valid path, for example:

```text
path="mod/Player_Secular_Title_as_Head_of_Faith"
```

A valid absolute path to the same extracted folder may also be used.

### Step 4: Enable the Mod

Add and enable **Player Secular Title as Head of Faith** in a Paradox Launcher playset. Fully restart the game after installing or updating the mod; flavorization data is not reliably hot-reloaded.

## Usage and Existing Saves

No decision, event button, or game rule is required. Existing saves are supported.

- Human players who are heads of faith use their normal vanilla secular holder titles.
- AI heads of faith retain their vanilla religious-head titles.
- All multiplayer participants should use the same mod version and load order.

## Implementation and Engine Limitation

CK3 1.19.0.6 flavorization cannot directly evaluate `is_ai`, but its documented schema supports one character `flag` condition.

The mod uses append-only on-actions to maintain an AI-only head-of-faith flag. It replaces the three vanilla `special = head_of_faith` entry points in this game version so that religious-head titles require that AI flag. Human players never receive the flag and therefore fall through to the unmodified vanilla `special = holder` secular rules.

Flags are normalized after the lobby and refreshed on title transfers and the quarterly playable-character pulse. If a human head of faith disconnects during a running multiplayer session and immediately becomes AI, the former player may temporarily retain the secular display until the next quarterly refresh. Reloading through the lobby also normalizes the state. This limitation affects display only.

## Compatibility

Potential conflicts include mods that:

- override `head_of_faith_male`, `head_of_faith_female`, or `head_of_faith_pope` in `common/flavorization`;
- change head-of-faith titles;
- change emperor, hegemon, Augustus, or other holder titles;
- perform a major total conversion.

After a CK3 update, review the current vanilla flavorization documentation and the three head-of-faith entry points again.
