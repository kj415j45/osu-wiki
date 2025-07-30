# osu! 比赛客户端

**osu! 比赛客户端** 是与 [osu!tourney](/wiki/osu!_tournament_client/osu!tourney) 配合使用的官方客户端，可在直播 osu! 比赛期间提供补充场景和相关信息覆盖层。

在使用客户端时遇到问题的用户可以[在 GitHub 上创建问题](https://github.com/ppy/osu/issues)或向 [tournaments@ppy.sh](mailto:tournaments@ppy.sh) 发送电子邮件。

## 设置

要启动 osu! 比赛客户端，需要为 [osu!(lazer)](/wiki/Client/Release_stream/Lazer) 可执行文件指定启动参数。方法是在桌面上创建一个新的快捷方式，并将其位置设置为 `%LOCALAPPDATA%/osulazer/osu!.exe --tournament`。这将使该特定快捷方式以比赛客户端模式启动 osu!(lazer)。

由于 osu! 比赛客户端只是 osu!tourney 的覆盖层，因此也需要设置 osu!tourney。将 osu!tourney 中的发布流设置为 `Cutting Edge (Experimental)`，并在 osu!tourney 的安装文件夹内创建一个名为 `ipc.txt` 的空文件。之后，按照 [osu!tourney 设置指南](/wiki/osu!_tournament_client/osu!tourney/Setup)进行操作。

打开 osu! 比赛客户端，将会看到此设置界面：

![osu! 比赛客户端设置界面](img/setup-screen.png)

- 确保 `Current IPC source` 与将要使用的 osu!tourney 实例的位置匹配。
- 通过点击 `Change Login` 登录到 osu!(lazer)。
- 使用下拉菜单设置正确的游戏模式。
- 更改高度以匹配 osu!tourney 的 `tournament.cfg` 文件中设置的 `Height` 值。

## 管理比赛

[osu!(lazer)](/wiki/Client/Release_stream/Lazer) 的比赛配置存储在 `%APPDATA%/osu/tournaments` 中。客户端首次启动时，会在此文件夹内创建一个名为 `default` 的目录。用户可以维护多个比赛配置，并根据需要在它们之间切换以应用适当的自定义设置。

要创建新的比赛配置，请在 `tournaments` 目录中创建一个以比赛名称命名的新目录。

在比赛配置内，可以提供必要的资源来显示地图池的国旗、视频和模组图标。每个资源类别都有自己的文件夹：

- your-tournament
  - Flags
  - Mods
  - Videos

## 自定义

osu! 比赛客户端可以通过提供自定义国旗、模组图标和视频文件进行自定义。这些将根据需要在相应场景中显示。

### 国旗

默认情况下，osu! 比赛客户端提供世界各国的内置国旗。这些可以在团队编辑器中通过其 [ISO 3166 Alpha-2 国家代码](https://www.iso.org/iso-3166-country-codes.html)进行引用。

对于自定义国旗，接受 `.jpg` 和 `.png` 文件。国旗图像应至少为 140x94，保持接近此规格的宽高比以获得最佳效果。

国旗必须放置在 `<your-tournament>/Flags` 中。然后可以在团队编辑器中通过文件名（不包含文件扩展名）引用国旗。

### 模组

对于自定义模组图标，接受 `.jpg` 和 `.png` 文件。分辨率可以是任何值，客户端会将其适配到谱面面板中。作为参考，1920x1080 下的谱面面板为 563x60 像素。

模组图标必须放置在 `<your-tournament>/Mods` 中。然后可以在回合编辑器和种子结果编辑器中通过文件名（不包含文件扩展名）引用模组。

### 视频

可以在每个场景的背景中显示循环视频。

注意：客户端使用软件解码来解码视频文件，因此根据使用场景，性能可能会有所不同。

文件必须符合以下规格：

- 16:9 宽高比，例如 1280x720 或 1920x1080
- `mp4`、`m4v` 或 `avi` 文件扩展名
- 视频编解码器：H.264，音频编解码器：无

视频文件必须放置在 `<your-tournament>/Videos` 中，并且需要特定的名称才能正确运行。

| 场景 | 文件 |
| :-- | :-- |
| Schedule | `schedule` |
| TeamIntro | `teamintro` |
| Seeding | `seeding` |
| MapPool | `mappool` |
| Gameplay | `gameplay` |
| Win | `teamwin-red`, `teamwin-blue` |
| Drawings | `main` |
| Showcase | `showcase` |
| Bracket | `ladder` |
