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

### **第一步：进入“文档”文件夹**

打开 Windows 文件资源管理器，点击左侧导航栏中的 **Documents／文档**，然后依次进入：

```text
Paradox Interactive\Crusader Kings III
```

### **第二步：检查并创建 `mod` 文件夹**

检查 `Crusader Kings III` 文件夹中是否存在名为 `mod` 的文件夹。如果没有，请右键空白处，选择“新建 → 文件夹”，并将新文件夹准确命名为：

```text
mod
```

### **第三步：解压模组（不要忘了这一步！！）<=**

下载 `Player_Secular_Title_as_Head_of_Faith_v1.0.0.zip` 后，将压缩包的内容直接解压到刚才确认或创建的 CK3 用户 `mod` 文件夹：

```text
Documents\Paradox Interactive\Crusader Kings III\mod
```

常见 Windows 路径为：

```text
C:\Users\你的用户名\Documents\Paradox Interactive\Crusader Kings III\mod
```

如果“文档”位于 OneDrive 或其他磁盘，请使用 CK3 实际用户数据目录。

解压完成后，目录结构必须是：

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

压缩包已经包含正确的外部 `.mod` 文件和相对路径。**不要再复制、重命名或编辑 `descriptor.mod`。**

不要只把 ZIP 文件留在目录中；必须解压其内容。也不要形成重复嵌套结构：

```text
mod\Player_Secular_Title_as_Head_of_Faith\Player_Secular_Title_as_Head_of_Faith\...
```

### **在启动器中启用**

在 Paradox Launcher 的播放集（Playsets）中添加并启用 **Player Secular Title as Head of Faith**。如果没有出现，确认使用的是 CK3 实际扫描的“文档”目录（可能被 OneDrive 或系统重定向），然后在任务管理器中结束所有 Paradox Launcher 进程并重新打开。修改或更新模组后，应完全退出游戏再重新启动；flavorization 不能在运行中的游戏里可靠热更新。

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

### **Step 1: Open the Documents Folder**

Open Windows File Explorer, click **Documents** in the left navigation pane, and then open:

```text
Paradox Interactive\Crusader Kings III
```

### **Step 2: Check or Create the `mod` Folder**

Check whether the `Crusader Kings III` directory contains a folder named `mod`. If it does not, right-click an empty area, select **New → Folder**, and name the new folder exactly:

```text
mod
```

### **Step 3: Extract the Mod (Do Not Forget This Step!!)**

After downloading `Player_Secular_Title_as_Head_of_Faith_v1.0.0.zip`, extract the contents of the archive directly into the CK3 user `mod` folder that you just confirmed or created:

```text
Documents\Paradox Interactive\Crusader Kings III\mod
```

If Windows or OneDrive redirects the Documents folder, use CK3's actual user-data directory.

After extraction, the structure must be:

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

The archive already contains the correct external `.mod` file and relative path. **Do not copy, rename, or edit `descriptor.mod`.** Do not leave the ZIP itself unextracted in this directory, and do not create an extra nested folder.

### **Enable the Mod**

Add and enable **Player Secular Title as Head of Faith** in a Paradox Launcher playset. If it does not appear, verify that this is the actual Documents directory scanned by CK3 (it may be redirected by OneDrive or Windows), terminate every Paradox Launcher process in Task Manager, and reopen it. Fully restart the game after installing or updating the mod; flavorization data is not reliably hot-reloaded.

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
