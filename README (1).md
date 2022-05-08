# Camera Controller

在FPS中，相机和角色头部运动保持一致，只需要实时同步两者的transform即可。

因此，可以把MainCamera拖到Player下；或者，在Player下创建一个名为”CameraPoint“的子物体移动其至头部（记得调整好下x,y,z轴的朝向），然后用下列脚本绑定MainCamera与CameraPoint。通过这种方式，可以更灵活地调用MainCamera。

![Camera Point](.gitbook/assets/Unity\_MuKhcXoNWy.png)

```
using UnityEngine;
public class CameraController : MonoBehaviour
{
    public Transform target;
    void LateUpdate()
    {
        transform.position = target.position;
        transform.rotation = target.rotation;
    }
}
```

第一人称视角下，通过鼠标操控Camera的旋转

```
public Transform camTransform;
public float mouseSensitivity;
void Update()
{
    //control camera rotation
    Vector2 mouseInput = new Vector2(Input.GetAxisRaw("Mouse X"), Input.GetAxisRaw("Mouse Y")) * mouseSensitivity;
    //通过控制player的俯仰角度，并且把camera和player绑定，来实现camera的俯仰
    transform.rotation = Quaternion.Euler(transform.rotation.eulerAngles.x, transform.rotation.eulerAngles.y + mouseInput.x, transform.rotation.eulerAngles.z);
    //下行代码作用和上行一样
    //transform.rotation = Quaternion.Euler(transform.rotation.eulerAngles + new Vector3(0f, mouseInput.x, 0f));
    //控制镜头左右转动
    camTransform.rotation = Quaternion.Euler(camTransform.rotation.eulerAngles + new Vector3(-mouseInput.y, 0f, 0f));
}
```

{% content-ref url="camera/transform.eulerangles-yu-transform.rotation.md" %}
[transform.eulerangles-yu-transform.rotation.md](camera/transform.eulerangles-yu-transform.rotation.md)
{% endcontent-ref %}

上述逻辑利用了欧拉角函数，而下面则会利用四元数，展示以上逻辑的另一种写法

```
public Transform camTransform;
public float mouseSensitivity;
void Update()
{
    Vector2 mouseInput = new Vector2(Input.GetAxisRaw("Mouse X"), Input.GetAxisRaw("Mouse Y")) * mouseSensitivity;
    transform.eulerAngles = transform.eulerAngles + new Vector3(0f, mouseInput.x, 0f);
    camTransform.eulerAngles = camTransform.eulerAngles + new Vector3(-mouseInput.y, 0f, 0f);
    //创建一个public GameObject cam；
    //然后cam.transform.eulerAngles = cam.transform.eulerAngles + new Vector3(-mouseInput.y, 0f, 0f);也可以
}
```
