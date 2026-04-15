**Lab assignments for MIT Course 6.S184: Generative AI with Stochastic Differential Equations**

# Lab One: Simulating ODEs and SDEs
本实验主要学习**常微分方程（ODE）** 与**随机微分方程（SDE）** 的定义、数值解法与可视化，理解随机过程如何改变样本分布。
## 实验结构
### 0. 引言
- ODE 形式：
$$dX_t = u_t(X_t)dt$$
- SDE 形式：
$$dX_t = u_t(X_t)dt + \sigma_t dW_t$$
- ODE 可看作扩散项为 0 的特殊 SDE
### 1. 数值模拟方法
实现两种基础数值求解器：
- **Euler 法**：用于 ODE 数值模拟
- **Euler-Maruyama 法**：用于 SDE 数值模拟
- 当扩散系数为 0 时，两者完全等价
### 2. SDE 解的可视化
实现并观察两类经典随机过程：
#### （1）布朗运动（Brownian Motion）
- 方程：
$$dX_t = \sigma dW_t$$
- 分析 $\sigma$ 对轨迹波动幅度的影响
#### （2）奥恩斯坦-乌伦贝克过程（OU 过程）
- 方程：
$$dX_t = -\theta X_t dt + \sigma dW_t$$
- 具有**均值回归**特性
- 稳态分布：N(0, σ²/2θ)
- 观察 $\theta$ 大小对回归速度的影响
### 3. 使用 SDE 变换分布（朗之万动力学）
重点：**朗之万动力学** 可将样本逐步引导至目标分布 $\pi$
- 朗之万方程形式：
$$dX_t = \frac{1}{2}\sigma^2\nabla\log p(X_t)dt + \sigma dW_t$$
- 实现漂移项、扩散项
- 证明：**OU 过程是朗之万动力学的特例** 
## 实验收获
- 掌握 ODE/SDE 基本形式与区别
- 实现 Euler / Euler-Maruyama 数值解法
- 直观理解布朗运动、OU 过程行为
- 初步理解**分数匹配（score-based）** 与朗之万采样思想
## 后续实验
- Lab Two: Flow Matching and Score Matching
- Lab three: A Conditional Generative Model for Images
