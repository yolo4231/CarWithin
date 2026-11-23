# 源码构建说明

使用 Xcode 打开 TDSCarKit.xcodeproj，选择 TDSCarKit scheme，配置自己的开发团队、Bundle ID 和签名，再构建 iOS 目标。最低部署目标为 iOS 16.0。

源码不包含配件认证身份、私钥、证书或 Apple 签名材料。没有可用身份时应用可编译，但本机 CarPlay 连接需要另行配置有效身份。Tools/generate_project.py 会将本地 App/BundledIdentity 内的文件加入生成的工程，请勿把该目录中的身份材料提交到公开仓库。

发布安装包与源码应对应同一代码版本。第三方许可与来源见 THIRD_PARTY_NOTICES.txt 和 LICENSES。

## GitHub Actions 试验包

推送到 `main` 或 `ae3-pro` 分支后，`Build iOS IPA` 会运行 PXC 模拟测试并构建 arm64 iOS 应用。也可在 Actions 页面手动运行。成功后从对应运行的 Artifacts 下载 `EvoPlay-AE3-Pro-unsigned`，解压得到未签名 IPA。请用自己的工具签名和安装。公开 CI 构建不包含 MFi 配件身份，实际启动本机 CarPlay 仍需有效身份。

在 App 中选择「当前输出 → 极核 AE3 Pro 5 寸」。此模式复用极核 PXC 投屏，IP 独立保存，默认 `192.168.0.1`。H.264 输出尺寸取自仪表媒体协商，最高 30 FPS。已在一台 AE3 Pro 实车确认可以投屏，30 FPS 上限需实车确认。
