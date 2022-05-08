# Transform.eulerAngles与transform.rotation

**Transform.eulerAngles**&#x20;

在世界空间坐标物体旋转的欧拉角 直接对eulerAngles可以使用vector3（）而不能使用Quatertion.Euler

Obj2.transform.eulerAngles = new Vector3(0, 10, 0);

**transform.rotation**&#x20;

在世界空间坐标物体旋转的四元数

直接对rotation赋值时需要使用Quatertion.Euler而不能直接使用vector3（）

Obj2.transform.rotation = Quaternion.Euler(0, 10\*Time.time, 0);&#x20;
