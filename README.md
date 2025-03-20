#  Reinforcement Learning Projects 

This repository contains projects leveraging **Reinforcement Learning (RL)** for solving real-world problems. The projects focus on **robot path planning** and **voltage control in power systems**, applying deep RL techniques to optimize decision-making.

---

##  **Projects in this Repository**

###  **1. RL for Robot Path Planning**
- Applies **Deep Q-Learning (DQN)** and **Proximal Policy Optimization (PPO)** to navigate robots in dynamic environments.
- Uses **grid-based pathfinding** and reinforcement learning for obstacle avoidance.
-  [View Project](./Reinforcement_Learning_for_Robot_Path_Planning.ipynb)

###  **2. Reinforcement Learning for Voltage Control in Power Systems**
## **Overview**
This project explores **Reinforcement Learning (RL) for voltage regulation** in power grids using **Proximal Policy Optimization (PPO)**. It involves building a **custom OpenAI Gym environment** integrated with **pandapower** for power system simulations. The RL agent optimizes reactive power injection to maintain bus voltages within permissible limits.

## **Project Features**
- **Custom OpenAI Gym Environment**: Simulates a simple **three-bus power system** with controllable reactive power.
- **Pandapower Integration**: Real-time power flow simulations ensure realistic voltage control scenarios.
- **Reinforcement Learning with PPO**: Implements **Stable-Baselines3 PPO** to learn optimal voltage regulation strategies.
- **Reward Function Design**: Encourages the agent to minimize voltage deviations from the nominal value (1.0 p.u.).
- **Scalability**: Can be extended to larger networks and different RL algorithms.

## **Implementation Details**
### **Power System Model**
- **Network:** A 3-bus system with an external grid, transmission lines, and loads.
- **Control Variable:** Reactive power (Q) injected by a static generator (SGen).
- **Objective:** Maintain bus voltages within acceptable limits by adjusting Q dynamically.

### **Reinforcement Learning Setup**
- **State Space:** Voltage magnitudes of non-slack buses.
- **Action Space:** Continuous Q adjustment (`-0.5 ≤ Q ≤ 0.5`).
- **Reward Function:** Penalizes voltage deviations from 1.0 p.u.
- **Algorithm:** Proximal Policy Optimization (PPO) from Stable-Baselines3.

## **Installation & Usage**
### **Dependencies**
```bash
pip install gymnasium pandapower stable-baselines3 numpy
```
### **Run Training**
```python
from stable_baselines3 import PPO
from voltage_control_env import VoltageControlEnv

env = VoltageControlEnv()
model = PPO("MlpPolicy", env, verbose=1)
model.learn(total_timesteps=10000)
model.save("voltage_control_agent")
```
### **Test Trained Agent**
```python
model = PPO.load("voltage_control_agent")
obs, _ = env.reset()
done = False
while not done:
    action, _ = model.predict(obs)
    obs, reward, done, _, _ = env.step(action)
    print("Voltage State:", obs, "Reward:", reward)
```

## **Results & Future Work**
- The trained agent successfully regulates voltage within the expected range.
- Future improvements:
  - Implementing **LSTM-based RL agents** for better stability in dynamic grids.
  - Extending the environment to **multi-bus systems** with variable loads.
  - Exploring **multi-agent reinforcement learning (MARL)** for coordinated control.

## **References**
- [OpenAI Gym Documentation](https://gymnasium.farama.org/)
- [Pandapower Library](https://www.pandapower.org/)
- [Stable Baselines3](https://stable-baselines3.readthedocs.io/)
-  [View Project](./Reinforcement_Learning_for_Voltage_Control_in_Power_Systems.ipynb)

---

##  **How to Run the Projects?**
1. Clone this repository:  
   ```bash
   git clone https://github.com/your-username/Reinforcement_Learning_Projects.git
