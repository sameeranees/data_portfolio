---
layout: page_no_title
---

# Race Against the Machine – 5G Enabled Tele-Operated vs Automated Driving

**Duration:** 2021 - 2022  
**Technologies:** ROS, Python, C++, 5G Networks, SLAM, Web Technologies  
**Institution:** TU Dortmund University - Chair of Communication Networks (CNI)  

---
## Source Code

Unfortunately, the code is proprietary and cannot be shared. However for more information about the project, visit the official TU Dortmund University page:
[Race Against the Machine - TU Dortmund CNI](https://cni.etit.tu-dortmund.de/newsdetail/race-against-the-machine-22130/)

---
## Project Overview

The "Race Against the Machine" project was conducted during the winter semester of 2021/2022 at TU Dortmund University as part of the Chair of Communication Networks (CNI) research program. This project explored the intersection of 5G communication technology and autonomous vehicle systems through a competitive framework that pitted human teleoperators against autonomous driving algorithms using F1/10 scale vehicles.

The primary objective was to evaluate the robustness of private 5G networks in teleoperated driving scenarios while simultaneously developing and testing various autonomous driving approaches. The F1/10 platform provided an ideal testing environment, offering realistic vehicle dynamics and sensor configurations while maintaining safety and controllability for experimental purposes.

![Race Against the Machine Team](assets/images/race_against_machine_team.webp)
*Project team working on the F1/10 platform and teleoperation system*

## Technical Approach

### 5G Network Integration
The project's foundation relied on establishing a robust 5G communication infrastructure capable of supporting real-time teleoperation requirements. The network performance was systematically evaluated across multiple metrics including latency, packet loss, bandwidth utilization, and signal quality. This comprehensive analysis was essential for understanding how network characteristics directly impact the Quality of Experience (QoE) in teleoperated driving scenarios.

The 5G network's ability to maintain low-latency communication proved critical for safe and effective remote vehicle control, where response times directly correlate with operational safety and performance.

### Multi-Modal Control Systems
The project implemented three distinct control paradigms to enable comprehensive evaluation of different driving approaches:

- **Direct Teleoperation:** Human operators control vehicles remotely through the 5G network infrastructure
- **Indirect Teleoperation:** Semi-autonomous systems with human oversight and intervention capabilities
- **Fully Autonomous:** Complete autonomous navigation using computer vision and sensor fusion

### Digital Twin Implementation
A sophisticated web-based digital twin was developed to provide real-time visualization and monitoring capabilities. This system integrated ROS-based communication protocols to deliver comprehensive environmental awareness, including vehicle positions, network performance metrics, and system status information. The digital twin served as both a monitoring tool and an interface for system control and analysis.

![Digital Twin Interface](assets/images/race_against_machine_digital_twin.webp)
*Web-based digital twin interface showing real-time vehicle tracking and environment visualization*

## Key Technical Components

### SLAM Implementation
The Simultaneous Localization and Mapping (SLAM) system formed a critical component of the project, utilizing Google's Cartographer algorithm to provide accurate real-time positioning and environmental mapping capabilities. This implementation was essential for both autonomous navigation functionality and the digital twin visualization system.

A particularly innovative aspect involved the integration of OpenStreetMap data to automatically generate scaled-down racetrack environments for laboratory testing. This approach enabled the creation of realistic racing scenarios based on actual Formula 1 track layouts, providing authentic testing conditions while maintaining laboratory safety standards.

### Web-Based Digital Twin Development
The digital twin interface was developed using modern web technologies and RESTful API architecture to enable real-time data streaming from vehicle systems. The system captured and visualized comprehensive telemetry data including vehicle positions, velocities, network performance metrics, and system status information.

The 3D visualization component provided an intuitive interface for monitoring race progress, analyzing network performance, and enabling remote system control when necessary. This implementation demonstrated the practical value of digital twin technology in autonomous vehicle testing and development.

### F1/10 Platform Integration
The F1/10 platform integration required careful consideration of real-time processing requirements and system reliability. The vehicles were equipped with comprehensive sensor suites including cameras, LiDAR, and IMU systems, mirroring the sensor configurations found in full-scale autonomous vehicles.

The primary technical challenge involved ensuring that all software components could meet the demanding real-time requirements of racing scenarios while maintaining system robustness and reliability under various operating conditions.

## Research Significance

### Industry Applications
The research conducted in this project has direct relevance to current and future autonomous vehicle development, particularly in the context of SAE Level 4 autonomous systems where human operator intervention may be required for unexpected scenarios. The teleoperation capabilities demonstrated are also applicable to rescue robotics and industrial automation applications where reliable remote control is essential.

### Key Research Contributions
The project successfully demonstrated several critical capabilities:

- **5G Network Reliability:** Established that 5G networks can effectively support real-time vehicle teleoperation requirements
- **Autonomous System Performance:** Demonstrated that autonomous systems can achieve competitive performance against human operators in controlled environments
- **Digital Twin Technology:** Validated the practical value of real-time monitoring and control systems for autonomous vehicle applications
- **Multi-Modal Integration:** Proved the feasibility of seamless transitions between autonomous and human-controlled operation modes

The network performance benchmarks and reliability metrics established through this research have been adopted by other research teams working on similar teleoperation and autonomous vehicle challenges.

## System Architecture

The system architecture integrated multiple components to create a comprehensive teleoperation and autonomous driving platform:

![System Architecture](assets/images/race_against_machine_system.webp)
*System architecture diagram showing the integration of 5G networks, ROS communication, and web-based monitoring*

![Process Flow](assets/images/race_against_machine_flow.png)
*Process flow diagram illustrating the teleoperation and autonomous driving workflow*

The overall system was built on a ROS-based communication framework, with 5G network infrastructure handling real-time teleoperation data transmission. The web-based interface provided centralized monitoring and control capabilities, enabling comprehensive oversight of the entire system operation.

## Project Outcomes and Impact

This project provided valuable insights into the practical implementation of 5G-enabled teleoperation systems and their integration with autonomous vehicle technologies. The research demonstrated the feasibility of combining multiple control paradigms within a single platform while maintaining system reliability and performance.

The development of the digital twin technology proved particularly valuable, providing real-time monitoring capabilities that are essential for safe operation of autonomous systems. The ability to seamlessly transition between autonomous and teleoperated modes represents a significant advancement in human-robot interaction for vehicle control applications.

The research findings and technical implementations developed through this project continue to be referenced by other research teams working on similar teleoperation and autonomous vehicle challenges, contributing to the broader advancement of the field.
