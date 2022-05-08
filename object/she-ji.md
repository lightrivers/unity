# 射击

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
