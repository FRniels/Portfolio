# BOMB-Case Game

---

![BOMB-Case Game](../Images/BOM_Case_Casecore_Games.png)

---

## Korthagen Reflection Model

### Action

During the second year of the Electronics-ICT bachelor, our class worked on the development of a BOMB-Case game. The project consisted of multiple teams, each responsible for designing and implementing an electronics puzzle module. The final game would contain up to nine modules, which players needed to solve before time ran out or before making too many mistakes.

At the start of the project, no team was assigned the responsibility of creating the central game controller. I decided to take ownership of this task and developed a master module for the BOMB-Case. This module implemented the overall game state machine, including system boot-up, I2C communication with all puzzle modules, module detection, score tracking, error counting, game progression, and game completion logic.

To simplify integration, I also developed a template state machine that other teams could use as a foundation for their own puzzle modules. In the end, only two teams integrated this state machine into their modules, allowing the complete system to be tested with two active puzzle modules.

### Looking Back

I enjoyed working on this project because it allowed me to take responsibility for an important part of the system architecture. Developing the master controller required me to think beyond a single module and consider how all subsystems would interact. It was rewarding to see the game operate as a complete system rather than as separate electronics projects.

At the same time, I noticed that collaboration between teams was challenging. Not all teams implemented the provided framework, which limited the amount of integration testing that could be performed. This reduced the opportunity to fully validate the scalability of the master controller with all intended modules.

### Awareness of Essential Aspects

This project taught me the importance of system integration and clear interfaces in larger engineering projects. A well-defined communication protocol and common software structure are essential when multiple teams contribute to a single product.

I also learned valuable lessons regarding hardware communication reliability. During testing, communication between modules occasionally became unstable. Based on the observed behavior, the most likely cause was the I2C bus configuration, as the system used relatively long cables and relied primarily on the internal pull-up resistors of the RP2040 microcontrollers. This demonstrated how hardware design decisions can directly influence software reliability.

### Creating Alternatives

If I were to repeat this project, I would define stricter integration requirements and testing milestones from the beginning. This would encourage all teams to implement the common framework earlier and allow problems to be detected sooner.

From a technical perspective, I would also investigate the communication bus more thoroughly by optimizing cable lengths, adding external pull-up resistors, and validating signal integrity before integrating all modules into the system.

### Trial

In future projects, I will continue to take initiative when important responsibilities are not clearly assigned. However, I will also place greater emphasis on defining integration standards and ensuring that all stakeholders actively contribute to the common goal. This experience strengthened my skills in embedded software development, system architecture, and technical problem solving.

## PXL X-Factor

* **(Em)passion:** I showed enthusiasm and commitment by taking responsibility for a crucial part of the project that was initially unassigned.
* **Entrepreneurial:** I identified a gap in the project organization and proactively developed a solution that enabled the different modules to function as one complete game.
* **Innovative:** I designed a central game controller and a reusable state machine framework to simplify module integration for other teams.
* **(Inter)nationality:** The project improved my communication and collaboration skills within a multidisciplinary team environment.
* **Multi-perspective:** I learned to consider both hardware and software aspects of a system and to account for the needs of multiple teams contributing to a shared project.

## Sustainable Development Goals (SDGs)

### SDG 4 – Quality Education

This project contributed to SDG 4 by promoting practical, hands-on learning in embedded systems, electronics, and software engineering. Through collaboration and knowledge sharing between teams, students gained experience with real-world engineering challenges such as system integration, communication protocols, and project coordination.

### SDG 9 – Industry, Innovation and Infrastructure

The project also aligns with SDG 9 because it involved the development of an innovative embedded system consisting of multiple interconnected modules. Designing reliable communication between devices and creating a scalable system architecture reflects challenges commonly encountered in modern industrial and technological environments.

