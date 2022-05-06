# GUI.Button

public static bool Button ([Rect](https://docs.unity.cn/cn/2021.3/ScriptReference/Rect.html) position, string text);

public static bool Button ([Rect](https://docs.unity.cn/cn/2021.3/ScriptReference/Rect.html) position, [Texture](https://docs.unity.cn/cn/2021.3/ScriptReference/Texture.html) image);

public static bool Button ([Rect](https://docs.unity.cn/cn/2021.3/ScriptReference/Rect.html) position, [GUIContent](https://docs.unity.cn/cn/2021.3/ScriptReference/GUIContent.html) content);

public static bool Button ([Rect](https://docs.unity.cn/cn/2021.3/ScriptReference/Rect.html) position, string text, [GUIStyle](https://docs.unity.cn/cn/2021.3/ScriptReference/GUIStyle.html) style);

public static bool Button ([Rect](https://docs.unity.cn/cn/2021.3/ScriptReference/Rect.html) position, [Texture](https://docs.unity.cn/cn/2021.3/ScriptReference/Texture.html) image, [GUIStyle](https://docs.unity.cn/cn/2021.3/ScriptReference/GUIStyle.html) style);

public static bool Button ([Rect](https://docs.unity.cn/cn/2021.3/ScriptReference/Rect.html) position, [GUIContent](https://docs.unity.cn/cn/2021.3/ScriptReference/GUIContent.html) content, [GUIStyle](https://docs.unity.cn/cn/2021.3/ScriptReference/GUIStyle.html) style);

### 返回

**bool** 当用户单击该按钮时，返回 /true/。

### 描述

创建一个单击按钮。当用户点击该按钮时，立即执行一些操作。

```
// Draws 2 buttons, one with an image, and other with a text
// And print a message when they got clicked.using UnityEngine;
using System.Collections;public class ExampleClass : MonoBehaviour
{
    public Texture btnTexture;    
    void OnGUI()
    {
        if (!btnTexture)
        {
            Debug.LogError("Please assign a texture on the inspector");
            return;
        }        
        if (GUI.Button(new Rect(10, 10, 50, 50), btnTexture))
            Debug.Log("Clicked the button with an image");
                    
        if (GUI.Button(new Rect(10, 70, 50, 30), "Click"))
            Debug.Log("Clicked the button with text");
    }
}
```



参考资料：[https://docs.unity.cn/cn/2021.3/ScriptReference/GUI.Button.html](https://docs.unity.cn/cn/2021.3/ScriptReference/GUI.Button.html)
