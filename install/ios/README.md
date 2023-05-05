# 📱 iOS

* [非越狱设备](./#non-jailbroken-devices)
  * [AltStore 软件源](./#altstore-ruan-jian-yuan)
  * [AltStore 旁加载](./#altstore-pang-jia-zai)
  * [其他方式](./#qi-ta-fang-shi)
* [TrollStore](./#trollstore)
* [越狱设备](./#yue-yu-she-bei)
* [总结](./#zong-jie)

越狱与非越狱环境下，UTM 的兼容性不同，如果越狱，UTM 可以在 iOS11+ 的设备运行，UTM 也可以在非越狱设备上通过[“开发者调试”](https://github.com/osy/Jitterbug)的方式运行，兼容性取决于您设备的硬件新旧以及 iOS 版本，并且 UTM 有多个分支提供了不同的兼容性和特性，详细信息参见以下内容。



{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

* UTM （JIT）是 UTM 的主线版本，它使用 TCG（JIT）加速以获得“最佳性能”，iOS 设备上的 JIT 需要设备已经越狱，或者对应您的 iOS 版本的解决方案（有关更多详细信息，请参阅“安装”）。
* UTM SE（”缓慢版“），它使用 TCTI TCG 后端，或者说线程解释器 （[threaded interpreter](https://github.com/ktemkin/qemu/blob/with\_tcti/tcg/aarch64-tcti/README.md)），它的性能比即时编译（JIT）慢，但比传统解释器（traditional interpreter）要快。通俗地说，UTM SE 的实际性能比 UTM JIT 要慢，UTM SE 可以像常规应用一样旁加载。
* UTM HV（Hypervisor），在满足条件的情况下，UTM HV 可以使用 hvf 虚拟化加速，它将提供无与伦比的仿真性能，但使用要求更为苛刻（有关更多详细信息，请参阅“安装”）。



从 GitHub 下载最新发布版本：

{% embed url="https://github.com/utmapp/UTM/releases/latest" %}

## 非越狱设备 <a href="#non-jailbroken-devices" id="non-jailbroken-devices"></a>

**如果您的设备系统版本是 iOS11～13：**那么 UTM 不需要越狱即可使用，您只需要旁加载 UTM。当然也可以使用开发者账户的证书签名 UTM 的 IPA 即可在未越狱的 iOS 设备安装使用。但您需要知道旁加载有以下缺点：

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



## 总结

| 版本                                                                              | 概述                     | 安装方式                        | JIT                                      | 虚拟化监视程序（Hvf）                             | 宿主机 USB                             |
| ------------------------------------------------------------------------------- | ---------------------- | --------------------------- | ---------------------------------------- | ---------------------------------------- | ----------------------------------- |
| [UTM.deb](https://github.com/utmapp/UTM/releases/latest/download/UTM.deb)       | iOS 的越狱版本              | 使用 Cydia、Sileo 或 dpkg 打开    | 可用                                       | <mark style="color:yellow;">可用（1）</mark> | 可用                                  |
| [UTM.ipa](https://github.com/utmapp/UTM/releases/latest/download/UTM.ipa)       | iOS 的非越狱（旁加载）版本        | 使用 AltStore 等方式安装（见非越狱设备页面） | <mark style="color:yellow;">可用（2）</mark> | <mark style="color:red;">不可用</mark>      | <mark style="color:red;">不可用</mark> |
| [UTM.HV.ipa](https://github.com/utmapp/UTM/releases/latest/download/UTM.HV.ipa) | iOS 的非越狱（TrollStore）版本 | TrollStore                  | <mark style="color:green;">可用（3）</mark>  | <mark style="color:yellow;">可用（1）</mark> | 可用                                  |
| [UTM.SE.ipa](https://github.com/utmapp/UTM/releases/latest/download/UTM.SE.ipa) | iOS 的非越狱（旁加载）版本        | AltStore、企业签名等方式            | <mark style="color:red;">不可用</mark>      | <mark style="color:red;">不可用</mark>      | <mark style="color:red;">不可用</mark> |

1. iOS 上的虚拟化监视程序（hvf）目前只在 M1 iPad 上可用。
2. 开启 JIT 可能会需要像 [Jitterbug](https://github.com/osy/Jitterbug)、[Jitstreamer](https://github.com/jkcoxson/JitStreamer) 这样的 JIT 工具。
3. UTM HV 需要 4.1.0 及更新版本才可以脱离 JIT 工具。
