# Android 签名配置指南

## 1. 生成 Android Keystore

```bash
# 生成新的keystore
keytool -genkey -v -keystore rustdesk-release.keystore -alias rustdesk -keyalg RSA -keysize 2048 -validity 10000

# 或使用Android Studio生成
# Build -> Generate Signed Bundle/APK -> Create New Keystore
```

## 2. 转换为 Base64

```bash
# Windows
certutil -encode rustdesk-release.keystore rustdesk-release.keystore.base64

# macOS/Linux
base64 -i rustdesk-release.keystore -o rustdesk-release.keystore.base64
```

## 3. 在 GitHub 中配置 Secrets

前往你的 GitHub 仓库 -> Settings -> Secrets and variables -> Actions，添加：

| Secret Name | Value |
|-------------|-------|
| `ANDROID_SIGNING_KEY` | keystore文件的base64内容 |
| `ANDROID_ALIAS` | 密钥别名 (例如: rustdesk) |
| `ANDROID_KEY_STORE_PASSWORD` | keystore密码 |
| `ANDROID_KEY_PASSWORD` | 密钥密码 |

## 4. 验证配置

配置完成后，推送代码到仓库将自动触发构建，生成已签名的APK文件。

## 临时解决方案

如果暂时不需要签名，可以使用debug签名。构建的APK仍然可以安装使用，只是无法发布到应用商店。