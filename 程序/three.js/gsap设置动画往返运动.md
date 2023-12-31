## GSAP 设置动画往返运动详解

### 往返运动（Yoyo）

1. **定义：**
   - 往返运动是指动画在正向播放完毕后，以相反的方向回到初始状态。在 GSAP 中，这一特性被称为 "yoyo"。

2. **用法：**
   - 使用 `yoyo` 属性设置往返运动，该属性接受一个布尔值。

3. **示例代码：**
   ```javascript
   gsap.to(".element", {
     x: 100,
     duration: 2,
     yoyo: true,
     repeat: 1, // 重复次数（可选）
     onComplete: () => {
       console.log("Animation completed!");
     }
   });
   ```

4. **作用：**
   - 当 `yoyo` 设置为 `true` 时，动画会在正向播放结束后，以相反方向返回初始状态，形成往返效果。

5. **其他属性：**
   - `repeat`：可以设置往返运动的重复次数。在上述例子中，`repeat: 1` 表示动画正向播放和反向播放各执行一次。

6. **注意事项：**
   - 确保动画设置了足够的 `duration`，以便在正向和反向运动之间有足够的时间。

### 总结：

- GSAP 的 `yoyo` 功能允许简单而有效地创建往返运动的动画效果。
- 通过调整 `repeat` 属性，可以控制往返运动的重复次数。
- 适用于需要来回移动的元素或循环效果的动画。