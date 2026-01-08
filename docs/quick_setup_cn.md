# 快速配置 (Quick setup)

该插件配备了众多配置选项以应对不同场景，但在常规使用中仅需设置少数几项。为此，我们推出了设置向导 (Setup wizard)功能，旨在简化配置流程。

![](../images/quick_setup_1.png)

自托管实时同步功能提供三种配置方式。

1. [使用setup URIs](#1使用setup-uris) *(推荐)*
2. [最小化配置](#2-最小化配置)
3. [完全手动设置并在此对话框中启用](#3-手动设置)
## 第一台设备配置

### 1.使用setup URIs

> [!TIP]
> setup URI是什么? 为什么需要setup URI?  
> setup URI 是自托管LiveSync配置的加密形式，以URI格式呈现。 起始部分为 `obsidian://setuplivesync?settings=`. 该URI通过密码加密，因此可以在设备之间相对安全地共享。虽然它有点长，但仅占用一行。通过这一行URI，可以一次性统一配置一系列设置，避免出现任何不一致的情况。 
> 
> 如果您已通过 [Automated setup on Fly.io](./setup_flyio.md#a-very-automated-setup) 配置远程数据库或 [set up your server with the tool](./setup_own_server.md#1-generate-the-setup-uri-on-a-desktop-device-or-server), **您应当已拥有其中一种配置** 

在该流程中, [this video](https://youtu.be/7sa_I1832Xc?t=146) 会对我们有所帮助。

1. 点击 `Use` 按钮 （或者通过命令面板启动 `Use the copied setup URI（使用复制的设置URI）` 功能).
2. 在弹出的对话框中粘贴 Setup URI。
3. 输入Setup URI对应的密码短语。
4. 当询问 `Importing LiveSync's conf, OK?（是否导入LiveSync配置？）` 时选择`yes（是）`
5. 询问`How would you like to set it up?（希望如何进行设置？）`时，选择`Set it up as secondary or subsequent device (设置为第二台或后续设备)`。
6. 初始化即将开始，请稍等片刻。
7. 统将询问是否同步隐藏文件，请根据个人偏好选择
   1. 若初次使用自托管LiveSync，可暂时跳过此设置，后续再配置。
8. 同步已启动！当自托管LiveSync的状态指示消失后，建议选择`Reload app without saving（不保存并重新加载应用）`

好了，我们可以进行下一步的操作 [next step](#).

### 2. 最小化配置

若您未设置任何Setup URI，请点击`start（启动）`按钮。此时设置对话框将转为向导模式，仅显示最精简的设置项。

>[!TIP]
> 我们可以随时使用该工具生成Setup URI [this tool](./setup_own_server.md#1-generate-the-setup-uri-on-a-desktop-device-or-server).

![](../images/quick_setup_2.png)


#### 选择远端类型

1. 从下拉菜单中选择远端类型。 目前我们可在 CouchDB（及其兼容数据库）与对象存储（MinIO、S3、R2）之间进行选择。CouchDB 是首选方案，也是推荐选项。而支持对象存储目前属于实验性功能。


#### 远端配置

##### CouchDB

请输入已设置数据库的相关信息。

![](../images/quick_setup_3.png)  

##### 对象存储

1. 输入S3 API和存储桶的信息。

![](../images/quick_setup_3b.png)  


注1：若使用S3服务，可将Endpoint URL留空。
注2：若您的对象存储无法完全配置CORS设置，可通过启用`Use Custom HTTP Handler（使用自定义HTTP处理程序）`开关连接至服务器。

2. 请点击一次`Test Connection（测试连接）`中的`Test（测试）`按钮，确保能够成功连接到对象存储服务。

#### 仅限CouchDB: 测试数据库连接并检查数据库配置

我们可以检查数据库的连接性以及数据库设置。

![](../images/quick_setup_5.png)  

#### 仅限CouchDB: 检查并修复数据库配置

检查数据库设置并修复所有问题。

![](../images/quick_setup_6.png)

此项可能因连接方式不同而变化。在上述情况下，请依次按下三个"修复"按钮。

若修复按钮消失且全部变为勾选标记，即表示操作完成。

#### 保密性配置（可选但强烈推荐）

![](../images/quick_setup_4.png)

Enable End-to-end encryption and the contents of your notes will be encrypted at the moment it leaves the device. We strongly recommend enabling it. And `Path Obfuscation` also obfuscates filenames. Now stable and recommended.
启用端到端加密功能（End-to-end encryption）后，您的笔记内容在离开设备时即被加密。我们强烈建议您启用此功能。同时，`Path Obfuscation（路径混淆）`功能也会对文件名进行混淆处理。该功能现已稳定运行，建议您使用。

若您处于封闭网络环境，且明确不会受到第三方访问，可禁用这些设置。

> [!TIP]
> 加密采用基于256位AES-GCM算法实现。

我们现在可以继续进行下一步。

#### 同步设定
最后，通过选择一个同步预设来完成向导。

请注意：如果您打算使用对象存储，则无法选择 `LiveSync`.

![](../images/quick_setup_9_1.png)

选择我们想要使用的同步方法并点击`Apply（应用）`。若需要初始化数据库，系统将在此刻执行。当显示`All done!（全部完成）`时，即表示已准备好进行同步。

`Copy settings as a new setup URI（复制设置以生成新配置URI）`对话框将自动弹出。请输入密码短语用于加密新的`Setup URI`（此密码短语仅用于加密配置URI，而非保险库本身）。

![](../images/quick_setup_10.png)

配置URI将被复制到剪贴板，请务必记录此信息（请勿保存在Obsidian中）。

>[!TIP]
我们随时可以通过`Copy current settings as a new setup URI（复制当前设置以生成新配置URI）`功能进行复制。

### 3. 手动设置

强烈建议先进行“最小化配置”，并在确认同步完成后再配置其他内容。

如果您出于某些原因需要手动配置，请点击 `Enable LiveSync on this device as the set-up was completed manually` 旁边的 `Enable` 按钮。

同时，请通过`Copy current settings as a new setup URI（将当前设置复制为新的Setup URI）`来复制Setup  URI，并另行保存（请勿记录在 Obsidian 中）。

## 在后续设备上
在第一台设备上安装 Self-hosted LiveSync 后，系统会生成一个Setup URI。**首选方案是直接使用该 Setup URI**。请将其分享到您想要进行设置的设备上。

这与 [Using setup URIs on the first device](#1-using-setup-uris). 完全相同。请参考该部分。
