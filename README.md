# Ekko Studio 桌面更新测试

这是 Ekko Studio 的**公开测试更新仓库**，用于真实安装包的 A → B 更新验证。正式安装包和正式更新源不使用本仓库。

## 自动上传

在 [EKKOLearnAI/ekko-studio](https://github.com/EKKOLearnAI/ekko-studio/actions/workflows/desktop-update-test.yml) 运行 **Desktop Update Test Build**，选择测试系统/架构和版本。接入自动上传的工作流合并、并配置 `DESKTOP_UPDATE_TEST_TOKEN` 后，验证过的安装包会自动上传到本仓库对应的预发布 Release。

| 测试机器 | 固定更新目录 |
| --- | --- |
| macOS Apple Silicon | `https://github.com/EKKOLearnAI/ekko-studio-update-test/releases/download/update-test-darwin-arm64/` |
| macOS Intel | `https://github.com/EKKOLearnAI/ekko-studio-update-test/releases/download/update-test-darwin-x64/` |
| Windows x64 | `https://github.com/EKKOLearnAI/ekko-studio-update-test/releases/download/update-test-win32-x64/` |

这些地址由工作流自动写入测试包，无需手动填写。对应平台第一次成功发布后才有可下载的文件；目录本身不是网页。macOS 清单为 `latest-mac.yml`，Windows 为 `latest.yml`。请通过 [Releases](https://github.com/EKKOLearnAI/ekko-studio-update-test/releases) 下载 A 版本安装器，再构建更高版本 B 测试更新。

每个平台使用单独的预发布 Release；保留旧版安装器和 blockmap，先上传完整文件，再切换清单。同一平台只允许版本前进，不能用不同内容覆盖已发布的同名安装器。

## 测试说明

完整步骤及一次性权限配置见 [桌面更新测试文档](https://github.com/EKKOLearnAI/ekko-studio/blob/main/packages/desktop/UPDATE-TESTING.md)。测试包使用与正式版相同的应用身份，请在专用测试机、虚拟机或独立系统用户中安装。测试包固定使用测试源，恢复正式源需手动安装正式版。

本仓库不包含应用源码，不运行生产发布工作流。构建代码位于 [Ekko Studio](https://github.com/EKKOLearnAI/ekko-studio)。本仓库文档采用 MIT；托管的 Ekko Studio 二进制仍遵循源项目及其第三方组件的许可证，不因上传到本仓库而改变。
