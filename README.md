# Page 2

重力

```
    float yStore = moveInput.y;
    moveInput.y = yStore;
    moveInput.y += Physics.gravity.y * Time.deltaTime * gravityModifier;

    if(charCon.isGrounded)
    {
        moveInput.y = Physics.gravity.y * Time.deltaTime * gravityModifier;
    }
```
