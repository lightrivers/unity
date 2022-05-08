# 重力Gravity

Physics.gravity 的初始值为 (0,-9.8,0)



```
    float yStore = moveInput.y;
    //此处为控制平面上移动的代码，略
    moveInput.y = yStore;
    moveInput.y += Physics.gravity.y * Time.deltaTime * gravityModifier;

    if(charCon.isGrounded)
    {
        moveInput.y = Physics.gravity.y * Time.deltaTime * gravityModifier;
    }
```
