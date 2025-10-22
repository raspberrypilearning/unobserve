在 JavaScript 中，`unobserve` 方法与交叉观察器一起使用来停止观察目标元素。

你可以使用 `unobserve` 来停止触发动画，或者避免内存或性能问题。

以下是 [更多 Web](https://projects.raspberrypi.org/zh-CN/raspberrypi/more-web) 路径中的 [动画故事](https://projects.raspberrypi.org/zh-CN/projects/animated-story) 项目使用  `unobserve` 的示例：

--- code ---
---
language: js
filename:
line_numbers: true
line_number_start: 1
line_highlights: 6
---

// 隐藏弹跳观察器
const bounceObserver = new IntersectionObserver((entries) => {
  if (entries[0].isIntersecting) {
    console.log("视口中的弹跳触发器");
    document.querySelector("#bounce").style.opacity = 0;
    bounceObserver.unobserve(entries[0].target);
  }
});
bounceObserver.observe(document.querySelector("#hideBounce"));

--- /code ---

在第 6 行，调用 `bounceObserver` 来 `unobserve` 目标条目（带有 `id="hideBounce"` 的元素）。

这避免了内存或性能问题，因为一旦元素被隐藏，就不需要继续观察它。
