# 射击

首先制作子弹的预制体（BulletPrefab，需要有Rigidbody），然后创建一个空的GameObject（BulletSpawn，记得z轴需要瞄准发射的方向），然后用[Object](https://docs.unity.cn/cn/2019.4/ScriptReference/Object.html).Instantiate在BulletSpawn的位置生成子弹。

最后用GetComponent\<Rigidbody>().velocity给子弹赋予初速度。

```
public class Shoot : MonoBehaviour
{
    public GameObject BulletPrefab;
    public Transform BulletSpawn;
    public float BulletSpeed;
    void Update()
    {
        if(Input.GetButtonDown("Fire2"))
        {
            GameObject bullet = Instantiate(BulletPrefab, BulletSpawn.position, BulletSpawn.rotation);
            bullet.GetComponent<Rigidbody>().velocity = bullet.transform.forward * BulletSpeed;
            Destroy(bullet, 2);
        }
    }
}
```

## [Object](https://docs.unity.cn/cn/2019.4/ScriptReference/Object.html).Instantiate

public static Object Instantiate ([Object](https://docs.unity.cn/cn/2019.4/ScriptReference/Object.html) original, [Vector3](https://docs.unity.cn/cn/2019.4/ScriptReference/Vector3.html) position, [Quaternion](https://docs.unity.cn/cn/2019.4/ScriptReference/Quaternion.html) rotation);

### 描述

克隆 `original` 对象并返回克隆对象。
