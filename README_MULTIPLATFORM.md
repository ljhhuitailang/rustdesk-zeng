# RustDesk Zeng - 多平台远程桌面解决方案

基于 RustDesk 开源项目的增强版本，支持全平台自动构建和发布。

## 🚀 特性

- ✅ **多平台支持**: Windows (x86, x64, ARM64), macOS (Intel & Apple Silicon), Linux (x64, ARM64)
- ✅ **自动构建**: GitHub Actions 自动构建所有平台的发布版本
- ✅ **Flutter UI**: 现代化的 Flutter 用户界面
- ✅ **硬件编解码**: 支持硬件加速的视频编解码
- ✅ **移动端支持**: Android 和 iOS 应用

## 📦 发布版本

每次代码提交都会自动触发构建，生成以下平台的安装包：

### Windows
- `rustdesk-{version}-x86_64.exe` - 64位便携版
- `rustdesk-{version}-x86_64.msi` - 64位安装包
- `rustdesk-{version}-i686.exe` - 32位便携版
- `rustdesk-{version}-aarch64.exe` - ARM64版本

### macOS
- `rustdesk-{version}-x86_64.dmg` - Intel Mac
- `rustdesk-{version}-aarch64.dmg` - Apple Silicon Mac

### Linux
- `rustdesk-{version}-x86_64.deb` - Ubuntu/Debian 64位
- `rustdesk-{version}-aarch64.deb` - Ubuntu/Debian ARM64
- `rustdesk-{version}-x86_64.rpm` - RHEL/CentOS/Fedora 64位
- `rustdesk-{version}-aarch64.rpm` - RHEL/CentOS/Fedora ARM64
- `rustdesk-{version}-x86_64.AppImage` - 通用Linux包
- `rustdesk-{version}-x86_64.flatpak` - Flatpak包

### Android
- `rustdesk-{version}-aarch64.apk` - ARM64设备
- `rustdesk-{version}-armv7.apk` - ARMv7设备
- `rustdesk-{version}-x86_64.apk` - x64模拟器
- `rustdesk-{version}-universal.apk` - 通用包

## 🔧 配置 GitHub Secrets

为了启用应用签名和完整的发布流程，需要在 GitHub 仓库设置中添加以下 Secrets：

### 1. Android 签名 (必需)
```
ANDROID_SIGNING_KEY          # Android keystore base64编码
ANDROID_ALIAS               # keystore别名
ANDROID_KEY_STORE_PASSWORD  # keystore密码
ANDROID_KEY_PASSWORD        # 密钥密码
```

### 2. macOS 签名 (可选，用于发布到App Store)
```
MACOS_P12_BASE64           # Apple开发者证书p12文件base64编码
MACOS_P12_PASSWORD         # p12证书密码
MACOS_CODESIGN_IDENTITY    # 代码签名身份
MACOS_NOTARIZE_JSON        # 公证服务配置JSON
```

### 3. Windows 签名 (可选)
```
SIGN_BASE_URL             # 代码签名服务URL
SIGN_SECRET_KEY           # 签名服务密钥
```

### 配置方法：

1. 进入你的 GitHub 仓库
2. 点击 `Settings` -> `Secrets and variables` -> `Actions`
3. 点击 `New repository secret` 添加上述secrets

## 🏗️ 本地构建

### 先决条件
- Rust 1.75+
- Flutter 3.24.5
- CMake
- LLVM/Clang

### 构建命令

```bash
# 克隆仓库
git clone https://github.com/ljhhuitailang/rustdesk-zeng.git
cd rustdesk-zeng

# 构建桌面版
python3 build.py --flutter --release

# 构建Android版
cd flutter
flutter build apk --release

# 构建iOS版 (仅macOS)
cd flutter
flutter build ios --release
```

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！

## 📄 许可证

本项目基于 AGPL-3.0 许可证 - 详见 [LICENSE](LICENSE) 文件

## 🙏 致谢

- [RustDesk](https://github.com/rustdesk/rustdesk) - 原始项目
- [Flutter](https://flutter.dev/) - UI框架
- [Rust](https://www.rust-lang.org/) - 编程语言

---

**注意**: 这是一个基于 RustDesk 的修改版本，仅用于学习和个人使用。请确保遵守相关开源许可证。