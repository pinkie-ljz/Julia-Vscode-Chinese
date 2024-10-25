# Julia Markdown 文档

该扩展支持 Weave Markdown 文档，文件扩展名为 `.jmd`。所有 Julia 代码评估的快捷键和命令都应正常工作，但单元格应定义为围栏的 Julia 代码块（通常的 `##`/`# %%` 分隔符在这里没有意义）。

使用 `Julia Weave: Open Preview` 命令可以将当前文件编织为临时 HTML 文档，然后在编辑器中显示。`Julia Weave: Save to File...` 允许您选择输出格式，并将编织的文档保存到源文件旁边。
