# C#

这篇文章主要讲述在 Unity3D 中使用 C# 脚本的一些常见规则。

[TOC]



# 初见 Unity3D 中的 C# 脚本

## 创建脚本

在 Unity3D 中创建 C# 脚本，可以通过在 Project 窗口的 Assets 文件夹下右键，在 Create 选项中，选择 C# Script。

创建本地文件后，需要确定脚本名称。如果在创建时，使用了默认的 NewBehaviourScript 名称，后续要重命名，就需要保证同时修改文件名和类名。否则无法将脚本挂载到 GameObject 上，或者出现黄色警告（事先挂载了再修改的情况）。

新的脚本包含了一段代码模板。

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Player : MonoBehaviour
{
    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        
    }
}
```

每个脚本初始都包含了 Start 和 Update 方法。

Start 是当脚本被挂载到 GameObject 上后，并且脚本组件处于激活状态，那么运行游戏时会调用一次。

Update 则会每帧调用一次，调用次数受设备的性能帧数影响。

## 生命周期函数

上述两个函数方法属于生命周期函数。

除此之外，还有 Awake、FixedUpdate、LateUpdate 等等。

按照一个生命周期来排序，依次是

- Awake：当 GameObject 实例化后，处于激活状态，仅调用一次。
- OnEnable：当 GameObject 处于激活状态，每激活一次脚本组件，调用一次。
- Start：当 GameObject 和脚本组件处于激活状态，仅调用一次。
- FixedUpdate：根据固定帧率执行物理计算。
- Update：根据设备性能帧率执行游戏逻辑计算。
- LateUpdate：在 Update 之后执行，通常用于计算相机跟随。
- OnDisable：当 GameObject 处于激活状态，每失活一次脚本组件，调用一次。
- OnDestroy：当 GameObject 或者脚本组件被移除时，仅调用一次。

当然还有许多函数没有被列入，在此仅提供常见的函数。

