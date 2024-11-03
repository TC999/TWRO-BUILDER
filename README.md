## 基于 Github Action 的自动 TWRP 编译

## 广告

1. OrangeFox 在 [这里](https://github.com/azwhikaru/Action-OFRP-Builder) 

## 注意事项

1. Github Actions 服务**不是**无限的，为了避免浪费，不要在此使用未经验证的源代码，最好用于自动化构建已经稳定的仓库。

2. 在您进行任何更改之前，请确保您正在操作的仓库属于您。**如果您想要提交代码，请“Fork”，否则使用“Use this template”**。

3. 问题和拉取请求可能**不会**得到回复。如果您认为确实必要，请使用我的个人资料中的电子邮件与我联系。

4. Debian（Ubuntu）中的 Python 2 已被**移除**。如果您正在处理 Android 8.1 及以下版本，请使用 *Recovery Build (Legacy)*。

5. 不要询问任何关于您的源代码的问题，例如：
   - 没有规则来制作...
   - 图像...超出大小

## 感谢

所有贡献者

## 参数描述

| 名称                 | 描述                                       | 示例                                                         |
| -------------------- | ---------------------------------------- | ------------------------------------------------------------ |
| `MANIFEST_URL`       | 源地址                                    | https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git  |
| `MANIFEST_BRANCH`    | 源分支                                    | twrp-12.1                                                   |
| `DEVICE_TREE_URL`    | 设备地址                                   | https://github.com/TeamWin/android_device_asus_I003D          |
| `DEVICE_TREE_BRANCH` | 设备分支                                   | android-12.1                                                 |
| `DEVICE_PATH`        | 设备位置                                   | device/asus/I003D                                            |
| `COMMON_TREE_URL`    | 公共树地址                                 | https://github.com/TeamWin/android_device_asus_sm8250-common  |
| `COMMON_PATH`        | 公共树位置                                 | device/asus/sm8250-common                                    |
| `DEVICE_NAME`        | 型号名称                                   | I003D                                                       |
| `MAKEFILE_NAME`      | Makefile 名称                             | twrp_I003D                                                   |
| `BUILD_TARGET`       | 构建目标分区（boot/recovery/vendorboot） | recovery                                                    |

-----

## 如何使用

```
例如，您的用户名是：JohnSmith
```

#### 0. 如果您想要提交代码，请在本仓库右上角点击 'Fork'

![图片](https://user-images.githubusercontent.com/37921907/177914706-c92476c5-7e14-4fb3-be94-0c8a11dae874.png) 

#### 1. 如果您只是想简单使用，请点击本仓库右上角的 'Use this template'

![图片](https://github.com/azwhikaru/Action-TWRP-Builder/assets/37921907/fae6ce3c-bd4c-4bbe-8050-5dd29dff2522) 

#### 2. 在等待自动重定向后，您将看到您自己的用户名

![图片](https://user-images.githubusercontent.com/37921907/177915106-5bde6fc9-303c-479e-b290-22b48efd1e4e.png) 

#### 3. 更改 [用户名和电子邮件](https://github.com/CaptainThrowback/Action-Recovery-Builder/blob/main/.github/workflows/Recovery%20Build.yml#L100-L101) 以反映您的 Github 凭证（可选）

## 设置 SSH 密钥（可选）

#### 4. 转到设置，然后选择部署密钥并选择“添加部署密钥”按钮。

#### 5. 在您的 Android 设备上，安装 [Termux](https://github.com/termux/termux-app/releases) 

#### 6. 在 Termux 中安装 openssh 并生成 ssh 密钥。（不要为密钥使用密码）

注意：在为像 git@github.com:owner/repo.git 或 https://github.com/owner/repo 这样的仓库创建部署密钥时，将该 URL 放入密钥注释中。（提示：尝试 ssh-keygen ... -C "git@github.com:owner/repo.git".）
owner = 您的 Github 用户名

```
pkg install openssh
ssh-keygen -t ed25519 -C "git@github.com:owner/Action-Recovery-Builder.git"
```

#### 7. 将密钥添加到您的仓库。在 Termux 中，使用以下命令：

```
cd /data/data/com.termux/files/usr/etc/ssh
cat ssh_host_ed25519_key.pub
```

  选择并复制密钥，然后粘贴到密钥框中。
  您可以为标题选择任何名称。

#### 8. 现在添加您的私有 ssh 密钥。回到 Termux：

```
cat ssh_host_ed25519_key
```

  从 Termux 复制输出。

  在浏览器中，选择安全标签下的 *Secrets*。
  选择 Actions
  选择 New repository secret
  对于 New secret name，应该是 SSH_PRIVATE_KEY
  将 ssh_host_ed25519_key 的输出粘贴到 Value 框中。
  然后选择 Add secret。

## 构建 Recovery

#### 9. 点击 'Actions-Recovery Build'

![图片](https://user-images.githubusercontent.com/37921907/177915304-8731ed80-1d49-48c9-9848-70d0ac8f2720.png) 

#### 10. 点击 'Run workflow' 并根据上述 'parameter description' 填写

![图片](https://user-images.githubusercontent.com/37921907/177915346-71c29149-78fb-4a00-996f-5d84ffc9eb8c.png) 

#### 11. 填写完毕后，点击 'Run workflow' 开始运行

-----

## 编译结果

可在 [Release](../../releases) 下载
