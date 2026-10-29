# 艾尔登法环练习工具（中文版）

基于 [veeenu/eldenring-practice-tool](https://github.com/veeenu/eldenring-practice-tool)（johndisandonato 原作，AGPLv3）的中文本地化与实战优化分支，用于离线练习 Boss、速跑路线、弹反帧与位置回溯。

> [!CAUTION]
> **仅限离线单人使用。** 本工具会自动禁用游戏的 EAC（Easy Anti-Cheat）反作弊。**启用后再联机、进 multiplayer、召协助手/召唤入侵者，FromSoftware 可能直接软封或硬封你的账号，后果自负。** 本仓库作者不对任何封号、存档损坏或设备问题负责。
>
> 仅支持正版 Steam 版游戏。盗版、魔改、装过其他 mod 的存档不提供支持。

---

## 下载

去 [Releases](https://github.com/siyuang421-collab/er-practice-tool-cn-rc/releases/latest) 下载最新的 `er-practice-tool-cn-vX.X.X.zip`，解压后按下面步骤跑。

## 前置要求

- Steam 开着（离线模式也行，但 Steam 进程必须在）。
- 游戏是**完全原版、没装任何 mod** 的安装。装过 mod 请先验证游戏文件完整性或重装。
- 杀毒软件（包括 Windows Defender）暂时关了，或者把解压目录加白名单——注入 dll 经常被误报。
- 不要开 RivaTuner / FRAPS 这类叠加层软件（Steam Overlay 例外）。
- 正版游戏。盗版不支持。

## 怎么运行

### 方式一：独立模式（推荐先试）

1. 解压 zip 到任意位置。
2. Steam → 右键 **ELDEN RING** → 管理 → 浏览本地文件，**双击 `eldenring.exe` 启动游戏**（不要从 Steam 库里点开始）。
3. 游戏跑起来后，双击解压目录里的 `jdsd_er_practice_tool.exe`。
4. 工具界面会叠加在游戏上，按 `右 Shift + 0` 显示/隐藏。

### 方式二：安装模式

1. 解压 zip。
2. 把所有文件复制到游戏目录（就是 `eldenring.exe` 所在的那个文件夹）。
3. **双击 `eldenring.exe`** 启动游戏，启动过程中**按住右 Shift 几秒钟**直到工具界面出现。
4. 错过了也没事，游戏目录里双击 `jdsd_er_practice_tool.exe` 一样能加载。
5. 更新时直接覆盖旧文件；卸载时删掉游戏目录里的 `dinput8.dll`。

> [!NOTE]
> 首次运行时如果还没禁 EAC，工具会自动帮你禁，之后需要重启一次游戏和工具。

### Linux / Steam Deck

给游戏加启动参数：

```sh
WINEDLLOVERRIDES="dinput8=n,b" %command%
```

---

## 快捷键速查

| 按键 | 功能 |
|---|---|
| `1` | 无敌 |
| `2` | 专注值不消耗（含战技） |
| `3` | 精力不消耗 |
| `4` | 道具/箭矢不消耗 |
| `5` | 关闭死亡镜头 |
| `6` | 不死 |
| `7` | 一击必杀 |
| `8` | 速度循环（0.5× / 1× / 2× / 5× / 10×） |
| `9` | 加 10000 卢恩 |
| `[` / `]` | 上下微调位置 |
| `h` / `j` / `k` | 读取保存的位置 |
| `右 Shift + h/j/k` | 保存当前位置 |
| `o` | 卢恩弧开关 |
| `p` | 退出重进（quitout） |
| `Ctrl + O` | 存档管理 |
| `Ctrl + U` | 生成物品 |
| `Ctrl + N` | 目标信息 |
| `Ctrl + L` | 冻结动作 |
| `F1` | AI 静止 |
| `F2` | 重力 / 灵马重力开关 |
| `F3` | 显示全部赐福/地标 |
| `F4` | 显示地图 |
| `F5` | 显示角色 |
| `F6` | 稳定位置指示 |
| `F7` / `F8` | 高/低 hitbox |
| `F9` | 武器判定 |
| `右 Shift + 0` | 显示/隐藏工具界面 |
| `L3 + R3`（手柄） | 打开径向菜单 |

详细可调项在 `jdsd_er_practice_tool.toml` 里改。

---

## 中文版本次更新（v1.10.0-RC）

- **位置保存与读取**：支持骑马状态保存、移动、回溯；通过灵马实体句柄动态解析物理模块，老固定地址失效的区域也能存读位置；灵马模块不可用时自动回退到玩家坐标写入。
- **位置微调与重力**：骑马上下微调改用动态灵马物理坐标；长距离回溯时临时关闭重力，位置稳定后自动恢复。
- **跨区域位置回溯**：保存点和当前点不在同一张图时，先走游戏传送流程加载目标地图，再恢复精确坐标和朝向。
- **速度与动画**：修复移动速度、灵马速度、动画速度叠加时骑马状态下的异常；退出工具时自动把动画速度恢复 1.0。
- **物品与复活**：物品搜索支持拼音首字母/全拼；修复托雷特死亡复活仍扣血瓶的问题。
- **生成物品界面重做**：物品名运行时从游戏内存直接读，跟游戏语言一致；按官方分类分组；支持本体/DLC 筛选；支持中文、拼音、ID 搜索；扩大中文字库。
- **退出与重载**：退出时关闭所有补丁，修复退出后无法再次加载的句柄泄漏问题。

完整改动见 [CHANGELOG.md](CHANGELOG.md)。

---

## 致谢

- 原作者 [johndisandonato (veeenu)](https://github.com/veeenu) 与 late Aura Ackermann。
- ViRazY 完成 Linux 支持。
- Soulsmodding 社区提供 Param 定义与 CE 表。
- UI 字体 [Comic Mono](https://github.com/dtinth/comic-mono-font)。

## License

本项目基于 AGPLv3 发布，沿用原仓库协议。修改部分同样以 AGPLv3 公开。详见 [LICENSE](LICENSE)。
