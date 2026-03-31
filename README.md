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
