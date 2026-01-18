# 👋 Hi, I'm 榴莲不进

> C++ / Linux 后端开发学习者  
> Focus on 网络编程 · 并发模型 · 系统设计

---

## 🧭 About Me

- 🎓 方向：C++ / Linux 后端开发
- 🔧 关注领域：
  - Linux 网络编程（TCP / epoll）
  - 多线程与并发模型
  - 高性能服务器设计
- 📚 当前状态：系统性学习 + 项目实战
- 🎯 目标：具备独立设计与实现中型后端系统的能力

---

## 🛠 Tech Stack

### Programming Languages
![C++](https://img.shields.io/badge/C++-17/20-blue?logo=cplusplus)
![C](https://img)

import { createAnimatable, utils } from 'animejs';

const $demos = document.querySelector('#docs-demos');
const $demo = document.querySelector('.docs-demo.is-active');
const [ $x, $y ] = utils.$('.coords');
let bounds = $demo.getBoundingClientRect();
const refreshBounds = () => bounds = $demo.getBoundingClientRect();

const circle = createAnimatable('.circle', {
  x: 500,
  y: 500,
  ease: 'out(2)',
});

// Gets and log the current x and y values
circle.animations.x.onRender = () => {
  $x.innerHTML = utils.roundPad(circle.x(), 2);
  $y.innerHTML = utils.roundPad(circle.y(), 2);
}

const onMouseMove = e => {
  const { width, height, left, top } = bounds;
  const hw = width / 2;
  const hh = height / 2;
  const x = utils.clamp(e.clientX - left - hw, -hw, hw);
  const y = utils.clamp(e.clientY - top - hh, -hh, hh);
  // Sets x and y values
  circle.x(x);
  circle.y(y);
}

window.addEventListener('mousemove', onMouseMove);
$demos.addEventListener('scroll', refreshBounds);
