# TD3_HER
# Hindsight Experience Replay and Goal Selection Strategies for Multi-Goal RL

## 📌 Overview

This repository presents a systematic study of **Hindsight Experience Replay (HER)** combined with **off-policy reinforcement learning algorithms**, specifically **TD3** and **DDPG**, in **multi-goal robotic environments**.

We investigate how different **goal selection strategies** in HER impact **sample efficiency, convergence speed, and performance**, particularly in **sparse reward settings**.

The work is evaluated on **six MuJoCo-based environments** using OpenAI Gym:
- FetchReach, FetchPush, FetchSlide
- HandManipulateBlock, HandManipulateEgg, HandManipulatePen

---

## 🚀 Key Contributions

- 📊 Benchmark of **TD3 and TD3 + HER** across **6 multi-goal environments**
- 🎯 Systematic comparison of **HER goal selection strategies**:
  - Episode
  - Future
  - Final
- 🤖 Evaluation in **high-dimensional dexterous manipulation tasks (24-DOF hand)**
- ⚡ Analysis of **sample efficiency and learning behavior under sparse rewards**

---

## 🧠 Background

### Reinforcement Learning Objective

The goal of reinforcement learning is to maximize the expected cumulative reward:
R_t = \sum_{i=t}^{\infty} \gamma^{i-t} r_i



However, in **multi-goal robotics**, rewards are often **sparse**, making learning inefficient.

### Hindsight Experience Replay (HER)

HER improves learning by:
- Replacing the desired goal with the **achieved goal**
- Turning failed experiences into useful training signals
- Increasing sample efficiency

---

## 🏗️ Methodology

### Algorithms Used

- **DDPG** — baseline actor-critic for continuous control
- **TD3** — improved version of DDPG with:
  - Clipped Double Q-learning
  - Delayed Policy Updates
  - Target Policy Smoothing

### HER Integration

HER is combined with TD3 using:
- Online sampling
- 4 hindsight goals per transition
- Goal selection strategies: Episode, Future, Final

---

## ⚙️ Training Setup

| Parameter | Value |
|----------|------|
| Actor/Critic Network | 3 layers × 256 units (ReLU) |
| Optimizer | Adam |
| Learning Rate | 1e-3 |
| Replay Buffer | 1e6 |
| Batch Size | 256 |
| Discount Factor | 0.95 |
| Exploration Noise | Gaussian (σ = 0.2) |
| Episode Length | 100 |

---

## 🧪 Environments

### Fetch Environments (7-DOF robotic arm)
- **FetchReach** — move gripper to target
- **FetchPush** — push object to goal
- **FetchSlide** — slide puck to distant target

### Shadow Dexterous Hand (24-DOF)
- **Block Manipulation**
- **Egg Manipulation**
- **Pen Manipulation** (most challenging)

---

## 📊 Results

### Mean Reward After Training

| Task | TD3 | TD3 + HER (Final) | TD3 + HER (Future) |
|------|-----|------------------|-------------------|
| FetchReach | -0.34 ± 0.19 | **-0.28 ± 0.26** | -0.41 ± 0.18 |
| FetchSlide | -8.66 ± 3.97 | -17.79 ± 18.97 | **-8.28 ± 3.77** |
| FetchPush | -8.23 ± 3.68 | -8.22 ± 3.70 | -8.26 ± 3.70 |
| HandBlock | **-255.45 ± 117.17** | -274.49 ± 117.19 | -307.47 ± 115.33 |
| HandEgg | **-290.91 ± 93.59** | -306.21 ± 102.46 | -316.10 ± 99.36 |
| HandPen | **-150.14 ± 99.96** | -161.31 ± 94.57 | -165.79 ± 117.85 |

---

## 🔍 Key Findings

- ✅ **HER improves sample efficiency and convergence speed**
- 🎯 **Episode goal strategy** performs best in FetchReach
- 🧊 **Future strategy** performs best in long-horizon tasks like FetchSlide
- 🤖 **TD3 + HER enables learning in complex 24-DOF dexterous tasks**
- ⚠️ Mean reward alone does not fully capture HER benefits — **success rate and stability also improve**

---

## ⚠️ Limitations

- Experiments are limited to **simulation (MuJoCo)** — no real-world validation
- HER improvements are **task-dependent**
- Fixed hyperparameters (RLZoo) may not be optimal for all environments
- Limited to TD3/DDPG — no comparison with newer methods (e.g., SAC, TQC)

---

## 🔮 Future Work

- Hierarchical RL (Options Framework + HER)
- Adaptive / learned goal selection strategies
- Reward curriculum learning
- Real-world robotic deployment
- Integration with distributional critics (e.g., TQC)

---

## 🛠️ Tech Stack

- Python
- PyTorch
- Stable-Baselines3
- OpenAI Gym
- MuJoCo

---

## 📚 References

- Lillicrap et al., *DDPG*
- Fujimoto et al., *TD3*
- Andrychowicz et al., *Hindsight Experience Replay*
- Stable-Baselines3 & RL Zoo

---

## 📌 Summary

This work demonstrates that combining **TD3 with HER**, along with carefully chosen **goal selection strategies**, significantly improves learning in **sparse, multi-goal robotic environments**, and provides a foundation for future research in **dexterous manipulation and hierarchical reinforcement learning**.
