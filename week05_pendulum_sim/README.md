# 第 5 周实验：单摆仿真（Pendulum Simulation）

## 实验者信息

- 姓名：刘宇彬
- 学号：5904126080

## 无菌工作区就绪状态

- 目录路径：`week05_pendulum_sim/`
- 隔离范围：本目录仅存放第 5 周单摆仿真实验相关文件，不引用、不混入其他周次的实验产物。
- 依赖项：独立于其他周次，不共享中间产物与生成文件。
- 就绪状态：✅ 基线提交时目录内仅含 README.md（无菌 clean 基线）；后续新增文件均限制在本目录内，无跨周次混入。

## 目录说明

| 路径 | 说明 |
| --- | --- |
| `README.md` | 本文件，实验说明与工作区状态声明 |
| `index.html` | 单摆模拟器（单文件，原生 Canvas，无外部依赖，双击即可运行） |
| `index_buggy_demo.html` | 任务四排错演练版：原始含 ReferenceError 缺陷，保留并已修复，用于实验记录与 Git 留痕 |

## 任务四排错记录

**`index_buggy_demo.html`** 源自课程提供的演练代码，原版缺陷如下：

- 报错：点击「重置摆动」后控制台抛出 `Uncaught ReferenceError: resetAnimation is not defined at HTMLButtonElement.onclick`
- 根因：按钮内联 `onclick="resetAnimation()"` 在全局作用域查无此标识符；脚本里同名函数实为 `resetSimulationState()`，名称不一致 → 错误只在点击触发时抛出
- 修复：
  1. 删除按钮的内联 `onclick` 属性
  2. 将函数统一重命名为 `resetAnimation()`
  3. 改用 `addEventListener('click', resetAnimation)` 在脚本作用域内绑定
- 验收：MS Edge headless 探针（自动 click + 错误监听 + 状态断言） → `PASS`，`errCount=0`，点击后 `angle = π/4` 精准复位

## Git 基线

首次提交信息：`feat(week05): init pendulum experiment workspace`
