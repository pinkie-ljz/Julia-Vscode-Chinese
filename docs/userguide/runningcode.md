# 运行代码

扩展提供了多种运行 Julia 代码的方法。本节将描述所有这些选项，除了如何在调试器中运行代码，相关内容在文档的其他部分中讨论。

## 运行 Julia 文件

默认情况下，VS Code 命令 `Run: Start Without Debugging` (Ctrl+F5) 会启动一个新的 Julia 实例并运行当前打开的 Julia 文件。该命令会自动为此 Julia 进程创建一个新的 VS Code 终端。

> [!note]
> 通过此命令启动的 Julia 实例与扩展支持的 Julia REPL 完全独立。

您可以通过创建 [启动配置](https://code.visualstudio.com/docs/editor/debugging#_launch-configurations) 来轻松自定义 `Run: Start Without Debugging` 的行为。在许多情况下，运行当前打开的文件并不理想，而是将工作区中的某个文件配置为项目的主要入口点，在您按 Ctrl+F5 时运行该文件。

其他自定义选项包括 _自定义工作目录_、_命令行参数_ 或 _特定的 Julia 环境_（与 VS Code 窗口中的活动 Julia 环境不同）。启动配置还允许您配置更复杂的执行场景，在这些场景中，通过 [复合启动配置](https://code.visualstudio.com/docs/editor/debugging#_compound-launch-configurations) 同时启动多个 Julia 和非 Julia 脚本。

Julia 扩展本身支持以下启动配置属性：

- `program`: 指向 .jl 文件的路径。这是在使用此启动配置时将要运行的 Julia 文件。如果未指定此属性，默认使用编辑器中当前打开的 Julia 文件。
- `cwd`: 指向文件夹的路径。据此配置启动的 Julia 进程将使用该路径作为初始工作目录。如果未指定此属性，默认使用在 VS Code 中打开的根工作文件夹。
- `juliaEnv`: 指向 Julia 项目的路径。Julia 进程将使用此 Julia 项目作为活动项目启动。如果未指定此属性，默认使用 VS Code 窗口中当前活动的 Julia 环境。
- `args`: 命令行参数的数组。在此列表中指定的值将作为命令行参数传递给启动的 Julia 进程，并可以通过 Julia 中的 `Base.ARGS` 变量访问。如果未指定此属性，则不会将任何命令行参数传递给 Julia 实例。

## Julia REPL

Julia 扩展在 VS Code 内提供了一个 Julia REPL。您可以使用 `Julia: Start REPL` 命令启动此 REPL。

扩展中的 Julia REPL 与默认的 Julia REPL 相同，但增加了一些额外的集成功能（绘图面板、网格查看器、调试器等），这些功能不是标准 REPL 的一部分。请注意，只有通过 `Julia: Start REPL` 命令启动的 REPL 才具有这些集成功能。如果您在 VS Code 内通过系统 shell 启动 Julia，则不会提供这些集成点。

通过 `Julia: Start REPL` 命令启动的 REPL 将以当前活动工作区的根文件夹作为其工作目录，并将与当前在 VS Code 窗口中活动的 Julia 项目一起启动。

## 在 Julia REPL 中运行代码

您可以使用以下四个命令在 Julia REPL 中运行来自编辑器的代码：
- `Julia: Execute Code in REPL`
- `Julia: Execute Code Cell in REPL` / `Julia: Execute Code Cell in REPL and Move`
- `Julia: Execute File in REPL`
- `Julia: Run File in New Process`

### Julia: Execute Code in REPL

每当在当前活动编辑器中选择了一些 Julia 代码时，此命令将执行所选代码。如果没有选定文本，该命令将识别光标所在的顶层语言构造的范围（模块除外）并执行该代码块。

该命令将与执行的代码关联位置信息，`include` 将正确处理相对路径，宏如 `@__DIR__` 和 `@__FILE__` 将按预期工作。

对于大多数用户而言，这应成为在 REPL 中运行 Julia 代码的默认命令。

### Julia: Execute Code Cell in REPL

该扩展支持通过特殊格式的注释（`##` 或 `# %%`）在标准 Julia 文件中标记代码单元。`##` 或 `# %%` 中的一种注释必须出现在行首，并可以后跟文本。此命令将识别光标在活动编辑器中当前所在的代码单元，然后执行该单元中的代码。如果当前文件中未使用代码单元，它将执行整个文件。

代码单元分隔符可以通过用户设置 `julia.cellDelimiters` 指定为正则表达式。默认值为 `["^##(?!#)", "^#(\\s?)%%", "^#-"]`。

此命令使用与 `Julia: Execute Code Block` 命令相同的代码执行技术。包含语句、位置信息等都按预期工作，也就是使用此命令运行的。

>[!note]
> `Julia: Execute Code Block` 命令在笔者当前的 Julia 扩展中没有找到，应该已经取消了。
### Julia: Execute File in REPL

此命令在 Julia REPL 中运行当前活动文件的全部内容。它使用与 `Julia: Execute Code Block` 命令相同的代码执行技术。包含语句、位置信息等都按预期工作，也就是使用此命令运行的。

### Julia: Run File in New Process

有时希望在新进程中运行代码（例如，如果您想确保没有先前运行的代码状态干扰），因此此命令将启动一个新的 Julia 进程并在其中运行活动文件。
