---
layout: page_no_title
permalink: /master_thesis/
---
# Master Thesis: Autonomous Navigation of Multi-Robot Systems in Dynamic Warehousing and Rescue Environments

**Author:** Sameer Anees Jaliawala  
**Institution:** TU Dortmund  
**Program:** MSc Automation and Robotics  
**Supervisors:** Prof. Dr. Dr. h. c. Michael ten Hompel, Julia Freytag, M.Sc.  
**Completion Date:** October 2024

---
## Source Code
 - [ISAAC SIM](https://github.com/sameeranees/RL_Multi_Robot)
 - [Gazebo](https://github.com/sameeranees/DRL_robot_navigation_ros2)

---

## Abstract

The integration of autonomous mobile robots in intralogistics and disaster management scenarios is crucial for ensuring safety and productivity in complex environments. This thesis explores the development of an autonomous navigation system that enables single or multi-robots to navigate dynamic environments, avoid obstacles, and reach targets efficiently.

The research implements and compares various reinforcement learning algorithms (DQN, DDPG, TD3) across two simulation platforms: ISAAC Sim and Gazebo. The experimental results demonstrate that DQN performs efficiently in ISAAC Sim, while DDPG excels in Gazebo. For multi-robot systems, TD3 outperforms DQN in ISAAC Sim, though both DDPG and TD3 face challenges in Gazebo environments.

---

## Research Objectives

### Primary Objective
Evaluate and compare different machine learning algorithms for robot navigation in dynamic environments such as intralogistics and warehousing by testing their performance across multiple simulation platforms.

### Key Research Questions
1. Which reinforcement learning algorithms have been proposed for intralogistics and rescue scenarios?
2. What system architecture and environmental setup are necessary for robot navigation in simulated environments?
3. How do proposed reinforcement learning algorithms perform across various simulation platforms?
4. How do algorithm modifications affect benchmark performance?
5. How can single robot navigation algorithms be extended to multi-robot approaches?
6. What are the limitations of implemented algorithms and future research directions?

---

## Methodology

### Simulation Environments

#### ISAAC Sim Configuration
- **Environment:** Section of Chair of Materials Handling and Warehousing (FLW) hall at TU Dortmund
- **Features:** Six 'obstacle-walls' positioned in upper and lower halves
- **Robot Configuration:** Differential drive with Velodyne LiDAR scanner
- **Advantages:** Real-world physics simulation, exceptional sim-to-real transferability

![ISAAC Sim Single Robot Environment](assets/images/single_objects_01.png)
*ISAAC Sim Environment for Single Robot Navigation*

![ISAAC Sim Multi Robot Environment](assets/images/multi_objects_01.png)
*ISAAC Sim Environment for Multi Robot Navigation*

#### Gazebo Configuration
- **Environment:** Similar layout to ISAAC Sim but smaller scale
- **Purpose:** Direct comparison with ISAAC Sim for algorithm evaluation
- **Robot Configuration:** Identical sensor setup for fair comparison

![Gazebo Single Robot Environment](assets/images/single_gazebo_head.png)

*Gazebo Environment for Single Robot Navigation*

![Gazebo Multi Robot Environment](assets/images/multi_gazebo_head.png)
*Gazebo Environment for Multi Robot Navigation*

### Implemented Algorithms

#### 1. Deep Q-Network (DQN)
- **Input:** Heading to Goal (HTG), Distance to Goal (DTG), 52 laser scan distances
- **Output:** 3 discrete actions (forward, turn left, turn right)
- **Architecture:** [54, 300, 300, 3] neural network
- **Features:** Large replay buffer, epsilon-greedy exploration

![DQN Architecture](assets/images/methodologie_deep_q.png)
*Deep Q-Network Architecture*

#### 2. Deep Deterministic Policy Gradient (DDPG)
- **Input:** 10-dimensional sparse laser findings, robot's past actions, relative target position
- **Output:** Continuous angular and linear velocities (normalized 0-1)
- **Architecture:** Actor-Critic network with 3×512 dense layers
- **Features:** Target network updates, experience replay

![DDPG Architecture](assets/images/methodologie_ddpg.png)
*Deep Deterministic Policy Gradient Architecture*

#### 3. Twin Delayed DDPG (TD3)
- **Input:** 20-dimensional Points of Interest (POIs), robot actions, relative DTG and HTG
- **Output:** Continuous angular and linear velocities
- **Architecture:** Actor network (800×600) + 2 critic networks (800→600→600)
- **Features:** Delayed policy updates, target policy smoothing

![TD3 Architecture](assets/images/methodologie_td3_network.png)
*Twin Delayed DDPG Architecture*

### System Architecture

#### Robot Sensor Configuration
- **LiDAR:** Velodyne rotating scanner providing 360° range data
- **Odometry:** Position and orientation tracking
- **Point Cloud:** 3D environment mapping capabilities

#### Action Graph Components
- ROS2 Twist Subscriber for velocity commands
- Differential Controller for wheel velocity calculation
- Articulation Controller for motor control

![Robot Action Graph](assets/images/single_action_graph_1.png)
*Robot Action Graph Architecture*

#### Sensor Graph Components
- Isaac Create Render Product for LiDAR rendering
- Isaac Read Lidar Beam Node for sensor data processing
- ROS2 Publish Laser Scan for communication
- Isaac Compute Odometry Node for position tracking

![Robot Sensor Graph](assets/images/single_sensor_graph_1.png)
*Robot Sensor Graph Architecture*

---

## Experimental Results

### Single-Robot Navigation Performance

#### ISAAC Sim Results
| Algorithm | Original | 1st Param | 2nd Param | 3rd Param |
|-----------|----------|-----------|-----------|-----------|
| **DQN**   | 1.6%     | 1.3%      | 3.9%      | 3.2%      |
| **DDPG**  | 0%       | 0.2%      | 0%        | 0%        |
| **TD3**   | 0.4%     | 0%        | 0%        | 0%        |

*Success rates across different parameterizations*

![Single Robot Loss - Original Implementation](assets/images/single_robot_loss_original.png)
*Training Loss Comparison - Original Implementation*

![Single Robot Successes - Original Implementation](assets/images/single_robot_successes_original.png)
*Success Rate Comparison - Original Implementation*

#### Gazebo Results
| Algorithm | Randomized Goals | Fixed Goals                    |
|-----------|------------------|--------------------------------|
| **DQN**   | 18%              | 1.2%                           |
| **DDPG**  | 19.5%            | 45.8% (78.4% after convergence) |
| **TD3**   | 4.6%             | 2.72%                          |

![Gazebo Loss Comparison](assets/images/gazebo_loss.png)
*Training Loss Comparison in Gazebo Environment*

![Gazebo Successes Comparison](assets/images/gazebo_successes.png)
*Success Rate Comparison in Gazebo Environment*

### Multi-Robot Navigation Performance

#### ISAAC Sim Multi-Robot Results
| Algorithm    | Success Rate |
|--------------|--------------|
| **Multi TD3** | 0.14%        |
| **Multi DQN** | 0%           |

#### Gazebo Multi-Robot Results
| Algorithm     | Success Rate |
|---------------|--------------|
| **Multi TD3** | 0%           |
| **Multi DDPG** | 0%           |

![Multi Robot Loss - ISAAC Sim](assets/images/multi_robot_loss.png)
*Multi-Robot Training Loss in ISAAC Sim*

![Multi Robot Successes - ISAAC Sim](assets/images/multi_robot_successes.png)
*Multi-Robot Success Rate in ISAAC Sim*

![Multi Robot Loss - Gazebo](assets/images/multi_robot_gazebo_loss.png)
*Multi-Robot Training Loss in Gazebo*

![Multi Robot Successes - Gazebo](assets/images/multi_robot_gazebo_successes.png)
*Multi-Robot Success Rate in Gazebo*

### Key Performance Insights

#### Algorithm-Specific Findings
- **DQN:** Most consistent performance in ISAAC Sim, highest success rates across parameterizations
- **DDPG:** Excellent performance in Gazebo with fixed goals (78.4% success rate after convergence)
- **TD3:** Best performance in multi-robot scenarios within ISAAC Sim

#### Environment-Specific Observations
- **ISAAC Sim:** More challenging environment, lower overall success rates
- **Gazebo:** Better algorithm performance, particularly for DDPG with fixed goals
- **Multi-Robot:** Significant performance degradation compared to single-robot scenarios

### Advanced Parameterization Results

#### Gradient Clipping Implementation
![Single Robot Loss - Gradient Clipping](assets/images/single_robot_loss_gradient.png)
*Training Loss with Gradient Clipping Implementation*

![Single Robot Successes - Gradient Clipping](assets/images/single_robot_successes_gradient.png)
*Success Rate with Gradient Clipping Implementation*

#### Delayed Training, Prioritized Memory, and Randomized Robots
![Single Robot Loss - DT_PM_RR](assets/images/single_robot_loss_dt_pm_rr.png)
*Training Loss with Delayed Training, Prioritized Memory, and Randomized Robots*

![Single Robot Successes - DT_PM_RR](assets/images/single_robot_successes_dt_pm_rr.png)
*Success Rate with Delayed Training, Prioritized Memory, and Randomized Robots*

---

## Technical Implementation Details

### Reward Structures

#### Single-Robot Rewards
| Case            | DQN       | DDPG     | TD3  |
|-----------------|-----------|----------|------|
| Target Reached  | +200-500  | +120     | +100 |
| Collision       | -200      | -100     | -100 |
| Linear Step     | +5/-5     | -5       | -5   |
| Angular Step    | +1/-1     | -1       | -1   |
| DTG Improvement | +5        | Variable | -    |
| HTG Improvement | +1        | -        | -    |

#### Multi-Robot Rewards
| Case            | Multi TD3 | Multi DQN |
|-----------------|-----------|-----------|
| Target Reached  | +200      | +500      |
| Collision       | -200      | -100      |
| Linear Step     | -2        | -5        |
| Angular Step    | -2        | -1        |
| DTG Improvement | +1        | +5        |
| HTG Improvement | +1        | +1        |

### Key Parameters
- **Learning Rate:** 0.0001-0.001
- **Discount Factor:** 0.95-0.99999
- **Memory Size:** 100,000-1,000,000
- **Batch Size:** 40-128
- **Exploration Rate:** 0.01-1.0

---

## Navigation Stack Integration

### System Architecture
The research successfully integrated the DRL local planner with a global planner to form a complete navigation stack:

1. **Global Planner:** Utilizes global costmap from map server
2. **Local Planner:** DRL-based obstacle avoidance and path following
3. **Controller:** Converts paths to velocity commands
4. **Simulation Environment:** Provides sensor data and executes commands

![Navigation Stack Concept](assets/images/Nav_stack_concept.png)
*Navigation Stack Architecture*

### Integration Results
- Successful overlap between laser scan data and predefined maps
- Real-time navigation capability within mapped environments
- Effective coordination between global and local planning modules

![Navigation Stack in RViz](assets/images/nav_stack_rviz.png)
*Navigation Stack Integration in RViz*

---

## Key Findings and Contributions

### Major Achievements
1. **Algorithm Comparison:** Comprehensive evaluation of DQN, DDPG, and TD3 across multiple environments
2. **Environment Analysis:** Detailed comparison between ISAAC Sim and Gazebo simulation platforms
3. **Multi-Robot Extension:** Successful extension of single-robot algorithms to multi-robot scenarios
4. **Navigation Stack:** Complete integration of DRL local planner with traditional navigation stack

### Performance Insights
- **DQN** demonstrates superior performance in ISAAC Sim environments
- **DDPG** achieves excellent results in Gazebo with fixed goals (78.4% success rate)
- **TD3** shows promise for multi-robot coordination in ISAAC Sim
- Environment-specific optimization is crucial for algorithm performance

### Technical Contributions
- Implementation of multiple parameterization strategies
- Integration of gradient clipping and prioritized memory
- Development of delayed training mechanisms
- Creation of comprehensive reward structures

---

## Limitations and Challenges

### Algorithm Limitations
- **Overfitting:** Algorithms showed signs of overfitting in certain environments
- **Environment Dependency:** Performance varied significantly between simulation platforms
- **Multi-Robot Challenges:** Significant performance degradation in multi-robot scenarios
- **Training Instability:** Algorithms crashed after extended training periods

### Technical Challenges
- **Physics Engine Differences:** Variations between ISAAC Sim and Gazebo physics
- **Sensor Configuration:** LiDAR sensor limitations affecting input quality
- **Computational Resources:** High computational requirements for multi-robot training
- **Sim-to-Real Transfer:** Challenges in transferring simulation results to real-world applications

---

## Future Directions

### Recommended Approaches
1. **PPO Algorithm:** Potential for better performance with parallelized simulation environments
2. **ISAAC Gym:** Leverage GPU acceleration for faster training and improved results
3. **Hybrid Methods:** Combine classical and machine learning approaches for robust navigation
4. **Extended Training:** Longer training periods with improved stability mechanisms

### Research Opportunities
- **Real-World Deployment:** Testing algorithms on physical robots
- **Advanced Multi-Robot Coordination:** Improved communication and coordination strategies
- **Dynamic Environment Adaptation:** Algorithms that adapt to changing environments
- **Semantic Navigation:** Integration of semantic understanding for complex scenarios

---

## Conclusion

This research successfully demonstrates the implementation and comparison of reinforcement learning algorithms for autonomous robot navigation in dynamic environments. The findings provide valuable insights into algorithm performance across different simulation platforms and highlight the challenges and opportunities in multi-robot navigation systems.

The work contributes to the growing field of autonomous robotics by providing a comprehensive framework for evaluating navigation algorithms and establishing a foundation for future research in intralogistics and disaster management applications.

### Key Takeaways
- **Environment-Specific Optimization:** Different algorithms excel in different simulation environments
- **Multi-Robot Complexity:** Significant challenges remain in scaling single-robot solutions to multi-robot systems
- **Integration Success:** DRL algorithms can be successfully integrated with traditional navigation stacks
- **Future Potential:** Continued research in PPO and parallelized training shows promise for improved performance

---

## Technical Specifications

### Hardware Requirements
- **Simulation Platforms:** ISAAC Sim, Gazebo
- **Robot Type:** Differential drive mobile robots
- **Sensors:** Velodyne LiDAR scanner, odometry sensors
- **Computing:** GPU acceleration recommended for training

### Software Stack
- **Framework:** ROS 2, PyTorch
- **Languages:** Python, C++
- **Simulation:** ISAAC Sim, Gazebo
- **Visualization:** RViz, Matplotlib

### Performance Metrics
- **Success Rate:** Percentage of successful navigation episodes
- **Training Loss:** Algorithm convergence during training
- **Distance to Goal:** Path efficiency measurement
- **Heading to Goal:** Navigation accuracy assessment

---

*This thesis represents a comprehensive study in autonomous robot navigation, contributing valuable insights to the fields of robotics, machine learning, and logistics automation.*
