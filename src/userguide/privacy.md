# 隐私

您可以通过向开发团队发送使用统计数据和异常信息来帮助改善 Julia VS Code 扩展。默认情况下，不收集遥测和崩溃报告数据，用户必须选择加入才能发送其数据。

## 选择加入政策

默认情况下，`julia.enableTelemetry` 和 `julia.enableCrashReporter` 的设置都为 `null`。在 `null` 设置下，不会向开发团队发送任何数据。用户界面会发送提示，询问用户是否同意启用遥测和崩溃报告的设置。如果不选择加入，您的数据不会发送给开发团队。

## 收集数据

如果将 `julia.enableTelemetry` 设置为 `true`，则匿名的、非识别性使用和错误数据将发送给开发团队。

当 `julia.enableCrashReporter` 设置为 `true` 时，扩展中的错误堆栈跟踪将发送给开发团队。这些堆栈跟踪可能包含识别信息，例如文件名。

这些信息通过 Azure Application Insights 收集并发送。

## 禁用遥测

要禁用遥测并不报告任何使用数据或崩溃报告，请将 `julia.enableTelemetry` 和 `julia.enableCrashReporter` 设置为 `false`。

## ## 使用收集的数据

收集的数据用于改善 Julia VS Code 扩展。我们不会出售这些信息。我们有时可能会发布匿名统计数据（例如用户数量等）。
