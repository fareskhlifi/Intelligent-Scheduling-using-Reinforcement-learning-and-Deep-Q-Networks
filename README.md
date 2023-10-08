# Intelligent Scheduling in Wireless Sensor Networks

**Project Overview:**
This GitHub repository houses the code and resources for an intelligent scheduling strategy developed to optimize sensor energy consumption and enhance system state estimation within a Wireless Sensor Network (WSN). The project explores the application of Reinforcement Learning, particularly the Deep Q-Networks (DQN) algorithm, to tackle the challenges of scheduling in WSNs.

**Key Concepts:**
- **Reinforcement Learning:** This project leverages Reinforcement Learning, a machine learning paradigm, to enable the sensor network to learn and adapt its scheduling strategy over time.
- **Deep Q-Networks (DQN):** DQN is a specialized algorithm within Reinforcement Learning used to approximate the optimal action-value function for decision-making.
- **Q-Learning:** Q-Learning is a fundamental concept in Reinforcement Learning and serves as a basis for understanding DQN.
- **Machine Learning:** The project incorporates machine learning principles to enhance scheduling decisions.
- **Gymnasium and Stable Baselines3:** These technologies are employed to create a customized environment for simulating and training the intelligent scheduling strategy.

# Environment Description

**WSNEnvironment: A Customized Gym Environment**

The core of this project is a customized gym environment, 'WSNEnvironment,' meticulously crafted to emulate real-world scenarios within a WSN. This environment is tailored to represent the intricacies of sensor deployment, coverage and energy optimization, and event handling, all central to achieving the project's objectives. Here's an in-depth look at the key components and functionality:

## Observation and Action Spaces
In Reinforcement Learning, defining the observation and action spaces is crucial. These spaces determine what the agent perceives and what actions it can take. In 'WSNEnvironment':
- **Observation Space:** The observation space is a matrix representing the 2D positions of sensors in the network. However, a novel enhancement has been added: a third column tracks the number of selections each sensor receives during an episode. This addition enables the agent to evolve from random behavior to strategic decision-making as it learns from the DQN model.
- **Action Space:** The action space corresponds to the number of sensors in the network. Each action taken by the agent corresponds to selecting a sensor to retrieve data from its buffer.

## Environment Dynamics
The heart of 'WSNEnvironment' lies in how it simulates a dynamic sensor network over time:
- **Sensor Deployment:** The environment allows for the creation of a customizable sensor network. The number of sensors (`num_sensors`) and their spatial distribution are determined using a Poisson point distribution, ensuring a random and diverse sensor deployment.
- **Coverage and Energy Optimization:** 'WSNEnvironment' simulates the optimization of sensor energy usage while maintaining efficient coverage of the monitored area. Sensors operate within circular coverage areas, representing regions where they can detect and capture events.
- **Event Handling:** Events, representing data to be captured, are generated with a certain probability if it exceeds the threshold probability(`threshold_prob`). If an event is generated, its location is determined randomly within the monitored region. Sensors within the event's coverage area detect and record the event, mimicking real-world event detection and they add it to their buffers.

## Agent Interaction
- **Step and Reset Functions:** The 'step' function models the agent's interaction with the environment, simulating the process of selecting sensors and capturing events over multiple time steps. The 'reset' function initializes the environment at the start of each episode.
- **Reward Function:** The reward mechanism has been significantly enhanced from the initial version. Instead of a simple reward structure, 'WSNEnvironment' now calculates rewards based on the Age of Information (AoI). Minimizing AoI is the key to optimizing the system's state estimation. The agent's reward is proportional to how well it minimizes AoI, ensuring more strategic sensor selections.

The 'WSNEnvironment' in this project offers a comprehensive and flexible platform for experimenting with intelligent scheduling strategies, allowing you to explore and develop state-of-the-art reinforcement learning algorithms for sensor network optimization.

## How to Use
- Clone this repository to your local machine.
- Explore the 'WSNEnvironment' class and its methods to understand the simulation environment.
- Stay tuned for further instructions on utilizing this environment and conducting experiments, as we continue to refine and enhance this project.


![WSNEnvironment](https://github.com/fareskhlifi/Intelligent-Scheduling-using-Reinforcement-learning-and-Deep-Q-Networks/blob/main/WSN.png?raw=true)
