# Move

## [Input](https://docs.unity.cn/cn/2019.4/ScriptReference/Input.html).GetAxis

### 描述

返回由 `axisName` 标识的虚拟轴的值。

对于键盘和游戏杆输入设备，该值将处于 -1...1 的范围内。\
\
该值的含义取决于输入控制的类型，例如，对于游戏杆的水平轴，值为 1 表示游戏杆向右推到底，值为 -1 表示游戏杆向左推到底；值为 0 表示游戏杆处于中性位置。\
\
如果将轴映射到鼠标，该值会有所不同，并且不会在 -1...1 的范围内。此时，该值为当前鼠标增量乘以轴灵敏度。通常，正值表示鼠标向右/向下移动，负值表示鼠标向左/向上移动。\
\
该值与帧率无关；使用该值时，您无需担心帧率变化问题。

**注意：**水平范围和垂直范围从 0 变为 +1 或 -1，以 0.05f 的步幅增加/减少。[GetAxisRaw](https://docs.unity.cn/cn/2019.4/ScriptReference/Input.GetAxisRaw.html) 立即从 0 变为 1 或 -1，因此没有步幅。



```
void Update()
{
    //moveInput.x = Input.GetAxis("Horizontal") * moveSpeed * Time.deltaTime;
    //moveInput.z = Input.GetAxis("Vertical") * moveSpeed * Time.deltaTime;

    Vector3 vertMove = transform.forward * Input.GetAxis("Vertical");
    Vector3 horitMove = transform.right * Input.GetAxis("Horizontal");

    moveInput = vertMove + horitMove;
    moveInput.Normalize();
    moveInput = moveInput * moveSpeed;
    

    charCon.Move(moveInput * Time.deltaTime);
    
    //control camera rotation
    Vector2 mouseInput = new Vector2(Input.GetAxisRaw("Mouse X"), Input.GetAxisRaw("Mouse Y")) * mouseSensitivity;

    transform.rotation = Quaternion.Euler(transform.rotation.eulerAngles.x, transform.rotation.eulerAngles.y + mouseInput.x, transform.rotation.eulerAngles.z);

    camTransform.rotation = Quaternion.Euler(camTransform.rotation.eulerAngles + new Vector3(-mouseInput.y, 0f, 0f));

}
```

## Quaternion

### 描述

四元数用于表示旋转。

它们结构紧凑，不受万向锁影响，可以轻松插值。 Unity 内部使用四元数来表示所有旋转。\
\
它们基于复数，不容易理解。 您几乎不会有机会访问或修改单个四元数分量（x、y、z、w）； 大多数情况下，您只需要获取现有旋转（例如，来自 [Transform](https://docs.unity.cn/cn/2021.3/ScriptReference/Transform.html)），然后使用它们构造新的旋转 （例如，在两个旋转之间平滑插值）。 您绝大多数时间使用的四元数函数为： [Quaternion.LookRotation](https://docs.unity.cn/cn/2021.3/ScriptReference/Quaternion.LookRotation.html)、[Quaternion.Angle](https://docs.unity.cn/cn/2021.3/ScriptReference/Quaternion.Angle.html)、[Quaternion.Euler](https://docs.unity.cn/cn/2021.3/ScriptReference/Quaternion.Euler.html)、[Quaternion.Slerp](https://docs.unity.cn/cn/2021.3/ScriptReference/Quaternion.Slerp.html)、[Quaternion.FromToRotation](https://docs.unity.cn/cn/2021.3/ScriptReference/Quaternion.FromToRotation.html) 和 [Quaternion.identity](https://docs.unity.cn/cn/2021.3/ScriptReference/Quaternion-identity.html)。（其他函数仅用于一些十分奇特的用例。）\
\
您可以使用 Quaternion.operator \* 对旋转进行旋转，或对向量进行旋转。\
