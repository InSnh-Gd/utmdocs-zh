# 📱 iOS

越狱与非越狱环境下，UTM 的兼容性不同，如果越狱，UTM 可以在 iOS11+ 的设备运行，UTM 也可以在非越狱设备上通过[“开发者调试”](https://github.com/osy/Jitterbug)的方式运行，兼容性取决于您设备的硬件新旧以及 iOS 版本，并且 UTM 有多个分支提供了不同的兼容性和特性，详细信息参见以下内容。



{% content-ref url="utm.md" %}
[utm.md](utm.md)
{% endcontent-ref %}

* UTM （JIT）是 UTM 的主线版本，它使用 TCG（JIT）加速以获得“最佳性能”，iOS 设备上的 JIT 需要设备已经越狱，或者对应您的 iOS 版本的解决方案（有关更多详细信息，请参阅“安装”）。
* UTM SE（”缓慢版“），它使用 TCTI TCG 后端，或者说线程解释器 （[threaded interpreter](https://github.com/ktemkin/qemu/blob/with\_tcti/tcg/aarch64-tcti/README.md)），它的性能比即时编译（JIT）慢，但比传统解释器（traditional interpreter）要快。通俗地说，UTM SE 的实际性能比 UTM JIT 要慢，UTM SE 可以像常规应用一样旁加载。
* UTM HV（Hypervisor），在满足条件的情况下，UTM HV 可以使用 hvf 虚拟化加速，它将提供无与伦比的仿真性能，但使用要求更为苛刻（有关更多详细信息，请参阅“安装”）。



从 GitHub 下载最新发布版本：

{% embed url="https://github.com/utmapp/UTM/releases/latest" %}

### 总结

| 版本                                                                              | 概述                     | 安装方式                        | JIT                                      | 虚拟化监视程序（Hvf）                             | 宿主机 USB                             |
| ------------------------------------------------------------------------------- | ---------------------- | --------------------------- | ---------------------------------------- | ---------------------------------------- | ----------------------------------- |
| [UTM.deb](https://github.com/utmapp/UTM/releases/latest/download/UTM.deb)       | iOS 的越狱版本              | 使用 Cydia、Sileo 或 dpkg 打开    | 可用                                       | <mark style="color:yellow;">可用（1）</mark> | 可用                                  |
| [UTM.ipa](https://github.com/utmapp/UTM/releases/latest/download/UTM.ipa)       | iOS 的非越狱（旁加载）版本        | 使用 AltStore 等方式安装（见非越狱设备页面） | <mark style="color:yellow;">可用（2）</mark> | <mark style="color:red;">不可用</mark>      | <mark style="color:red;">不可用</mark> |
| [UTM.HV.ipa](https://github.com/utmapp/UTM/releases/latest/download/UTM.HV.ipa) | iOS 的非越狱（TrollStore）版本 | TrollStore                  | <mark style="color:green;">可用（3）</mark>  | <mark style="color:yellow;">可用（1）</mark> | 可用                                  |
| [UTM.SE.ipa](https://github.com/utmapp/UTM/releases/latest/download/UTM.SE.ipa) | iOS 的非越狱（旁加载）版本        | AltStore、企业签名等方式            | <mark style="color:red;">不可用</mark>      | <mark style="color:red;">不可用</mark>      | <mark style="color:red;">不可用</mark> |

1. iOS 上的虚拟化监视程序（hvf）目前只在 M1 iPad 上可用。
2. 开启 JIT 可能会需要像 [Jitterbug](https://github.com/osy/Jitterbug)、[Jitstreamer](https://github.com/jkcoxson/JitStreamer) 这样的 JIT 工具。
3. UTM HV 需要 4.1.0 及更新版本才可以脱离 JIT 工具。
