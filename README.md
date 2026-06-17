# Enabling Biomimetic Self-Regulation in Intrinsically Motivated Robots

## 🦎 Abstract

From weaving spiders to hibernating mammals and migratory birds, nature presents numerous examples of organisms exhibiting extraordinary autonomous behaviors that ensure their self-maintenance. However, physiological needs often interact and compete. This requires living organisms to handle them as a coordinated system of internal needs rather than as isolated subsystems. We present an artificial agent equipped with a neural mass model replicating fundamental self-regulatory behaviors observed in desert lizards. Our results demonstrate that this agent not only autonomously regulates its internal temperature by navigating to areas with optimal environmental conditions, but also harmonizes this process with other internal needs, such as energy, hydration, security, and mating. This biomimetic agent outperforms a control agent lacking interoceptive awareness in terms of efficiency, fairness, and stability. Additionally, to demonstrate the flexibility of our framework, we develop a ”cautious” agent that prioritizes security over other needs, achieving a Maslow-like hierarchical organization of internal needs. Together, our findings suggest that grounding robot behavior in biological principles of self-regulation provides a robust framework for designing multipurpose, intrinsically motivated agents capable of resolving trade-offs in dynamic environments.

<p align="center">
  <img src="img/VisualAbstract.png" alt="Visual Abstract" width="70%">
</p>

## 🧠 Project description

This repository includes the source code for the publication:

**Biomimetic self-regulation in intrinsically motivated robots**
Rosado, O. G., Amil, A. F., Freire, I. T., Vinck, M., & Verschure, P. F. — *Artificial Life Conference Proceedings 37*, MIT Press, 2025
[https://direct.mit.edu/isal/proceedings/isal2025/37/49/134044](https://direct.mit.edu/isal/proceedings/isal2025/37/49/134044)

An early version of this work was presented at IROS 2023 as part of the workshop [Learning Robot Super Autonomy](https://wp.nyu.edu/workshopiros2023superautonomy/).

### 🧩 Components

The repository includes several executable files:

- **Epuck Launch**   
  Launches the Webots simulation using hyperparameters defined in `config.ini`.

- **Gradients Node**  
  Generates gradients that indicate resources' locations and assist robot navigation.

- **Allostatic model Node**  
  Implements the Neural-mass multiattractor model of allostatic orchestration.

- **Robot navigation Node**   
  Integrates gradient's and allostatic model's information to guide robot's navigation.

- **Data Gathering Node**  
  Collects simulation metrics and stores them in a `.csv` file at the end of each experimental session.
  
- **Supervisor Node**  
  Manages simulation-level tasks such as resetting, plotting, and tracking spatial metrics. 

---

## ⚙️ Installation

> 🐧 This repository was developed on **WSL-Ubuntu 22.04** for Windows 11, but it also supports native Linux installations.

### ✅ Requirements

- Ubuntu 22.04 (or WSL-Ubuntu 22.04 on Windows)
- Python `3.10.12`

### 🐧 Linux 

1. Install [**Webots**](https://cyberbotics.com/).
2. Install [**ROS2 Iron Irwini**](https://docs.ros.org/en/iron/Installation.html).
3. Install [**webots_ros2**](https://docs.ros.org/en/iron/Tutorials/Advanced/Simulators/Webots/).

### 🪟 Windows 11 via WSL2

> 💡 We can provide a pre-configured WSL environment for convenience. To install manually:

1. Install [**Webots**](https://cyberbotics.com/) natively on Windows.
2. Create a WSL-Ubuntu 22.04 instance.
3. Follow Linux steps 2 and 3 inside WSL. 
4. Open **Windows Firewall with Advanced Security** and create an **inbound rule** for port `1234`.
5. Set your Windows IP as the `nameserver` in `/etc/resolv.conf`.

---

## 🚀 Running the Simulation

> 🧑‍💻 For Windows 11 users, use WSL-Ubuntu 22.04 terminals.

1. Create your ROS2 workspace:

```bash
    mkdir -p ~/ALIFE2025-Desert-Lizard/src
    cd ~/ALIFE2025-Desert-Lizard/src
    git clone https://github.com/oscarguerrerorosado/ALIFE2025-Desert-Lizard.git
```

2. Build the workspace:

```bash
    cd ~/ALIFE2025-Desert-Lizard
    colcon build
```

3. Source the environment by editing your bashrc file: 

```bash
    cd
    sudo nano ~/.bashrc 
```

    Add the following at the end (adjust your paths if needed): 

```bash
    source /opt/ros/iron/setup.bash
    source ~/ALIFE2025-Desert-Lizard/install/local_setup.bash
```

4. Save and close the file, then reload it:

```bash
    source ~/.bashrc
```

5. Open **six terminals** and run:

    - **Terminal 1**:
```bash
      ros2 launch webots_pkg mini_launch.py
```

    - **Terminal 2**:
```bash
      ros2 run webots_pkg gradients
```

    - **Terminal 3**:
```bash
      ros2 run webots_pkg allostatic_model
```

    - **Terminal 4**:
```bash
      ros2 run webots_pkg robot_navigation
```

    - **Terminal 5**:
```bash
      ros2 run webots_pkg data_gathering
```

    - **Terminal 6**:
```bash
      ros2 run webots_pkg supervisor
```

6. Alternatively to step 5, you can run a launch file including all the rest nodes. However, prints of each node will not be visible:

    - **Terminal 1**:
```bash
      ros2 launch webots_pkg full_launch.py
```

---

## 📬 Contact

For questions or issues, feel free to contact Oscar Guerrero Rosado at guerrerorosado.o@gmail.com. A pre-configured WSL image can also be provided for a faster setup.