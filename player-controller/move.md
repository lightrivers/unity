# Move

## Quaternion

### 描述

四元数用于表示旋转。

它们结构紧凑，不受万向锁影响，可以轻松插值。 Unity 内部使用四元数来表示所有旋转。\
\
它们基于复数，不容易理解。 您几乎不会有机会访问或修改单个四元数分量（x、y、z、w）； 大多数情况下，您只需要获取现有旋转（例如，来自 [Transform](https://docs.unity.cn/cn/2021.3/ScriptReference/Transform.html)），然后使用它们构造新的旋转 （例如，在两个旋转之间平滑插值）。 您绝大多数时间使用的四元数函数为： [Quaternion.LookRotation](https://docs.unity.cn/cn/2021.3/ScriptReference/Quaternion.LookRotation.html)、[Quaternion.Angle](https://docs.unity.cn/cn/2021.3/ScriptReference/Quaternion.Angle.html)、[Quaternion.Euler](https://docs.unity.cn/cn/2021.3/ScriptReference/Quaternion.Euler.html)、[Quaternion.Slerp](https://docs.unity.cn/cn/2021.3/ScriptReference/Quaternion.Slerp.html)、[Quaternion.FromToRotation](https://docs.unity.cn/cn/2021.3/ScriptReference/Quaternion.FromToRotation.html) 和 [Quaternion.identity](https://docs.unity.cn/cn/2021.3/ScriptReference/Quaternion-identity.html)。（其他函数仅用于一些十分奇特的用例。）\
\
您可以使用 Quaternion.operator \* 对旋转进行旋转，或对向量进行旋转。\
