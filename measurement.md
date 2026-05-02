这个过程在量子力学中被称为**冯·诺伊曼测量模型（von Neumann Measurement Model）**。它是将“测量”本身作为一个量子力学过程进行严格数学描述的标准框架。

以下是该演化过程的严格数学推导，分为四个核心步骤：

---

## 1. 希尔伯特空间与初始态的定义

我们首先定义两个量子系统：**被测系统 (System, S)** 和 **探测器/仪器 (Apparatus, A)**。

* **系统 $S$ 的状态空间 $\mathcal{H}_S$：**
    设待测量的物理量对应的算符为 $\hat{A}$，其本征态方程为：
    $$\hat{A}|\phi_n\rangle = a_n|\phi_n\rangle$$
    系统初始处于叠加态：
    $$|\psi\rangle_S = \sum_n c_n |\phi_n\rangle$$
    其中 $\sum_n |c_n|^2 = 1$。

* **仪器 $A$ 的状态空间 $\mathcal{H}_A$：**
    为了记录测量结果，仪器必须有一个连续的“指针”变量。我们用位置算符 $\hat{Q}$ 和动量算符 $\hat{P}$ 来描述仪器的指针，满足对易关系 $[\hat{Q}, \hat{P}] = i\hbar$。
    设仪器的初始状态为 $|\Phi_0\rangle_A$，在位置表象下，这是一个以 $q=0$ 为中心的波包 $\Phi_0(q) = \langle q|\Phi_0\rangle$。

* **系统与仪器的初始总态：**
    在相互作用发生前，两者相互独立，总希尔伯特空间 $\mathcal{H}_{total} = \mathcal{H}_S \otimes \mathcal{H}_A$ 中的总态为直积态：
    $$|\Psi(0)\rangle = |\psi\rangle_S \otimes |\Phi_0\rangle_A = \left( \sum_n c_n |\phi_n\rangle \right) \otimes |\Phi_0\rangle_A$$

---

## 2. 相互作用哈密顿量与幺正演化

为了让仪器“感知”到系统，我们引入耦合。假设这是一个**脉冲式测量（Impulsive Measurement）**，即相互作用时间极短且强度极大，此时可以忽略系统和仪器自身的自由演化哈密顿量。

* **相互作用哈密顿量 $H_{int}$：**
    $$H_{int} = g(t) \hat{A} \otimes \hat{P}$$
    其中 $g(t)$ 是时间分布函数，表示耦合仅在 $t \in [0, \tau]$ 内存在。我们定义总耦合强度 $\lambda = \int_0^\tau g(t) dt$。

* **时间演化算符 $\hat{U}$：**
    根据薛定谔方程，系统演化的幺正算符为：
    $$\hat{U} = \exp\left( -\frac{i}{\hbar} \int_0^\tau H_{int} dt \right) = \exp\left( -\frac{i}{\hbar} \lambda \hat{A} \otimes \hat{P} \right)$$

---

## 3. 指针平移与理想纠缠态的生成

现在，我们将演化算符作用于初始总态，这是整个理论中最精妙的一步数学操作：

$$|\Psi(\tau)\rangle = \hat{U} |\Psi(0)\rangle = \exp\left( -\frac{i}{\hbar} \lambda \hat{A} \otimes \hat{P} \right) \left[ \sum_n c_n |\phi_n\rangle \otimes |\Phi_0\rangle \right]$$

由于算符 $\hat{A}$ 作用在本征态 $|\phi_n\rangle$ 上会给出本征值 $a_n$，我们可以将指数算符展开并作用于具体的项：

$$|\Psi(\tau)\rangle = \sum_n c_n |\phi_n\rangle \otimes \left[ \exp\left( -\frac{i}{\hbar} \lambda a_n \hat{P} \right) |\Phi_0\rangle \right]$$

**关键数学性质：** 在量子力学中，动量算符 $\hat{P}$ 是空间平移的生成元。算符 $\exp(-i x \hat{P} / \hbar)$ 会将位置态波函数平移 $x$ 的距离。因此，令平移后的仪器态为 $|\Phi_n\rangle$：
$$|\Phi_n\rangle = \exp\left( -\frac{i}{\hbar} \lambda a_n \hat{P} \right) |\Phi_0\rangle$$
在位置表象下，这表示仪器的波包中心从 $0$ 移动到了 $\lambda a_n$：
$$\langle q|\Phi_n\rangle = \Phi_0(q - \lambda a_n)$$

最终相互作用结束后的总态变成了**纠缠态（Entangled State）**：
$$|\Psi(\tau)\rangle = \sum_n c_n |\phi_n\rangle \otimes |\Phi_n\rangle$$
此时，仪器的指针位置 $\lambda a_n$ 已经与被测系统的本征态 $|\phi_n\rangle$ 建立了严格的一一对应关系。

---
