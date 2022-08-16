# Importance of RE 

Requirements Engineering (RE) is an iterative, systematic approach, designed for efficiency and effectiveness, with the goal of creating explicit **requirements and system specifications** that are agreed upon with all stakeholders. 


## Functional Requirements
- Requirements that describe the **behavior** of the system, especially with regard to its use (including time behavior when relevant for functionality: mp4 player)

## Quality Requirements 
- Requirements on quality **properties** of the system (characteristic/quantitative properties with regard to behavior), general conditions

## Process Requirements 

- Development process requirements (project plan, milestones, budget, deadlines, quality assurance, etc)
- Implementation specifications (boundary conditions, constraints): Components or technologies to be used 

Quality and process requirements are often vaguely called **non-functional requirements**



---
(?) Name five problems that can be solved in sofftware and system development through sound requirements engineering. 
Additionally, What does "sound" requirements engineering mean anyway ? 

- Imcomplete requirements 
- Uncover hidden requirements 
- Identifying incomplete and/or hidden requirements 
- Separating requirements from known solutions 
- Defining Time-boxing metrics per activity 
- Clarifying moving targets of a project 
- Redefining underspecified requirements 

- Underspecified requirements 
- Software not fulfulling customer wishes due to misunderstood requirements 
- Wasted resources due to more being developed then customer needs ("Gold plating")
- Stakeholders being ignored making the finished product not usable 
- Software not being able to built due to contradicting requirements or sections in the contract
- Frequent change requests due to changing requirements

- **Sound RE**
    - Aims at an efficient and effective administration and use of requirements throughout the entire system life cycle

---

Solve the following subtasks:
- a) Classify the following text examples into: **Functional Requirements, Quality Requirements, and Process Re- quirements**.
- b) For each example, mark a possible requirement source, a possible author, the stakeholders involved, the require- ment rationale, and the actual requirement.
Text examples:
1. The system can be controlled easily and intuitively with the aid of two control elements. A button is used to discard hints. A switch is used to turn the system on or off.
2. The vehicle’s radio frequency warning (RFW) system can then compare the intended direction of travel with the observed direction of travel. If the intended direction of travel and the vehicle’s direction of travel match, the information is processed further; otherwise, the information is filtered out. The vision of the Radio Frequency Warning (RFW) system is to help drivers cope with the flood of information on the road with the help of radio frequency signals (hereafter RaSi).
3. The RFW system is intended to provide the user with an alternative to traffic signs that are visually difficult to see.
4. For the development of the RFW system the V-model XT shall be used to simplify quality assurance.
5. The supplier shall comply with the applicable standards and laws, even if they are not explicitly mentioned in the agreements. It should be noted that not only the laws applicable in Germany must be complied with, but also those of other EU countries.

**Answer**

1. **Functional Requirement**
    - **Requirement source:** requirements document (maybe stakeholder ?)
    - **Possible author:** requirements engineer 
    - **Stakeholders:** user, UI/UX Designer 
    - **Requirement rationale**: intuitive and easy UX/UI
    - **Actual requirement:** The user must be able to switch the system on and off 

2. **Quality Requirement**
    - Requirement source: systems-vision, goals, glossary 
    - Possible auther: requirements engineer
    - Stakeholders: driver
    - Requirements rationale: In today's automobiles, the driver is offered a great deal of information. As the driver is in traffic, it is essential to support him in coping with this information.
    - Actual requirement: If the direction of travel and the vehicle's direction of travel do not match, the system must filter out the information, otherwise the information is processed further. 


3. **Functional Requirement**
    - **Requirement source:** requirements document/stakeholder
    - **Possible author:** UI/UX
    - **Stakeholders:** user, user experience designer
    - **Requirements rationale:** the user has problems identifying traffic signs
    - **Actual requirement:** the system must show (current active) traffic signs 


4. **Process Requirement**
    - **Requirement source:** Commissioning, tendering
    - **Possible author:** Requirements Engineer
    - **Stakeholders:** QS Representative, Develope, Project Manager
    - **Requirements rationale:** QA should be easy
    - **Actual requirement:** during development, applicable standards must be observed. 
5. **Quality Requirements**
    - **Requirement Source:** contract
    - **Possible author:**law department
    - **Stakeholders:** legislator, contractor, client
    - **Requirements rationale:** avoidance of penalties
    - **Actual requirement:** during development, applicable standards must be observed

--- 

## Analysis of Requirements for separation of problem and solution (Analyis)

When stakeholders describe requirements, they often put forward concrete solution proposals. Those can distract from the actual problem and unnecessarily restrict the solution space. As a requirements engineer, it is your task to question such proposed solutions in order to approximate an adequate problem description.

*Consider the e-scooter: One stakeholder poses the specific request ”The handle should be made of stainless steel”. You as a requirements engineer question this specific request: ”Why stainless steel?” and receive the answer: ”Because it is easier to clean”. From this, you deduce the requirement: ”The handle should be easy to clean”. During system design, the decision is made to use carbon because it is even easier to clean than stainless steel and is also cheaper.*

Extract a possibly problematic solution constraint from the following statements. Reformulate these statements so that their solution space is not unnecessarily restricted:
- ”The microwave oven should be equipped with a video camera that analyzes the food in the microwave and automatically adjusts the power intensity and duration from it.”
- “The user should be able to choose the appropriate category from the drop-down menu via GUI.”
- “A typical third party ‘load balancer’ shall distribute user requests to the different servers to ensure a response time below 2 seconds.”
- “To avoid distracting the driver, the desired speed shall be adjustable via two buttons, + and −, on the steering wheel.” ”
- “The vehicle shall not accelerate at more than 2m/s2.”
- “All new data fed into the system must be backed up once per hour.” .
- “Before creating a new text entry, the character set to be used should always be queried.”

**Create 2 more examples that may include a solution constraint. Have your partner analyse them (or re-use your results of Exercise 2)**



## Answer: Analysis of Requirements for separation ...
> First statement

- **Problematic solution constraint:** why does it need to be a camera ?
- **Reformulation:** The microwave oven should be equipped with a sensor that analyzes the food in the microwave and automatically adjusts the power intensity and duration from it 

> Second statement 
- **Problematic solution constraint:**  Why drop-down menu ? 
- **Reformulation:** The user can choose the appropiate category over GUI.

> Third statement 
- **Problematic solution constraint:** why 2 seconds upper bound ? 
- **Reformulation:** A typical third part "load balancer" shall distribute user requests to the different servers to ensure a reasonable response time. 

> Fourth statement

- **Problematic solution constraint:** why buttons on steering wheel ? 
- **Reformulation:** To avoid distracting the driver, the desired speed shall be adjustable via an easily reachable (button) system

> Fifth statement 

- **Problematic solution constraint:** why not more than 2m/sˆ2 ?
- **Reformulation:** The vehicle should not accelerate at more than certain threshold. 

> Sixth statement 

- **Problematic solution constraint:** Why per hour ? 
- **Reformulation:** All new data fed into the system must be backed up at appropative time periods.

> Seventh statement 

- **Problematic solution constraint:** why always query ? (it can create overheads )
- **Reformulation:** The text entries use the correct character set



