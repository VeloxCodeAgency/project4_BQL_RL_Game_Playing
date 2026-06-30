# Deep Reinforcement Learning for Game Playing 🎮🤖
### Training an AI Agent to Play CartPole using Deep Q-Networks (DQN)

A from-scratch implementation of a **Deep Q-Network (DQN)** agent trained to solve the classic `CartPole-v1` environment from OpenAI Gym (Gymnasium). This project demonstrates the foundational building blocks of modern reinforcement learning systems used in autonomous decision-making AI.

---

## 🚀 Live / Notebook
📓 **Google Colab Notebook:** `DQN_Deep_RL_Game_Playing.ipynb`

---

## 📌 Overview

The agent learns to balance a pole on a moving cart purely through trial and error — receiving a reward for every timestep the pole stays upright, and learning over thousands of episodes which actions lead to long-term success.

This project implements the core algorithm from DeepMind's original DQN paper (*Mnih et al., 2015*), adapted for a lightweight classic-control environment so it trains in minutes on free Colab resources, while remaining directly extensible to Atari games like Pong and Breakout.

---

## 🧠 Key Features

- **Deep Q-Network (DQN):** A fully connected neural network (PyTorch) that approximates Q-values for each possible action given a state.
- **Experience Replay Buffer:** Stores past transitions and samples random mini-batches during training, breaking correlation between consecutive experiences and stabilizing learning.
- **Epsilon-Greedy Exploration:** Balances exploration vs. exploitation, with epsilon decaying exponentially over training steps.
- **Target Network:** A periodically-updated copy of the policy network used to compute stable Q-value targets, preventing the "moving target" instability problem.
- **Reward & Loss Visualization:** Tracks and plots episode rewards (with moving average) and training loss over time.
- **Model Evaluation & Saving:** Runs the trained policy greedily to measure performance, and saves the final model weights.
- **Atari-Ready Architecture:** Includes a dedicated section explaining exactly how to extend the same pipeline to Atari games using CNNs and frame stacking.

---

## 🛠️ Technologies & Tools Used

| Category | Tools |
|---|---|
| Language | Python |
| Deep Learning Framework | PyTorch |
| RL Environment | OpenAI Gym / Gymnasium (`CartPole-v1`) |
| Visualization | Matplotlib |
| Numerical Computing | NumPy |
| Development Environment | Google Colab |

---

## ⚙️ How It Works

1. **Environment Setup** — `CartPole-v1` provides a 4-dimensional state (cart position, cart velocity, pole angle, pole angular velocity) and 2 discrete actions (push left / push right).
2. **Action Selection** — The agent selects actions using an epsilon-greedy policy: random exploration early in training, increasingly relying on the learned Q-network as epsilon decays.
3. **Experience Storage** — Each transition `(state, action, reward, next_state, done)` is stored in a replay buffer.
4. **Learning Step** — A random batch is sampled from the replay buffer. The policy network predicts Q-values, the target network computes stable target Q-values, and the network is updated by minimizing the Smooth L1 (Huber) loss between them.
5. **Target Network Sync** — Every few episodes, the target network's weights are updated to match the policy network, keeping training stable.
6. **Evaluation** — After training, the agent is run greedily (no exploration) to measure how consistently it can solve the task.

---

## 📈 Results

The agent's performance is tracked across training episodes and visualized as:
- Episode reward curve (raw + moving average)
- Training loss curve

The environment is considered "solved" when the agent consistently achieves rewards close to the maximum (500) over recent episodes.

---

## 🔮 Future Extensions

- Extend to **Atari environments** (Pong, Breakout) using CNN-based feature extraction and frame stacking
- Implement **Double DQN** to reduce Q-value overestimation
- Implement **Dueling DQN** architecture
- Add **Prioritized Experience Replay**
- Combine techniques into a **Rainbow DQN** agent

---

## 👤 Author

**Maryam Saif**

[GitHub](https://github.com/saifmaryam) | [LinkedIn](#) | [Hugging Face](#)

---

## 📄 License

This project is open-sourced for educational and portfolio purposes.
