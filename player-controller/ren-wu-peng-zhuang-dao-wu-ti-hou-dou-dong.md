# 人物碰撞到物体后抖动

把 Rigidbody 组件里的 Angular Drag 改成 Infinity就不会抖动了。或者加上Constraints约束角色抖动。

![Angular Drag](../.gitbook/assets/Unity\_axOU8cUy8l.png)

Rigidbody中 **Angular Drag**  （角阻力）：同样指的是空气阻力，只不过是用来阻碍物体旋转的。如果设置成无限的话，物体会立即停止旋转。如果设置成0，物体在上升过程中，会发生侧翻旋转。

![Constraints](<../.gitbook/assets/image (4).png>)

**Freeze Position/Rotation**（冻结位置/旋转）： 可以对物体在X、Y、Z三个轴上的位置/旋转进行锁定，即使受到相应的力也不会改变，但可以通过脚本来修改。否则物体在上升过程中会发生飘动（不仅y轴变化，X,Z也在变，不想这种现象，就把X，Z锁定）
