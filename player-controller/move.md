# Move

## [Input](https://docs.unity.cn/cn/2019.4/ScriptReference/Input.html).GetAxis

### 描述

返回由 `axisName` 标识的虚拟轴的值。

对于键盘和游戏杆输入设备，该值将处于 -1...1 的范围内。<mark style="color:red;">**（是标量而非向量）**</mark>\
\
该值的含义取决于输入控制的类型，例如，对于游戏杆的水平轴，值为 1 表示游戏杆向右推到底，值为 -1 表示游戏杆向左推到底；值为 0 表示游戏杆处于中性位置。\
\
如果将轴映射到鼠标，该值会有所不同，并且不会在 -1...1 的范围内。此时，该值为当前鼠标增量乘以轴灵敏度。通常，正值表示鼠标向右/向下移动，负值表示鼠标向左/向上移动。\
\
该值与帧率无关；使用该值时，您无需担心帧率变化问题。

**注意：**水平范围和垂直范围从 0 变为 +1 或 -1，以 0.05f 的步幅增加/减少。[GetAxisRaw](https://docs.unity.cn/cn/2019.4/ScriptReference/Input.GetAxisRaw.html) 立即从 0 变为 1 或 -1，因此没有步幅。

```
    public float moveSpeed;
    public CharacterController charCon;
    public float mouseSensitivity;
    private Vector3 moveInput;
void Update()
{
    //store y velocity
    float yStore = moveInput.y;
    //moveInput.x = Input.GetAxis("Horizontal") * moveSpeed * Time.deltaTime;
    //moveInput.z = Input.GetAxis("Vertical") * moveSpeed * Time.deltaTime;

    Vector3 vertMove = transform.forward * Input.GetAxis("Vertical");
    Vector3 horitMove = transform.right * Input.GetAxis("Horizontal");

    moveInput = vertMove + horitMove;
    moveInput.Normalize();
    //Normalize()使向量的值为1
    moveInput = moveInput * moveSpeed;
    //重力，由于之前改变了moveInput的值，因此需要用储存y velocity给moveInput.y重新赋值
    //其实下列代码中，把yStore和moveInput.y的调换一下，结果是一样的，只需要把
    //yStore = moveInput.y;移动到charCon.Move()之前
    moveInput.y = yStore;
    moveInput.y += Physics.gravity.y * Time.deltaTime * gravityModifier;

    if(charCon.isGrounded)//如果在地面上
    {
        moveInput.y = Physics.gravity.y * Time.deltaTime * gravityModifier;
    }
    if(moveInput.y < -10.0f)//限制下落速度
    {
        moveInput.y = -10.0f;
    }  
    charCon.Move(moveInput * Time.deltaTime);

}
```

[重力Gravity](https://app.gitbook.com/s/fhVo0DEhzYbtmuRTLGnE/\~/changes/btjXR1vJ6SLzKvZ3VZRl/game-manager/zhong-li-gravity)

{% content-ref url="zhong-li-gravity.md" %}
[zhong-li-gravity.md](zhong-li-gravity.md)
{% endcontent-ref %}

## Quaternion

### 描述

四元数用于表示旋转。

它们结构紧凑，不受万向锁影响，可以轻松插值。 Unity 内部使用四元数来表示所有旋转。\
\
它们基于复数，不容易理解。 您几乎不会有机会访问或修改单个四元数分量（x、y、z、w）； 大多数情况下，您只需要获取现有旋转（例如，来自 [Transform](https://docs.unity.cn/cn/2021.3/ScriptReference/Transform.html)），然后使用它们构造新的旋转 （例如，在两个旋转之间平滑插值）。 您绝大多数时间使用的四元数函数为： [Quaternion.LookRotation](https://docs.unity.cn/cn/2021.3/ScriptReference/Quaternion.LookRotation.html)、[Quaternion.Angle](https://docs.unity.cn/cn/2021.3/ScriptReference/Quaternion.Angle.html)、[Quaternion.Euler](https://docs.unity.cn/cn/2021.3/ScriptReference/Quaternion.Euler.html)、[Quaternion.Slerp](https://docs.unity.cn/cn/2021.3/ScriptReference/Quaternion.Slerp.html)、[Quaternion.FromToRotation](https://docs.unity.cn/cn/2021.3/ScriptReference/Quaternion.FromToRotation.html) 和 [Quaternion.identity](https://docs.unity.cn/cn/2021.3/ScriptReference/Quaternion-identity.html)。（其他函数仅用于一些十分奇特的用例。）\
\
您可以使用 Quaternion.operator \* 对旋转进行旋转，或对向量进行旋转。\


## [Transform](https://docs.unity.cn/cn/2019.4/ScriptReference/Transform.html).forward



| [right](https://docs.unity.cn/cn/2019.4/ScriptReference/Transform-right.html)     | 世界空间中变换的红轴。              |
| --------------------------------------------------------------------------------- | ------------------------ |
| [forward](https://docs.unity.cn/cn/2019.4/ScriptReference/Transform-forward.html) | 返回一个标准化矢量，它表示世界空间中变换的蓝轴。 |
| [up](https://docs.unity.cn/cn/2019.4/ScriptReference/Transform-up.html)           | 世界空间中变换的绿轴。              |
