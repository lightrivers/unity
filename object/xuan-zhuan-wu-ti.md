# 旋转物体

transform.Rotate()

运行以下代码，对象的旋转一直是在累加5

```
void Update()
    {    
        transform.Rotate(Vector3.up  * 5);
    }
```

Rotate方法是：旋转多少度。在原有的基础上累加，即旋转了多少角度。又旋转了多少角度，是在原有的基础上在旋转。

transform.rotation()

运行下列代买，对象旋转到5就不动了。也就是每次旋转都是同样的值。

```
void Update()
{
    transform.rotation = Quaternion.Euler(Vector3.up  * 5);
}
```

rotation方法是：旋转到某个角度，就是是在update中每帧都执行（我这里测试是放在了update中）。但每次旋转到的角度动是5，所以一直都是旋转到5度。

**总结：**

比如你只想让他旋转到多少,用rotation; 假如想让他一直转,可以用Rotate
