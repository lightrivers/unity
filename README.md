# Camera Controller



```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.SceneManagement;

public class PlayerController : MonoBehaviour
{
    public float speed;

    Animator animator;
    Vector3 movement;
    Rigidbody2D rbody;
    //public AudioClip walkAudio;
    // public AudioSource audioSource;
    // public AudioClip leaveAudio;
	
    // Start is called before the first frame update
    void Start()
    {
        animator = GetComponent<Animator>();
        rbody = GetComponent<Rigidbody2D>();
    }

    // Update is called once per frame
    void Update()
    {
        //movement = new Vector3(Input.GetAxisRaw("Horizontal") * Time.deltaTime * speed, Input.GetAxisRaw("Vertical") * Time.deltaTime * speed, 0);
        //transform.Translate(movement);//移动   把移动放到FixedUpdate可优化碰撞抖动效果

        if (movement.x > 0)//动画
        {
            // audioSource.PlayOneShot(walkAudio,2.0f);
            animator.SetBool("running", true);
        }
        else if (movement.x < 0)//动画
        {
            // audioSource.PlayOneShot(walkAudio);
            animator.SetBool("left", true);
        }
        else if(movement.y > 0)
        {
            // audioSource.PlayOneShot(walkAudio);
            animator.SetBool("goup", true);
        }
        else if(movement.y < 0)
        {
            // audioSource.PlayOneShot(walkAudio,2.0f);
            animator.SetBool("godown", true);
        }
        else
        {
            animator.SetBool("running", false);
            animator.SetBool("goup", false);
            animator.SetBool("godown", false);
            animator.SetBool("left", false);
        }
        
    }
    void FixedUpdate()
    {
        movement = new Vector3(Input.GetAxisRaw("Horizontal") * Time.deltaTime * speed, Input.GetAxisRaw("Vertical") * Time.deltaTime * speed, 0);
        transform.Translate(movement);//移动
        //audioSource.PlayOneShot(walkAudio);
    }

    private void OnTriggerEnter2D(Collider2D other)
    {
        if (other.gameObject.tag == "Bathroom") //玩家碰到tag为Bathroom的物体
        {
            // audioSource.PlayOneShot(leaveAudio,2.0f);
            GameManager.GM.S2(); //调用GameManager里的loadscene函数来切换场景
        }
        else if (other.gameObject.tag == "Restroon")
        {
            // audioSource.PlayOneShot(leaveAudio,2.0f);
            GameManager.GM.S3();
        }
        else if (other.gameObject.tag == "bedroon")
        {
            // audioSource.PlayOneShot(leaveAudio,2.0f);
            GameManager.GM.S3();
        }
    }
}

```
