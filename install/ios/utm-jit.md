# 🚲 UTM JIT

* [非越狱设备](utm-jit.md#non-jailbroken-devices)
  *

### 非越狱设备 <a href="#non-jailbroken-devices" id="non-jailbroken-devices"></a>

**如果您的设备系统版本是 iOS11～13：**UTM 不需要越狱即可使用，您只需要旁加载 UTM。当然也可以使用开发者账户的证书签名在未越狱的 iOS 设备上安装未经批准的应用。但您需要知道旁加载有以下缺点：

* 免费开发者帐户必须每 7 天重新签名一次
* 付费开发者帐号必须每 1 年重新签名一次

{% hint style="info" %}
#### 注意

iOS 11～13 最高可以使用的版本为 UTM v3.2.4 并且不会再得到更新。
{% endhint %}



**如果您的设备系统版本是 iOS14.0 iOS14.1 或 iOS14.4 及更新版本：**您需要使用 Jitterbug、Jitstreamer、AltJIT 或其他工具中的一个通过 “JIT 调试” 来启动 UTM 即可正常使用。

{% hint style="info" %}
#### JIT 调试

这里是指在您的设备上通过 VPN 或是局域网连接到 Mac/PC 或者另一台可以使用 WIFI 共享 的 iOS 设备，还可以连接到本机（使用 Jitterbug 本机调试和 UTM 的设备）进行调试。**通俗的说，这是类似于 Xcode 工具上开启 “JIT 编译” 的操作。**
{% endhint %}



如果您的设备系统版本是 iOS14.2～iOS14.3：如果您的设备具有 Apple A12 或更新的 CPU，则可以直接旁加载 UTM。否则，您仍然需要

