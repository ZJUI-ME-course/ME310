好的，这张照片包含了流体力学中一些核心概念和公式的笔记。我会将内容进行分类，然后逐一详细讲解。

### 1. 流线 (Stream Line)

---

* **定义**: 流线是某一瞬时，流场中每个点的速度向量的切线。它描绘了流体质点在该瞬间的运动方向。流线不交叉，除非速度为零（即滞止点）。
* **数学表示**:
    * $d\vec{r} \times \vec{V} = 0$
    * $\frac{dx}{u} = \frac{dy}{v} = \frac{dz}{w}$
* **函数**:
    * 对于二维流动，流线函数 $\Psi(x, y)$ 被定义，其梯度与速度垂直。
    * $u = \frac{\partial \Psi}{\partial y}$
    * $v = -\frac{\partial \Psi}{\partial x}$
    * 流线函数 $\Psi$ 沿流线是常数。

---

### 2. 连续性方程 (Equation of Continuity)

---

* **物理意义**: 质量守恒定律在流体力学中的体现。在一个控制体中，流入的质量减去流出的质量，等于该控制体内质量的变化率。
* **数学表示**:
    * **微分形式**: $\frac{\partial \rho}{\partial t} + \nabla \cdot (\rho \vec{V}) = 0$
    * **不可压缩流体**: $\nabla \cdot \vec{V} = 0$，即 $\frac{\partial u}{\partial x} + \frac{\partial v}{\partial y} + \frac{\partial w}{\partial z} = 0$。这是因为密度 $\rho$ 为常数。

---

### 3. 控制体分析 (Control Volume Analysis)

---

这部分笔记是围绕流体动量、能量和质量守恒的积分形式展开的，通常用于解决工程问题。

* **雷诺输运定理 (Reynolds Transport Theorem, RTT)**: 这是一个非常重要的定理，它将系统的瞬时变化率与控制体内的瞬时变化率联系起来。
    * $\frac{dB_{sys}}{dt} = \frac{\partial}{\partial t}\int_{CV} \beta \rho d\mathcal{V} + \int_{CS} \beta \rho \vec{V} \cdot d\vec{A}$
    * **B**: 任意的广延量，如质量、动量、能量。
    * **$\beta$**: 对应的广延量除以质量得到的集约量。
    * **CV**: 控制体，一个固定或运动的空间区域。
    * **CS**: 控制体的表面。
    * **$\int_{CV}$**: 控制体内的变化率。
    * **$\int_{CS}$**: 流经控制体表面的通量。

* **动量守恒 (Conservation of Momentum)**:
    * 牛顿第二定律的流体力学形式：$\sum\vec{F} = \frac{d\vec{P}_{sys}}{dt}$ (其中 $\vec{P}$ 是动量)
    * 使用RTT，可得到动量方程的控制体形式：
        $\sum\vec{F} = \frac{\partial}{\partial t}\int_{CV} \vec{V} \rho d\mathcal{V} + \int_{CS} \vec{V} \rho (\vec{V} \cdot d\vec{A})$
    * **力**: 表面力 (如压力、黏性力) 和体积力 (如重力)。

* **能量守恒 (Conservation of Energy)**:
    * 热力学第一定律的流体力学形式。
    * $W_{shaft} - W_{shear} - W_{other} + Q = \frac{dE_{sys}}{dt}$
    * 其中 $E_{sys}$ 是系统的总能量，包括内能、动能、势能。
    * $W$ 代表功， $Q$ 代表热量。
    * 同样使用RTT，可以推导出能量方程的控制体形式。

---

### 4. 纳维-斯托克斯方程 (Navier-Stokes Equations)

---

* **物理意义**: 这是描述黏性流体运动的微分方程组，是流体力学的核心。它源自牛顿第二定律，考虑了流体的惯性力、压力梯度力、黏性力 (切应力) 和体积力 (如重力)。
* **数学表示**:
    * **一般形式**: $\rho \frac{D\vec{V}}{Dt} = -\nabla P + \mu \nabla^2 \vec{V} + \vec{f}_{body}$
        * $\rho \frac{D\vec{V}}{Dt}$: 惯性项，其中 $\frac{D}{Dt}$ 是物质导数。
        * $-\nabla P$: 压力梯度力。
        * $\mu \nabla^2 \vec{V}$: 黏性力项。
        * $\vec{f}_{body}$: 体积力，如重力。

    * **分量形式**: 笔记中列出了在**笛卡尔坐标系**和**圆柱坐标系**下的表达式。
        * **笛卡尔**: 笔记中 $x, y, z$ 三个方向的方程。
        * **圆柱**: 笔记中 $r, \theta, z$ 三个方向的方程。这些方程形式更复杂，但对于分析管内流、旋转流等问题非常有用。

* **欧拉方程 (Euler Equation)**: 纳维-斯托克斯方程的无黏形式。当黏性力可以忽略不计时，方程大大简化。
    * $\rho \frac{D\vec{V}}{Dt} = -\nabla P + \vec{f}_{body}$
    * 常用于分析无摩擦的理想流体流动。

---

### 5. 其他概念

---

* **黏性 (Viscosity)**: 流体抵抗变形或流动的能力。笔记中提到了剪切应力 $\tau$ 和剪切速率 $\frac{du}{dy}$ 的关系。牛顿流体满足 $\tau = \mu \frac{du}{dy}$。
* **势流 (Potential Flow)**: 一种假设，流体是**无黏**且**无旋**的。
    * **无旋**：$\nabla \times \vec{V} = 0$，即涡量 $\vec{\omega}$ 为零。
    * **速度势函数** $\Phi$: 满足 $\vec{V} = \nabla \Phi$。
    * 结合无旋和连续性方程（不可压缩），得到拉普拉斯方程 $\nabla^2 \Phi = 0$。

* **伯努利方程 (Bernoulli Equation)**:
    * 这是在特定条件下（稳定、无黏、不可压缩）的动量方程积分形式。它表明流体沿同一流线运动时，压力、速度和高度三者之间存在守恒关系。
    * $P + \frac{1}{2}\rho V^2 + \rho g z = \text{常数}$

总的来说，这份笔记涵盖了流体力学课程的核心骨架：从基本的流体运动描述（流线、连续性方程），到更深入的控制体积分分析，再到描述流体运动的微分方程（纳维-斯托克斯方程），并引入了简化模型（欧拉方程、势流）和重要定理（雷诺输运定理）。这些内容构成了流体力学的基础理论体系。