# Cursor

## [Cursor](https://docs.unity.cn/cn/2021.3/ScriptReference/Cursor.html).lockState

确定硬件指针是否锁定到视图的中心、受限于窗口或者根本不受限制。

锁定时，光标位于视图的中心且无法移动。无论 [Cursor.visible](https://docs.unity.cn/cn/2021.3/ScriptReference/Cursor-visible.html) 的值如何，光标在此状态下均不可见。\


```
using UnityEngine;
public class Gamemanager : MonoBehaviour
{
    void Start()
    {
        Cursor.lockState = CursorLockMode.Locked;
    }
}
```

当受限时，光标表现正常，但限制在视图中。例如，在 Confined 模式下，如果应用程序在窗口中运行，鼠标光标将无法离开窗口。仅在 Windows 和 Linux 独立构建中受支持。\
\
要提供良好的用户体验，建议仅支持由用户操作（例如按下按钮）来锁定或限制光标。

```
using UnityEngine;
    void OnGUI()
    {
        //Press this button to lock the Cursor
        if (GUI.Button(new Rect(0, 0, 100, 50), "Lock Cursor"))
        {
            Cursor.lockState = CursorLockMode.Locked;
        }    
        //Press this button to confine the Cursor within the screen
        if (GUI.Button(new Rect(125, 0, 100, 50), "Confine Cursor"))
        {
            Cursor.lockState = CursorLockMode.Confined;
        }
    }
```

参考资料：[https://docs.unity.cn/cn/2021.3/ScriptReference/Cursor-lockState.html](https://docs.unity.cn/cn/2021.3/ScriptReference/Cursor-lockState.html)

## [Cursor](https://docs.unity.cn/cn/2021.3/ScriptReference/Cursor.html).visible



确定硬件指针是否可见。

将此属性设置为 true 可显示光标。设置为 false 可隐藏光标。请注意，在 [CursorLockMode.Locked](https://docs.unity.cn/cn/2021.3/ScriptReference/CursorLockMode.Locked.html) 模式下，无论此属性的值如何，光标始终不可见。

```
using UnityEngine;
using System.Collections;public class CursorScript : MonoBehaviour
{
    // Use this for initialization
    void Start()
    {
        //Set Cursor to not be visible
        Cursor.visible = false;
    }
}
```

参考资料：[https://docs.unity.cn/cn/2021.3/ScriptReference/Cursor-visible.html](https://docs.unity.cn/cn/2021.3/ScriptReference/Cursor-visible.html)
