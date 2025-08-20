# Self-Driving Car Simulation with Reinforcement Learning

## Overview

This project explores training autonomous car agents using deep reinforcement learning (RL) methods to navigate a custom environment. Two different input modalities were compared: a **Single-Stack Image Agent** and a **Stacked Frame Agent**, each implemented using the **Proximal Policy Optimization (PPO)** algorithm in the Unity ML-Agents environment.

## Methodology

- **Environment:** A Unity-based simulation designed to test continuous control of a car navigating a track, receiving visual observations.
- **Reinforcement Learning Algorithm:** PPO (Proximal Policy Optimization), a policy gradient method that stabilizes training through clipped objective functions.
- **Agents:**
  - **Single-Stack Agent:** Processes a single grayscale frame (image) per timestep.
  - **Stacked Frame Agent:** Processes a stack of the last 4 frames, giving the agent temporal context (velocity/movement).
- **Reward Design:** Agents were rewarded based on forward progress and penalized for off-track behavior or collisions.

## Training Configuration

- PPO configuration included:
  - Learning rate: `3e-4`
  - Batch size: `1024`
  - Buffer size: `20480`
  - Hidden units: `256`
  - Max steps: `1 million`
  - Time horizon: `64`
- Input preprocessing:
  - Grayscale image (84x84 resolution)
  - Normalization applied
  - Frame skipping in stack agent

## Results

- **Performance Comparison:**
  - The **Single-Stack Agent** showed more consistent and stable performance, converging to higher cumulative rewards more quickly.
  - The **Stacked Frame Agent**, while incorporating more temporal information, struggled with convergence and displayed higher variance in training.

- **Evaluation:**
  - Single-Stack Agent reached higher average episodic reward (~470 vs ~310).
  - Stacked Frame Agent demonstrated slower learning and greater instability in action selection.

## Conclusion

Using a **single grayscale frame per timestep** proved more effective for the given task and environment setup. The increased complexity from stacking frames did not improve performance, likely due to redundancy or instability in PPO updates with more input channels.

## Tools & Libraries

- Unity ML-Agents Toolkit
- TensorFlow / PyTorch (via ML-Agents)
- PPO Algorithm (Unity’s implementation)
- NumPy, OpenCV for preprocessing



COMP47590 — Assignment 2, University College Dublin
