# 🚲 UTM

* [非越狱设备](utm.md#non-jailbroken-devices)
  * [AltStore 软件源](utm.md#altstore-ruan-jian-yuan)
  * [AltStore 旁加载](utm.md#altstore-pang-jia-zai)
  * [其他方式](utm.md#qi-ta-fang-shi)
* [TrollStore](utm.md#trollstore)
* [越狱设备](utm.md#yue-yu-she-bei)

## 非越狱设备 <a href="#non-jailbroken-devices" id="non-jailbroken-devices"></a>

**如果您的设备系统版本是 iOS11～13：**那么 **** UTM 不需要越狱即可使用，您只需要旁加载 UTM。当然也可以使用开发者账户的证书签名 UTM 的 IPA 即可在未越狱的 iOS 设备安装使用。但您需要知道旁加载有以下缺点：

* 免费开发者帐户必须每 7 天重新签名一次
* 付费开发者帐号必须每 1 年重新签名一次

{% hint style="info" %}
**注意**

iOS 11～13 最高可以使用的版本为 UTM v3.2.4 并且不会再得到更新。
{% endhint %}

**如果您的设备系统版本是 iOS14.0 iOS14.1 或 iOS14.4 及更新版本：**需要使用 Jitterbug、Jitstreamer、AltJIT 或其他工具中的一个通过 “JIT 调试” 来启动 UTM 即可正常使用。

{% hint style="info" %}
**JIT 调试**

这里是指在您的设备上通过 VPN 或是局域网连接到 Mac/PC 或者另一台可以使用 WIFI 共享 的 iOS 设备，还可以连接到本机（使用 Jitterbug 本机调试和 UTM 的设备）进行调试。**通俗的说，这是类似于 Xcode 工具上开启 “JIT 编译” 的操作。**
{% endhint %}

**如果您的设备系统版本是 iOS14.2～iOS14.3：**如果您的设备具有 Apple A12 或更新的 CPU，可以直接旁加载 UTM。否则，您仍然需要 “JIT 调试”。

### AltStore 软件源

目前您需要 AltStore 测试版才能使用第三方软件源，准确的说，只有 AltStore 的 Patreon 支持者才能获得测试版。从软件源安装您还可以得到 AltStore 推送的更新。

1. 安装 [AltStore](https://altstore.io)。
2. 添加软件源：[https://alt.getutm.app](altstore://source?url=https://alt.getutm.app)
3. 在 AltStore 下载 UTM。

### AltStore 旁加载

如果您不是 AltStore 的 Patreon 的支持者，您只能使用公开版的 AltStore，公开版的 AltStore 不能添加第三方软件源也不能自动检查更新，不过 AltStore 仍然可以自动续签你的 UTM。

1. 安装 [AltStore](https://altstore.io)。
2. 在您运行 AltServer 的 Mac\PC 或运行 AltStore 的 iOS设备上下载 UTM 最新的 [IPA Releases](https://github.com/utmapp/UTM/releases/latest)。
3. 在 AltStore 打开 IPA。

### 其他方式

大多数“云签名”使用了错误的签名类型，您不能使用它们签名 UTM，否则 UTM 无法正常工作。当你使用 UTM 启动虚拟机时 UTM 崩溃或者黑屏，您的签名证书可能是无效的类型。&#x20;

您可以在查看“设置”中的`设置->通用->描述文件与设备管理`，如果用于签名 UTM 的证书在 `开发者应用` 中那么您的签名类型是正确的，反之如果证书在 `企业级应用` 中，则您的签名类型是错误的。

{% hint style="info" %}
**UTM SE**

与 UTM 不同，UTM SE 不支持 JIT 因此 UTM SE 的效率不佳，但是兼容所有签名服务。
{% endhint %}

## TrollStore

如果您的设备可以使用 [TrollStore](https://github.com/opa334/TrollStore)，那么您可以使用 UTM 的其他功能比如 USB 共享和虚拟化（目前仅限 M1 iPad）。您可以下载适用于 TrollStore 的 UTM IPA（UTM.HV.ipa），使用 TrollStore 安装。

{% hint style="info" %}
**提示**

您不可以使用 TrollStore 安装常规 UTM IPA，因为常规 UTM 包含 TrollStore 不支持的权限 `dynamic-codesigning`。
{% endhint %}

## 越狱设备

UTM 需要 AppSync Unified，您可以在 [Karen's Repo](cydia://url/https://cydia.saurik.com/api/share#%3Esource=https://cydia.akemi.ai/) 中找到。安装 UTM 需要在您的包管理器（Cydia、Sileo、Zebra 等）添加两个软件源。

1. AppSync Unified：[https://cydia.akemi.ai/](https://cydia.akemi.ai/)
2. UTM：[https://cydia.getutm.app/](https://cydia.getutm.app/)

更新包管理器元数据，安装 UTM 和 AppSync Unified。
