# Camera Controller

在FPS中，相机和角色头部运动保持一致，只需要实时同步两者的transform即可。

因此，可以把MainCamera拖到Player下；或者，在Player下创建一个名为”CameraPoint“的子物体移动其至头部（记得调整好下x,y,z轴的朝向），然后用下列脚本绑定MainCamera与CameraPoint。通过这种方式，可以更灵活地调用MainCamera。

![Camera Point](../.gitbook/assets/Unity\_MuKhcXoNWy.png)

```
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
