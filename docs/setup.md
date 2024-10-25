# 设置

要使 `Julia `扩展在 `VS Code` 中正常工作，涉及两个步骤：
1) 安装 `VS Code`，然后，
2) 安装 `Julia `扩展。

在极少数情况下，你还需要配置扩展以找到你的 `Julia` 安装路径。

## 安装 VS Code

- 直接前往 [VS Code](https://code.visualstudio.com/) 官方主页。
- 根据你的平台，按照安装说明进行操作。

完成此步骤后，你应该能够启动 `VS Code`。

## 安装 Julia 扩展

- 首先，启动 VS Code。
- 在 VS Code 内，可以通过执行 `View: Show Extensions` 命令（点击“视图”->“命令面板...”），或通过点击 VS Code 窗口左侧的扩展图标来打开扩展视图。
- 在扩展视图中，简单地在市场搜索框中搜索 `julia`，然后选择` Julia` 扩展并点击安装按钮。
- 在此步骤之后，你可能需要重新启动 VS Code。

## 配置 Julia 扩展

- 如果你在 Mac 或 Windows 系统上将 Julia 安装在标准位置，或者 Julia 的二进制文件位于你的 `PATH` 中，Julia VS Code 扩展应自动找到你的 Julia 安装，你不需要进行任何配置。

- 如果扩展无法自动找到你的 Julia 安装，或者你希望使用不同的 Julia 安装版本，
	- 你可以将 `julia.executablePath` 设置为扩展应该使用的 Julia 可执行文件的完整路径。在这种情况下，扩展将始终使用该 Julia 版本。
	- 要编辑配置设置，
	    - 执行 `Preferences: Open User Settings` 命令（你也可以通过菜单“文件”->“首选项”->“设置”来访问它），
	    - 然后确保你的用户设置中包含 `julia.executablePath` 选项。

字符串的格式应遵循平台的具体规范，请注意，在 JSON 中反斜杠 `\` 是转义字符，因此你需要在 Windows 上使用 `\\` 作为路径分隔符。
