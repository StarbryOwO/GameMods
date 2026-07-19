# Player Secular Title as Head of Faith

**Author / 作者:** StarbryOwO  
**Mod Version / 模组版本:** 1.0.0  
**Tested Game Version / 测试游戏版本:** Crusader Kings III 1.19.0.6 (Scribe)

---

# 中文说明

## 模组功能

当玩家角色兼任信仰领袖时，本模组会让玩家继续显示游戏原版的世俗称谓，而不是“教宗”“牧首”“哈里发”等宗教领袖称谓。

例如，满足原版条件的罗马帝国统治者可以继续显示“奥古斯都／奥古斯塔”等世俗称谓。

- 只影响真人玩家角色；
- AI 信仰领袖，包括 AI 世俗信仰领袖，仍使用原版宗教称谓；
- 不担任信仰领袖的玩家角色不会发生可见变化；
- 不修改信仰领袖机制、政体、头衔归属、继承、AI 行为或任何游戏数值；
- 本模组仅修改角色称谓的显示规则（flavorization）。

## 安装教程

本压缩包以“完整模组文件夹”的形式发布。请按照以下步骤手动安装。

### 第一步：解压模组文件夹

将下载的压缩包解压。

解压后应得到一个名为：

```text
PlayerSecularHOF
```

的模组文件夹。

### 第二步：把模组文件夹放入 CK3 的 mod 目录

将整个 `PlayerSecularHOF` 文件夹移动到：

```text
文档\Paradox Interactive\Crusader Kings III\mod
```

Windows 的完整路径通常为：

```text
C:\Users\你的用户名\Documents\Paradox Interactive\Crusader Kings III\mod
```

如果你的“文档”文件夹由 OneDrive 管理，路径可能是：

```text
C:\Users\你的用户名\OneDrive\Documents\Paradox Interactive\Crusader Kings III\mod
```

放置完成后，应当看到：

```text
Crusader Kings III
└── mod
    └── PlayerSecularHOF
        ├── descriptor.mod
        ├── common
        ├── events
        ├── tools
        └── README.md
```

实际文件夹内容可能因版本不同而略有变化，但 `descriptor.mod` 必须位于 `PlayerSecularHOF` 文件夹的最外层。

### 第三步：复制 descriptor.mod 到上一级 mod 目录

进入：

```text
文档\Paradox Interactive\Crusader Kings III\mod\PlayerSecularHOF
```

找到：

```text
descriptor.mod
```

将这个文件**复制**一份，再把复制出来的文件拖到上一级 `mod` 文件夹：

```text
文档\Paradox Interactive\Crusader Kings III\mod
```

注意：

- 请使用“复制”，不要直接移动原文件；
- `PlayerSecularHOF` 文件夹内必须继续保留原始的 `descriptor.mod`；
- 上一级 `mod` 目录也需要一份用于让启动器识别模组的 `.mod` 文件。

### 第四步：重命名复制出来的文件

将刚刚复制到上一级 `mod` 目录的：

```text
descriptor.mod
```

重命名为：

```text
PlayerSecularHOF.mod
```

最终目录结构应为：

```text
Crusader Kings III
└── mod
    ├── PlayerSecularHOF.mod
    └── PlayerSecularHOF
        ├── descriptor.mod
        ├── common
        ├── events
        ├── tools
        └── README.md
```

不要形成下面这种重复嵌套结构：

```text
mod\PlayerSecularHOF\PlayerSecularHOF\...
```

正确结构必须是：

```text
mod\PlayerSecularHOF\descriptor.mod
```

以及：

```text
mod\PlayerSecularHOF.mod
```

### 第五步：检查外部 .mod 文件的路径

使用记事本或其他纯文本编辑器打开：

```text
PlayerSecularHOF.mod
```

确认文件中包含以下路径：

```text
path="mod/PlayerSecularHOF"
```

如果没有这一行，请在文件末尾添加并保存。

不要把路径写成压缩包路径，也不要写成两层重复文件夹。

### 第六步：在 Paradox Launcher 中启用

1. 启动 Paradox Launcher；
2. 进入“播放集（Playsets）”；
3. 选择现有播放集，或创建一个新播放集；
4. 点击“添加更多模组”；
5. 找到 **Player Secular Title as Head of Faith**；
6. 将模组添加到播放集并启用；
7. 使用该播放集启动游戏。

如果启动器中没有显示模组：

1. 完全关闭游戏和 Paradox Launcher；
2. 再次检查上述目录结构；
3. 确认 Windows 没有把文件实际保存成 `PlayerSecularHOF.mod.txt`；
4. 重新打开启动器。

## 使用方法

本模组不需要额外决议、事件按钮或游戏设置。

启用后进入游戏即可自动生效。

- 玩家兼任信仰领袖时，会使用正常的原版世俗称谓；
- 符合原版条件的罗马帝国玩家可以显示“奥古斯都／奥古斯塔”等称谓；
- AI 信仰领袖仍然使用原版宗教领袖称谓。

本模组不会主动赋予“奥古斯都”等称谓。玩家仍然需要满足 CK3 原版对应称谓的文化、头衔、政体或决议条件。

## 已有存档与多人游戏

本模组设计为可以用于已有存档。

玩家标记会在读取游戏后应用，并通过游戏的可玩角色周期事件，在继承或切换角色后进行刷新。

- 单人游戏：只影响当前真人玩家；
- 多人游戏：影响所有由真人控制的玩家角色；
- 多人游戏的所有参与者应使用相同版本和相同加载顺序的模组。

## 引擎限制

CK3 1.19.0.6 的 flavorization 规则不能直接判断 `is_ai`，其可用结构只提供单一角色 `flag` 条件。

因此，本模组通过 on-action 维护一个“真人玩家兼任信仰领袖”的角色标记，再让这些玩家使用对应的世俗称谓规则。

如果真人信仰领袖在游戏运行过程中因为调试切换角色或多人玩家断线而突然变成 AI，该角色可能暂时继续显示世俗称谓，直到下一次季度可玩角色刷新。重新经过大厅读取存档也会清除此状态。

该限制只影响称谓显示，不影响任何机制或数值。

## 兼容性

本模组将原版 `special = holder` 的部分 flavorization 规则镜像到 `special = head_of_faith` 选择组，并只对带有本模组玩家标记的角色提高优先级。

可能发生冲突的模组包括：

- 大幅修改 `common/flavorization` 的模组；
- 修改信仰领袖称谓的模组；
- 修改皇帝、国王、奥古斯都等角色称谓的模组；
- 大型全面改造模组。

CK3 更新后，模组作者可以在 PowerShell 中运行：

```powershell
.\tools\generate_mirrors.ps1
```

然后根据新版本的原版 flavorization 文档检查生成文件。

本模组不会修改任何 CK3 原版文件。

---

# English Instructions

## What This Mod Does

When a human-controlled ruler is also a head of faith, this mod keeps the ruler's normal vanilla secular title instead of displaying a religious-head title such as Pope, Patriarch, Caliph, or a similar title.

For example, a Roman imperial ruler who meets the normal vanilla requirements can continue to display an Augustus/Augusta-style secular title.

- Only human-controlled player characters are affected.
- AI heads of faith, including AI secular heads of faith, retain their vanilla religious titles.
- Players who are not heads of faith are visually unchanged.
- The mod does not change head-of-faith mechanics, government, title ownership, succession, AI behavior, or game values.
- The mod changes display flavorization only.

## Installation Guide

This archive is distributed as a complete mod folder. Install it manually by following the steps below.

### Step 1: Extract the Mod Folder

Extract the downloaded archive.

After extraction, you should have a folder named:

```text
PlayerSecularHOF
```

### Step 2: Place the Mod Folder in the CK3 mod Directory

Move the entire `PlayerSecularHOF` folder into:

```text
Documents\Paradox Interactive\Crusader Kings III\mod
```

The usual full Windows path is:

```text
C:\Users\YourUserName\Documents\Paradox Interactive\Crusader Kings III\mod
```

If OneDrive manages your Documents folder, the path may instead be:

```text
C:\Users\YourUserName\OneDrive\Documents\Paradox Interactive\Crusader Kings III\mod
```

After this step, the structure should look similar to:

```text
Crusader Kings III
└── mod
    └── PlayerSecularHOF
        ├── descriptor.mod
        ├── common
        ├── events
        ├── tools
        └── README.md
```

The exact contents may vary between versions, but `descriptor.mod` must be located directly inside the outer `PlayerSecularHOF` folder.

### Step 3: Copy descriptor.mod to the Parent mod Directory

Open:

```text
Documents\Paradox Interactive\Crusader Kings III\mod\PlayerSecularHOF
```

Find:

```text
descriptor.mod
```

Make a **copy** of this file and drag or paste the copied file into the parent `mod` directory:

```text
Documents\Paradox Interactive\Crusader Kings III\mod
```

Important:

- Copy the file; do not remove the original.
- The original `descriptor.mod` must remain inside the `PlayerSecularHOF` folder.
- The parent `mod` directory also needs a separate `.mod` file so that Paradox Launcher can detect the mod.

### Step 4: Rename the Copied File

Rename the copied file in the parent `mod` directory from:

```text
descriptor.mod
```

to:

```text
PlayerSecularHOF.mod
```

The final directory structure must look like this:

```text
Crusader Kings III
└── mod
    ├── PlayerSecularHOF.mod
    └── PlayerSecularHOF
        ├── descriptor.mod
        ├── common
        ├── events
        ├── tools
        └── README.md
```

Do not create an extra nested folder such as:

```text
mod\PlayerSecularHOF\PlayerSecularHOF\...
```

The correct paths are:

```text
mod\PlayerSecularHOF\descriptor.mod
```

and:

```text
mod\PlayerSecularHOF.mod
```

### Step 5: Verify the Path in the External .mod File

Open the following file with Notepad or another plain-text editor:

```text
PlayerSecularHOF.mod
```

Make sure it contains:

```text
path="mod/PlayerSecularHOF"
```

If that line is missing, add it at the end of the file and save it.

Do not use the archive path, and do not use a duplicated two-folder path.

### Step 6: Enable the Mod in Paradox Launcher

1. Open Paradox Launcher.
2. Go to **Playsets**.
3. Select an existing playset or create a new one.
4. Click **Add More Mods**.
5. Find **Player Secular Title as Head of Faith**.
6. Add it to the playset and enable it.
7. Start Crusader Kings III with that playset.

If the mod does not appear in the launcher:

1. Fully close the game and Paradox Launcher.
2. Check the directory structure again.
3. Make sure Windows did not save the file as `PlayerSecularHOF.mod.txt`.
4. Reopen the launcher.

## How to Use

The mod does not require any additional decision, event button, or game rule.

Enable it and load the game; the effect is automatic.

- Human players who are heads of faith use their normal vanilla secular holder titles.
- Eligible Roman imperial player characters can display titles such as Augustus or Augusta.
- AI heads of faith continue to use their vanilla religious-head titles.

The mod does not grant titles such as Augustus by itself. The character must still meet the relevant vanilla culture, title, government, or decision requirements.

## Existing Saves and Multiplayer

The mod is intended to work with existing saves.

The player marker is applied after loading a game and is refreshed by the quarterly playable-character pulse after succession or character switching.

- Single player: only the current human player is affected.
- Multiplayer: all human-controlled player characters are affected.
- All multiplayer participants should use the same mod version and load order.

## Engine Limitation

CK3 1.19.0.6 flavorization cannot directly evaluate `is_ai`; its documented schema only provides a single character `flag` condition.

The mod therefore maintains a human-player/head-of-faith marker through on-actions and uses that marker to select the appropriate secular title rules.

If a human head of faith becomes AI during a running session because of a debug character switch or a multiplayer disconnect, that former player may temporarily retain the secular display until the next quarterly playable-character pulse. Reloading the save through the lobby also clears the state.

This limitation affects display only. It does not affect mechanics or game values.

## Compatibility

The mod mirrors selected vanilla `special = holder` flavorization rules into the `special = head_of_faith` selection group and raises their priority only for characters carrying the mod's player marker.

Potential conflicts include mods that:

- substantially replace `common/flavorization`;
- change head-of-faith titles;
- change emperor, king, Augustus, or other holder titles;
- perform a major total conversion.

After a CK3 update, the mod author can run the following command from PowerShell:

```powershell
.\tools\generate_mirrors.ps1
```

The generated file should then be reviewed against the new vanilla flavorization documentation.

No vanilla game file is modified.
