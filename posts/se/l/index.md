# Software Engineering


***这篇文章展示了软件工程的学习记录***

<!--more-->
---
# Software Engineering

## 1 Introduction to Software Engineering

### 1.1 Software Attributes
**Acceptability**
- MUST be acceptable to the type of users for which it is designed
- Understandable, usable, and compatible with other systems

**Dependability**
- Include **reliability**, **security**, and **safety**
- Should **NOT** cause physical or economic **damage** in event of system **failure**
- MUST be secure

**Efficiency**
- Software should **NOT** make **wasteful use** of system resources such as memory and processor cycles
- include responsiveness, processing time, memory/resource utilization, etc.

**Maintainability**
- Software should be written in such a way so that it can evolve to **meet changing requirements**
- Critical attribute since software change is an inevitable requirement of a changing business environment

---
## 2 Software Process
A structured set of activities required to develop a software system. 

There are many different software processes, but they all involve:
- **Specification** – *defining* what the system should do; 
- **Development** – *producing* the software that meets the specification; 
- **Validation** – *checking* that it does what it should do; 
- **Evolution** – *changing* the system in response to changing needs.

**Description**
Process descriptions may also include:
- Products, or deliverables, which are the outcomes of a process activity; 
- Roles, which reflect the responsibilities of the people involved in the process; 
- **Pre- and post-conditions**, which are statements that are true before and after a process activity has been enacted or a product produced.

---
### 2.1 Plan-Driven and Agile Processes
- **Plan-driven processes** are processes where **all** of the process activities are **planned in advance** and progress is measured against this plan.

- In **agile processes**, planning is **incremental**, and changing the process to reflect changing customer requirements is easier. 
  - In practice, most practical processes include elements of both plan-driven and agile approaches. 
  - There are no right or wrong software processes.

---
### 2.2 Software Process Models

#### 2.2.1 Waterfall Model
There are separate identified phases in the waterfall model, and in principle, a phase must be completed before moving on to the next phase

- **Requirements analysis and definition**
- **System and software design**
- **Implementation and unit testing**
- **Integration and system testing**
- **Operation and maintenance**

---
#### 2.2.2 Waterfall Model Problems
- ***Inflexible*** partitioning of the project into distinct stages makes it difficult to **respond** to **changing customer requirements**.
  - Therefore, this model is only appropriate when the **requirements** are **well-understood** and **changes** will be fairly **limited** during the design process. 

- Types of systems for which the waterfall model is appropriate 
  - **Embedded systems** where the software has to interface with hardware systems 
  - **Critical systems** where there is a need for extensive safety and security analysis of the software specification and design 
  - **Large software systems** that are part of broader engineering systems developed by several partner companies

---
### 2.2.3 Incremental Development
- Incremental development is based on the idea of developing an **initial implementation**, getting **feedback** from users and others, and **evolving** the software through several **versions** until the **required** system has been developed
  - This approach can be either plan-driven, agile or, more usually, a mixture of these approaches.
  - You don’t have to deliver each increment to the system customer. 

![](./pic/2_1.png)

---
#### 2.2.4 Incremental Development Benefits and Problems 
Benefits
- It is easier to get customer feedback on the development work that has been done. 
- The cost of accommodating changing customer requirements is reduced. 
- More rapid delivery and deployment of useful software to the customer is possible.

Problems
- There may be a mismatch between the organizations’ bureaucratic procedures and a more informal iterative or agile process
- System structure tends to **degrade** as new increments are added.

---
#### 2.2.5 Integration and Configuration
Based on software reuse where systems are integrated from existing components or application systems, or COTS (Commercial-off-the-shelf) systems.
- Reused elements may be configured to adapt their behaviour and functionality to a user’s requirements 
- Reuse is now the standard approach for building many types of business systems
 
Types of reusable software
- Stand-alone application systems that are configured for use in a particular environment. 
- Collections of objects that are developed as a component or a package to be integrated with frameworks like .NET or J2EE. 
- Web services that are developed according to service standards and that are available for remote invocation.

---
#### 2.2.6 Reuse-oriented Software Engineering

![](./pic/2_2.png)

Advantages and disadvantages
- Reduced costs and risks as less software is developed from scratch 
- Faster delivery and deployment of systems 
- Requirements compromises are inevitable so the system may not meet the real needs of users 
- Loss of control over the system evolution

---
### 2.3 Process Activities
Real software processes are inter-leaved sequences of technical, collaborative and managerial activities with the overall goal of specifying, designing, implementing and testing a software system.

The four basic process activities of specification, development, validation and evolution are organized differently in different development processes. 

For example, in the waterfall model, they are organized in sequence, whereas in incremental development they are interleaved.

---
#### 2.3.1 Software Specification
The process of establishing what services are required and identifying the constraints on the system’s operation and development. 

Requirements engineering process
- Requirements elicitation and analysis
  - What do the system stakeholders require or expect from the system? 
- Requirements specification
  - Defining the requirements in detail
- Requirements validation
  - Checking the validity of the requirements

![](./pic/2_3.png)

---
#### 2.3.2 Software Development
The process of developing an executable system for delivery to the customer.
- Design and implementation are interleaved activities for most types of software systems.
  
- Software design
  - Design a software structure to realize the requirements
  - Architectural design, database design, interface design, component selection and design, ...

- Implementation
- Translate this structure into an executable program
- Programming is an individual activity with no standard process

---
#### 2.3.3 Software Validation - needs
> **Verification** and **validation** **(V & V)** is intended to show that a system conforms to its **specification** and meets the **requirements** of the system customer.

- **Verification** 
  - Check implementation again the perceived req.(user and system from developer point of view) as **internal checking of a developer group**;
- **Validation**
  - Check real user requirements.

> Validation: Are we building the **right** product?
> Verification: Are we building the product **right**?

- It involves checking processes (such as inspections and reviews) and system testing (static vs. dynamic)
- **Testing** is the most commonly used V & V activity.
  - **Component** testing (***Verification***): Testing of individual components;
  - **System** testing (***Verification***): Testing of the system as a whole;
  - **Customer** testing (***Validation***): Testing with customer data;

- Defect testing and debugging are different processes. Testing establishes the existence of defects. Debugging is concerned with locating and correcting these defects.

---
#### 2.3.4 Software Evolution
> Software is inherently flexible and can change.
- As requirements change, the software that supports the business must also evolve and change. 
- Although there has been a demarcation between development and evolution (maintenance), the distinction is increasingly irrelevant as fewer and fewer systems are completely new. 
- It is more realistic to think of software engineering as an evolutionary process where software is continually changed in response to changing requirements and customer needs.

![](./pic/2_4.png)

---
### 2.4 Coping with Change
Change is **inevitable** in all large software projects.
- A software product is a model of the real world, which is continually changing 
- Software professionals are human, and they make mistakes.
 
The moving target problem: The requirements change while the software product is being developed
- Any change made to a software product can potentially cause a regression fault 
- If there are too many changes, the entire product may have to be redesigned and reimplemented 
- There is no solution to the moving target problem

Change leads to rework so the costs of change include both rework (e.g., re-analyzing requirements) as well as the costs of implementing new functionality

---
#### 2.4.1 Reducing The Costs of Rework
**Two related approaches**
- Change anticipation, where the software process includes activities that can anticipate possible changes before significant rework is required.
  - For example, a prototype system may be developed to show customers some key features of the system.
- Change tolerance, where the process is designed so that changes can be accommodated at a relatively low cost.
  - This normally involves some form of incremental development. 
  - The longer a change is delayed, the more it costs to implement.

---
#### 2.4.2 Two Ways of Coping with Changing Requirements 
**System prototyping**
- A version or part of the system is developed quickly to check the customer’s requirements and the feasibility of design decisions. 
- This is a method of change anticipation as it allows users to experiment with the system before delivery and refine their requirements.

**Incremental delivery**
- System increments are delivered to the customer for comment and experimentation. 
- This supports both change anticipation and change tolerance.

---
#### 2.4.3 Software Prototyping
A prototype is an initial version of a system used to demonstrate concepts, try out design options, and find out more about the problem and its possible solutions. 
- A prototype can be used
  - in the requirements engineering process to help with requirements elicitation and validation; 
  - in the design process to explore options and develop a UI design;

**Benefits**
- Improved system usability.
- A closer match to users’ real needs.
- Improved design quality.
- Improved maintainability.
- Reduced development effort.

---
#### 2.4.4 Prototyping Development

![](./pic/2_5.png)
May be based on **rapid** prototyping languages or tools 

May involve leaving out functionality
- Prototype should focus on areas of the product that are not well- understood
- Error checking and recovery may not be included in the prototype
- Focus on functional rather than non-functional requirements such as reliability and security

---
#### 2.4.5 Incremental Delivery
The development and delivery is **broken down** into **increments** with each increment delivering part of the **required functionality**
- User requirements are **prioritized** and the **highest priority** requirements are included in **early increments**.
- Once the development of an increment is started, the requirements are frozen though requirements for later increments can continue to evolve.

![](./pic/2_6.png)

**Advantages**:
- elicit requirements for later increments. 
- Customer value can be delivered with each increment, so system functionality is available earlier
- relatively easy to incorporate changes into the system
- The highest priority system services tend to receive the most testing

**Problems**:
- difficult to implement for replacement systems as increments have less functionality than the system being replaced. 
- common facilities can be difficult to identify with incremental delivery but most systems require a set of basic facilities
- Its essence is that the spec is developed in conjunction with the software, which conflicts with the procurement model of many organizations

---
### 2.5 PROCESS IMPROVEMENT

#### 2.5.1 Software Process Performance and Capability
**Software Process Performance**
- Represents the **actual** results achieved by following a software process. 
- E.g., our actual defect rate is 2 defect/KLOC 
- Software process performance focuses on the **achieved results**

**Software Process Capability**
- Describes the **expected** results that can be achieved by following a software process. 
- E.g., the final defect rate will likely be 1.5 defect/KLOC 
- Software process capability focuses on the **expected results**

---
#### 2.5.2 Software Process Maturity
**Process Maturity**
- It is the extent to which an organization’s processes are explicitly, defined, managed, measured, controlled, and effective. 
- Maturity implies a potential for **growth in capability**

**Immature software organization**
- Processes being improvised by practitioners
- Managers being forced to solve immediate crises (fire fighting) 
- No objective basis for judging quality

**Mature software organization**
- Processes are documented, usable, and consistent with the way the work is actually done

![](./pic/2_7.png)

---
#### 2.5.3 Quality Assurance (QA)
- the identification, planning, adoption, and implementation of the disciplines and actions (the process) necessary to assure that the product satisfies its users.
- focus on improving the **process**

Use **error** and **trend analysis** to locate weaknesses in:
- Development process
- Test process 
- Maintenance process 
- Support process (Quality, Configuration management)

---
#### 2.5.4 Capability Maturity Model Integration (CMMI)
CMMI is a **framework** to **improve** **product quality and development efficiency** for systems (both hardware and software)

CMMI supports **2 representations**: **staged** and **continuous**. To initiate the process improvement, an organization must first select a representation.

##### 2.5.4.1 Staged Representation of CMMI 
Staged models provide a proven sequence of improvements, beginning with basic management practices and progressing through successive levels.

![](./pic/2_8.png)

##### 2.5.4.2 Continuous Representation of CMMI
Continuous representation designates capability levels: numbered 0 through 3: incomplete, performed, managed, and defined


---
## 3 Agile Software Development

### 3.1 Agile Methods (or Agile Development)
Dissatisfaction with the overheads involved in plan-driven software design methods
- The plan-driven approach was mainly used for developing **large**, **long-lived** software systems.

**Aim**:
- reduce overheads in the software process, such as limiting documentation;
- respond quickly to changing requirements without excessive rework.

All agile methods suggest that software should be developed and delivered **incrementally**.

---
#### 3.1.2 Plan-Driven and Agile Development
**Plan-driven development**
- Based around **separate** development stages with the outputs to be produced at each stage.
- **Iteration** occurs **within** activities.

![](./pic/3_1.png)

**Agile development**
- Specification, design, implementation, and testing are **inter-leaved** and the outputs from the development process are negotiated during the software development process.
- Iteration occurs **across** activities.

![](./pic/3_2.png)

---
#### 3.1.3 Agile Methods Applicability
Agile methods have been particularly successful for two kinds of system development.
- **Product development** where a software company is developing a small or medium-sized product for sale.
  - Most software products and apps are now developed using an agile approach

**Custom system development** within an organization, where there is a clear commitment from the customer to become **involved** in the development process and where there are few external rules and regulations that affect the software.


---
#### 3.1.4 Principles of Agile Manifesto
- **Customer involvement**
  - Customers should be closely involved throughout the development process
- **Incremental delivery**
  - The software is developed in increments with the customer specifying the requirements to be included in each increment. 
- **People not process**
  - The skills of the development team should be recognized and exploited. 
- **Embrace change**
  - Expect the system requirements to change and so design the system to accommodate these changes. 
- **Maintain simplicity**
  - Focus on simplicity in both the software being developed and in the development process. 
  - Wherever possible, actively work to eliminate complexity from the system.

---
### 3.2 AGILE DEVELOPMENT TECHNIQUES
> Agile methods are **incremental development** methods that focus on **rapid** software development, **frequent releases** of the software, reducing process overheads by **minimizing documentation** and producing **high-quality code**.


#### 3.2.1 Extreme Programming (XP)
- A very influential agile method

Pushing recognized good practice to “extreme” levels
- New versions may be built several times per day;
- Increments are delivered to customers every 2 weeks
- All tests must be run for every build and the build is only accepted if tests run successfully.
  
The extreme programming release cycle

![](./pic/3_3.png)

---
#### 3.2.2 XP Principles and Practices
![](./pic/3_4.png)
![](./pic/3_5.png)

---
#### 3.2.3 Support for Agile Principles in XP Practices
**Incremental delivery** is supported through **small releases**. 

**Customer involvement** is supported through **on-site customers**. 

**People, not process**, are supported through **pair programming**, collective ownership, and sustainable pace.

**Change is embraced** through **small releases, test-first development, refactoring, and continuous integration.** 

**Maintaining simplicity** is supported by **refactoring** and **simple design**.

---
#### 3.2.4 Influential XP Practices
Key practices
- **User stories for specification**
- **Refactoring**
- **Test-first development**
- **Pair programming**

##### 3.2.4.1 User Stories for Requirements
A user story is a description of a system requirement from a user perspective, is a scenario of use that a system user might experience 

- User making decisions on requirements. 
- written on cards, and the customer chooses the stories for inclusion in the next release based on their priorities and the schedule estimates. 
- development team breaks the selected user stories into implementation tasks.
- easier to relate to these stories than a conventional requirements document or use cases. 

Drawbacks
- difficult to judge if enough user stories have been developed to cover **all the essential requirements**
- if a single story gives a **true** picture of an activity.

**user stories $\to$ tasks**

---
##### 3.2.4.2 Refactoring
Look for **possible** software **improvements** and make them even when there is no immediate need.
- Local changes tend to degrade software structure and readability 
- This improves the understandability of the software and reduces the need for documentation. 
- Changes are easier to make because the code is well-structured and clear. 
- However, refactoring sometimes gets delayed, and some changes require expensive architecture refactoring.

---
##### 3.2.4.3 Test in XP/ Test-Driven Development
With XP, no system specification can be used by an external testing team to develop system tests
- User stories are user requirements but not system requirements as they often miss important information about the system

XP has developed an approach to test the program after every change. XP testing features:
- Incremental test development from scenarios. 
- Test-first development - Tests are written as programs **after** code
- User involvement in test development and validation. 
- Use of automated testing frameworks

**Test-Driven Development(TDD)**: Tests are written as programs **before** code, only need a rough idea of the functionality of the program
- Each test includes a check of whether its execution is correct. 

> write a falling test $\to$ make the test pass $\to$ refactor the code $\to$ next falling test $\to$ ...

**Customer involvement**: The customer helps develop acceptance tests for the stories to be implemented in the next release of the system.

**limitations**:
- People adopting the customer role have limited time and cannot work full-time with the development team. 
- They may feel that providing the requirements was enough of a contribution and may be reluctant to get involved in the testing process.

**Test Automation**: tests are written as executable components (before the task is implemented)
- These testing components should be stand-alone, simulate the submission of input to be tested, and check that the result meets the output specification. 
- An automated test framework (e.g., JUnit) is a system that makes it easy to write executable tests and submit a set of tests for execution.

As testing is automated, there is always a set of tests that can be quickly and easily executed

---
**Drawbacks of Test-first development**
- Programmers prefer programming to testing and sometimes they take short cuts when writing tests.
  - not all possible exceptions may occur

- Some tests can be very difficult to write incrementally.
  - 'display logic' and workflow between screens

- difficult to judge the completeness of a set of tests.
  - the test set may not provide complete coverage

---
##### 3.2.4.4 Pair Programming
Programmers sit **together** at the **same computer** to develop the software.
- Pairs are created dynamically so that all team members work with each other during the development process.

Benefits:
- supports the idea of collective ownership and responsibility for the system. 
- acts as an informal review process because at least two people look at each line of code 
- encourages refactoring to improve the software structure. 
- It is not necessarily inefficient.

---
### 3.3 Agile Project Management
Plan-driven software development
- requires a manager to have a stable view of everything that has to be developed and the development processes. 

Agile methods
- Self-organizing teams
- Little or no documentation
- Short-term development plans
- adapted to incremental development

---
#### 3.3.1 Scrum
> **Scrum** is an agile method that focuses on managing **iterative development** rather than specific agile practices.

**Three phases**:
- *Initial* phase is an outline planning phase
- A series of *sprint cycles*, where each cycle develops an increment of the system.
- The *project closure* phase wraps up the project, completes required documentation, and assesses the lessons learned.

![](./pic/3_6.png)
![](./pic/3_7.png)

**Benefits**
- The product is broken down into a set of manageable and  understandable chunks that stakeholders can relate to. 
  - Unstable requirements do not hold up progress. 
  - The whole team has visibility of everything, and consequently, team communication is improved. 
- Customers see on-time delivery of increments and gain feedback on how the product works. 
- Trust between customers and developers is established

---
## 4 Requirements Engineering

### 4.1 Requirements and Requirements Engineering
**requirements**
- **descriptions** of the *services* that a system should **provide** and 
- **constraints on its operation**.

**Requirements Engineering**
- The process of **finding out**, **analyzing**, **documenting**, and **checking** these services and constraints 

**Two types of requirements**
- **User** requirements: Statements in natural language plus diagrams
- **System** requirements: A detailed, structured document

![](./pic/4_1.png)

**Example**
![](./pic/4_2.png)

---
#### 4.1.1 Agile Methods and Requirements
Requirements in agile processes
- Use **incremental** requirements engineering and often express requirements as "**user stories**"
- may a waste of time
- Practical for business systems but problematic for many others

For a "traditional" view of requirements.
- For most large systems, there is a clearly identifiable requirements engineering phase **before** system implementation begins

---
### 4.2 FUNCTIONAL AND NON-FUNCTIONAL REQUIREMENTS
- The line between them is **not** always **clear** since requirements are not independent;
- The system requirements should include both types of requirements;
- Non-functional requirements may generates functional requirements;
  
#### 4.2.1 Functional Requirements and Non-Functional Requirements

##### 4.2.1.1 Functional Requirements
- **statements** of services the system should **provide**, also may state what the system should **not do**.
  - May be in different forms and at different levels of detail
  - may be high-level statements of what the system should do. 
  - should describe the system services in detail. 
  - should be **complete** and **consistent**.

1. **Functional User Requirements**
- The high-level (overview) of the what the system should do;
2. **Functional System Requirements**
- Detailed description of the services provided by the system;

**Example**
![](./pic/4_3.png)

##### 4.2.1.2 Non-Functional Requirements
- **System properties and constrains**
  - properties: reliability, response time, and storage requirements;
  - constrains: I/O device capability and the data representations;
- May be more **critical** than **functional requirements**
- more difficult to identify which system components implement specific non-functional requirements
  - may affect the **overall architecture** of a system rather than the individual components.(e.g. a 4 parts system, if only one part is safe, the whole system is not safe)
  - may generate other related functional and/or non-functional requirements

##### 4.2.1.3 Verifying Non-Functional Requirements
> Non-functional requirements may be difficult to state precisely, and imprecise requirements may be difficult to verify. 

Two parts:
- **Goals**:
  - A general intention of the user, like Ease of Use;
- **Verifiable (Testable)**:
  - Some measure (satisfaction) that can be objectively tested.

**Metrics for Specifying Non-Functional Requirements**
|Property(Goals)|Measure(Verifiable)|
|---|---|
|Speed|Processed transactions/second; User/event response time; Screen refresh time|
|Size|Mbytes; Number of ROM chips|
|Ease of use|Training time; Number of help frames|
|Reliability|Mean time to failure; Probability of unavailability; Rate of failure occurrence; Availability |
|Robustness|Time to restart after failure; Percentage of events causing failure; Probability of data corruption on failure |
|Portability|Percentage of target dependent statements; Number of target systems|

![](./pic/4_13.png)

*[Example]*
**Goals**
> The system should be **easy to use** by medical staff and should be organized in such a way that user errors are ***minimized***. 

**Verifiable**
> Medical staff **shall** be able to use all the system functions **after four hours of training** (easy to use). After this training, the average number of errors made by experienced users ***shall not exceed two per hour*** (minimized) of system use.

---
##### 4.2.1.4 Challenges in Specifying Non-Functional Requirements
- Difficult for customer to **translate their goals** into measurable requirements.
  - No simple metrics for some goals (e.g., maintainability) 
  - Unclear connection between metrics and everyday experience 
  - High costs for verification

- **conflict** and **interact** with *other* functional and/or non-functional requirements

- **difficult** to **separate** functional and non-functional requirements in the requirements document.

---
### 4.3 REQUIREMENTS ENGINEERING PROCESSES
Generic activities common to all processes
- Requirements elicitation; 
- Requirements specification; 
- Requirements validation;

In practice, RE is an iterative activity in which these processes are interleaved.

![](./pic/4_5.png)

---
### 4.4 REQUIREMENTS ELICITATION

#### 4.4.1 Requirements Elicitation
>  working with stakeholders to find out about the **application domain**, **work activities**, **services, system features** that **stakeholders want**, etc.

Stages:
- **discovery and understanding**:
  - Interacting with stakeholders to discover their requirements
- **classification and organization**:
  - Groups related requirements and organises them into coherent clusters.
- **Prioritisation and negotiation**:
  - Prioritising requirements and resolving requirements conflicts.
- **Documentation**:
  - The requirements are documented and input into the next round of the spiral.

![](./pic/4_6.png)

##### Techniques - 1
**Interviewing**
- Closed interviews vs. Open interviews
- Normally a mixture of closed and open interviewing. 

**Problems**
- Application specialists may use language that isn’t easy for the requirements engineer to understand to describe their work. 
- Interviews are not good for understanding domain requirements

**Effective interviewing**
- Be open-minded, avoid pre-conceived ideas about the requirements, and be willing to listen to stakeholders. 
- Prompt the interviewee to talk about the system by suggesting requirements rather than simply asking them what they want.

##### Techniques - 2
Observation or ethnography 

**Benefits**:
- People do not have to explain or articulate their work.
- It is relatively inexpensive.
- The observer will get a practical insight into the work. Social and organizational factors of importance may be observed.
- Improvement areas can be easily identified.

**Drawbacks**:
- Participants might get disturbed.
- Participants might change their way of working during observation and the observer might not get a clear picture. 
- Knowledge-based activities (e.g., debugging) are hard to observe.

##### Problems of Requirements Elicitation
- Stakeholders don’t know what they really want. 
- They express requirements in their **own** terms and with implicit knowledge of their work. 
- Different stakeholders, with diverse requirements, may express their requirements in different ways. 
- Organisational and political factors may influence the system requirements. 
- The requirements change during the analysis process. New stakeholders may emerge, and the business environment may change.

---
### 4.5 REQUIREMENTS SPECIFICATION
> The process of writing down the user and system requirements in a requirements document.

#### 4.5.1 Requirements Specification
The process of writing down the user and system requirements in a **requirements document**.
- User requirements: **understandable** by **end-users** and **customers** who **do not have a technical background**. 
- System requirements: more **detailed** requirements and may include more technical information.

Common notations for writing system requirements
- Natural language sentences
- Structured natural language
- Graphical notations
- Mathematical specifications

**requirements**: **what** the system should do
**design**: **how** it does this.

They are **inseparable**;

---
#### 4.5.2 Natural Language Specifications
Guidelines on writing natural language requirements
- **standard forma**t and use it for all requirements.
- Use "**shall**" for **mandatory** requirements; Use "**should**" for **desirable** requirements. 
- Use text highlighting to identify key parts of the requirement. 
- Avoid the use of computer jargon. 
- Include an **explanation** (rationale) of why a requirement is necessary.

> **Example**
> ![](./pic/4_7.png)

---
#### 4.5.3 Structured Natural Language Specifications
> An approach to writing requirements in a standard way rather than as **free-form text**. 
> - Maintains most expressiveness and understandability of NL
> - Removes some of the problems of NL specification 
> - It is still sometimes difficult to write requirements in a clear and unambiguous way

**Example**
![](./pic/4_8.png)

---
#### 4.5.4 Use Cases
> Describe interactions between users and a system using a **graphical model** and **structured text**.
- Identify the actors involved in an interaction and name the type of the interaction. 
- Additional information can be added to describe the interaction

Use case diagram
- Each use case (a named ellipse) represents a class of interaction. 
- An actor (a stick figure) is a person or a system.
- Lines link actors with the interaction. 
- Documented with a textual description

> *[Example] - UML*
> ![](./pic/4_9.png)

---
#### 4.5.5 Requirements and Design
> - **requirements** should state **what** the system should do
> - **design** should describe **how** it does this. 
> - requirements and design are **inseparable**

---
#### 4.5.6 The Software Requirements Specification (SRS)
> The official statement of what the system developers should implement
> It is NOT a design document. As far as possible, it should set out WHAT the system should do rather than HOW it should do it.

- The information in the SRS depends on the type of system and the development process used. 
- Should include both user and system requirements. 
- Requirements specification standards have been designed (e.g., IEEE standard).

---
#### 4.5.7 The Structure of A Requirements Specification
![](./pic/4_10.png)
![](./pic/4_11.png)

---
### 4.6 REQUIREMENTS VALIDATION

#### 4.6.1 Requirements Validation
> The process of **checking** that requirements **define** the **system** that the **customer** really **wants**

*Overlaps with elicitation and analysis*

**Types of checks**
- **Validity** checks. Do the requirements reflect the real needs of system users? 
- **Consistency** checks. Are there any requirements conflicts? 
- **Completeness** checks. Are all functions required by the customer included? 
- **Realism** checks. Can the requirements be implemented, given the available budget and technology? 
- **Verifiability** checks. Can the requirements be verified?

---
#### 4.6.2 Requirements Validation Techniques
Various techniques that can be used **individually** or **together**
- ==Requirements reviews==: **Systematically** and **manually** analyze the requirements to check for errors and inconsistencies
  - Should be held regularly
  - Should involve both client and contractor staff
  - May be formal (with completed documents) or informal.

- ==Prototyping==: Using an **executable** model of the system to check requirements. 
- ==Test-case generation==: Developing tests for requirements to check verifiability.

---
### 4.7 REQUIREMENTS CHANGE

#### 4.7.1 Changing Requirements
Once a system is installed and regularly used, **new requirements *inevitably* emerge**.
- original requirements may have errors and omissions. 
- business and technical environment of the system always changes after installation. 
- stakeholders as well as their priorities and requirements may change

---
#### 4.7.2 Requirements Traceability Matrix
It helps to
- link requirements to business and project objectives,
- track requirements throughout the software life cycle, and
- manage changes.

---
## 5 System Modeling
> The process of developing abstract models of a system

**model**
- an **abstraction** of the system being studied
- **not** an **alternative representation** of that system. 

each model presents a **different view/perspective** of the system
- External, structural, behavioral, interaction, etc.

Models can be
- from different perspectives
- in different forms 
  - **graphical** 
  - **formal/mathematical**
  - **natural language**
- for systems at different stages 
  - **existing**
  - to be **developed**

---
**Abstraction & Representation**
- ***Abstraction***
  - Focus on the **essential** aspects of the system, without the **irrelevant** details, leave out the details;
    - Model is an abstraction of the system;
    - Not an alternative representation;
      - For a English book:
        - the representation is the Chinese version;
        - the slide is the abstraction of the book;

- ***Representation***
  - Each model **represents** a system from a **particular** perspective;
    - **External** perspective: context or environment of the system;
    - **Interaction** perspective: Interactions between systems and external agent between system components;
    - **Structural** perspective: components, organizations, data structures;
    - **Behavioral** perspective: dynamic behavior, responds;
  - example: UML (Unified Modeling Language) diagrams

---
### 5.1 Usage of Graphical System Models
- **stimulate** and focus **discussion** about a system
  - **incomplete** and **informal** (normal in agile modeling) 
- **document** an existing system
  - **correct** but **incomplete**
- **generate** a system implementation
  - **correct** and **complete**

---
### 5.2 UML (Unified Modeling Language)
> UML is a standard language for  specifying, visualizing, constructing, and documenting (software) systems.
> A general purpose modeling language for (OO software) systems

**Diagram Types**
- A UML model consists of diagrams and documentation that complements\ the diagrams

![](./pic/5_1.png)

---
### 5.3 Context Models
> illustrate a system's operational context

- shows other systems used by or depend on the system being developed
- not how the system interact with each other

**System boundary**
- what is inside and outside
- social and organizational concerns may affect the system boundary

![](./pic/5_2.png)

> add arrow to indicate the direction of the work flow

---
#### 5.3.1 Process Perspective
- A type of the context;
- Context models simply show the other systems in the environment, but **NOT** the types of relationships between, no details;

![](./pic/5_3.png)

---
### 5.4 Interaction Models
> All systems involve interactions of some kind
- **user interaction** helps to identify user requirements 
- **component interaction** helps to understand the performance and dependability of the system
- **system-to-system interaction** highlights the communication problems may arise

**Two related approaches**
- **Use case diagrams** model interactions between systems and external agents (human users or other systems); 
- **Sequence diagrams** model interactions between system components (and external agents)

---
#### 5.4.1 Use Case Modelling
**Use Case diagram**

![](./pic/5_4.png)

ellipse: use case 
stick figure: actor, person, system

![](./pic/5_5.png)

---
#### 5.4.2 Sequence Diagrams
- Interactions between the **actors** and the **objects** within a system and those between the objects themselves.
- Shows the sequence of interactions that take place during a particular use case or use case instance.

**Sequence diagram**:
![](./pic/5_6.png)

**Loop**:
![](./pic/5_7.png)

**Condition**:
![](./pic/5_8.png)

**Sequence Diagram**
![](./pic/5_9.png)

---
### 5.5 Structural Models
> Organization of a system in terms of the components
> Class, Objects

- The organization of a system in terms of the components
  - Used when discussing and designing the system architecture

**Static** models: **Class**; used at both the analysis and the implementation phase of software development
**Dynamic** models: **Object**;

#### 5.5.1 Classes
- **encapsulates** **state** (*attributes*) and **behavior**(*operations*)

![](./pic/6_1.png)

- each attribute has a type, each operation  has a signature

---
#### 5.5.2 Relationships
> Dependency

**Instance-level** (objects are also called instances)
- Association
- Aggregation
- Composition

**Class-level**
- Generalization
- Realization/Implementation

**Dependency**
- **semantic** connection between **dependent** and **independent** classes (modules).
  - If changes to the definition of one class (module) (the server or target) may cause changes to the other (the client or source).

![](./pic/6_2.png)

---
##### 5.5.2.1 Instance-level Relationship
**Associations**
> a type of relation between class instances 
- using association to communicate classes

![](./pic/6_3.png)

- Class A has an attribute of type B 
- Class A creates instances of B 
- Class A received a message with argument of type B

**Association Multiplicity**
> Multiplicity denotes how many objects of the class take part in the relation

*[1-to-1]*
![](./pic/6_4.png)

*[1-to-many]*
![](./pic/6_5.png)

*[many-to-many]*
![](./pic/6_6.png)

**Special Associations (Has-A Relation) - Aggregation & Composition**
- **Aggregation**: “part-of” relation between objects
  - Component can be part of multiple aggregates
  - Component can be created and destroyed **independently** of the aggregate

![](./pic/6_7.png)

- **Composition**:  strong aggregation
  - Component can be part of **only one** aggregate
  - Exists only together with the aggregate

![](./pic/6_8.png)

**Navigability of Association**
- whether objects can be accessed through this association(directed)

![](./pic/6_9.png)

---
##### 5.5.2.2 Class-level Relationship
> Generalization relation
- `Is-A` relationship
- **inheritance**
  - Generalization simplifies the model by eliminating redundancy

![](./pic/6_10.png)

---
### 5.6 Behavioral Models
> a system **responds** to a **stimulus** from its **environment**. 
- a system's **dynamic behavior** as it executes.
- system **responds** to a **stimulus** from its environment
  - Data
  - Event

---
#### 5.6.1 Data-Driven Modeling
- show the sequence of actions involved in processing input data and generating an associated output. 
  - business system(data-processing system) is driven by data

*[Activity diagrams example]*

![](./pic/6_11.png)

*[Sequence diagrams example]*

![](./pic/6_12.png)

---
#### 5.6.2 Event-Driven Modeling
- shows how a system responds to external and internal **events**.
  - a finite number of states
  - events (stimuli) may cause transitions between states.
- UML state diagrams show system **states** and **events** that cause transitions from one state to another.

![](./pic/6_13.png)

> states are nodes; events are arcs between nodes

---
#### 5.6.3 States and Stimuli for The Microwave Oven

![](./pic/6_14.png)

---
#### 5.6.4 Superstates
- looks like a single state in a high-level model
- expanded to show more detail in a separate diagram

![](./pic/6_15.png)

---
## 6 Architectural Design
> how a software system should be organized and designing the overall structure
- output is an **architectural model**, describing how the system is organized as a set of communications components
- critical link between design and requirements engineering
- should be designed at the early stage of an agile development process

**Architectural Abstraction**
- *Architecture in the small* is concerned with the architecture of individual programs.
- *Architecture in the large* is concerned with the architecture of complex enterprise systems that include other systems, programs, and program components.

---
**Advantages of Explicit Architecture**
- Stakeholder communication:
  - high-level presentation;
  - Be understandable by non-technical people;
  - Discussed by a range of different stakeholders;
- System analysis:
  - Whether or not the system can meet critical requirements;
- Large-scale reuse:
  - be reusable across a range of systems
  - product-line architectures

---
**Representations**
- using simple block diagrams
  - Box: component
  - Boxes in boxes: component decomposition
  - Arrows: data and control flow

- no types of relationship or components externally visible properties

![](./pic/7_1.png)

---
### 6.1 Architectural Design Decisions
> The solution to the architecture choose;
- **Reuse**: template of generic application architecture
- How distribute **across** hardware core/processors? (optional);
- What patterns should be used?
  - how to structure?
  - how components be decomposed?
  - how to control components?
- Best for delivering the non-functional?
- How should the architecture of the system be documented?

---
**Architecture on Non-Functional Requirements**
- **Performance**:
  - Localize critical operations, minimize communications:
    - In local, not remote;
    - Using large, NOT small components/fine-grain;
- **Security**:
  - layered architecture with critical assets in the inner layers
- **Safety**:
  - Will not cause harm to the user and others;
  - Localize safety-critical features in a small number of sub-systems;
    - Perform several checking for each small sub-system rather than one big system;
- **Availability**:
  - Include redundant components and mechanisms for fault tolerance.
    - e.g. Multiple servers for a web application; one down, other can still provide service;
- **Maintainability**:
  - Use fine-grain, self-contained components that may easily be changed.
    - Easy to replace problem components;
    - Easy to extend;

---
### 6.2 Architectural Views
- Different view on a architecture design
  - Each architectural model **only** shows one views
- Informal models and notations
  - UML: remain the most way of documenting architectures

---
### 6.3 Architectural Patterns
> stylized description of good design practice
> - include information when they are/not to use
> - mixture of narrative description and diagrams

**Architectural patterns**:
- The Model-View-Controller (MVC) pattern
- The Client-Server pattern
- The Pipe and Filter pattern
- The Layered pattern
- The Repository pattern

---
#### 6.3.1 The Model-View-Controller (MVC) Pattern
**Model**
- manages system data and associated operations on that data

**View**
- defines and manages how the data is presented to the user

**Controller**
- manages interaction(key presses, mouse clicks, etc.) passes these interactions to View and Model


![](./pic/7_2.png)
![](./pic/7_3.png)

---
#### 6.3.2 Layered Architectures
> Organized into **separate layers**, and each layer **ONLY relies** on the facilities and services offered by **the layer immediately beneath it**.

![](./pic/7_4.png)

Benefit:
- Supports the **incremental development**;
- Layer interface changes, **ONLY the adjacent layer** is **affected**;
- Allows **replacement** of entire layers;

![](./pic/7_5.png)

**Disadvantage**:
- Clean separation between layers is often difficult
- High-level layer may have to interact directly with lower-level layers rather than through the layer immediately below it.
  - e.g., from 1 to 3 directly, not access 2; 2 provide a special gate;   
  - the performance will be low;

---
![](./pic/7_6.png)

---
#### 6.3.3 Repository Architectures
Exchange of data among subsystems:
- **Centralized** storage
  - Shared **data** is held in a **central** database. High efficiency;
- **Distributed** storage
  - Sub-system maintains its **own database(copy of)** and passes data explicitly to other sub-systems. Low efficiency;

![](./pic/7_7.png)

**Benefit**:
- Components can be independent;

**Disadvantage**:
- Repository is a single point of failure
- Distributing may be difficult;

---
![](./pic/7_8.png)

> **Repository** model: A repository is **passive**, the **components** to **control** with the data in repository;
> **Blackboard** model: A blackboard **notifies(actively)** components when particular data become available;
> - Updates in the blackboard will notifies other components;
---
#### 6.3.4 Client-Server Architectures
> **Distributed** system model.

**Stand-alone servers**:
- provide specific services such as printing, data management, etc.

**Clients**:
- call on these services they want to;
- Can be implemented on single computer

![](./pic/7_9.png)

**Advantages**:
- Servers can be distributed across a network;
- Servers can also be client to access other servers;

**Disadvantage**:
- Performance may be unpredictable because it depends on the network;

---
![](./pic/7_10.png)

---
#### 6.3.5 Pipe and Filter Architectures
> The **runtime organization** of a system where functional transformations process inputs and produce outputs

- **pipes**: link processes using "pipes"
- **filter**: transformation “filters out” the data it can process from its input data stream.

![](./pic/7_11.png)

**Advantage:**
- easy to understand and supports transformation reuse
- matches structure of many **business** processes

**Disadvantage:**
- format for data transfer has to be agreed
- Each **transformation** must **parse** its **input** and **unparse** its **output** to the **agreed form**;

---
![](./pic/7_12.png)

---
### 6.4 Application Architectures
- An architecture that encapsulates the principal characteristics of a class of systems;
- Be configured and adapted to create a system that meets specific requirements.

**Usage**
- As a **starting** point for architectural design.
- As a design **checklist**.
- As a way of organizing the work of the **development team**.
- As a means of assessing components for **reuse**.
- As a vocabulary for talking about **application types**

---
#### 6.4.1 Applications Types Examples
- **Transaction processing systems**:
  - Database-centred applications;
  - User requests for information and update;
  - Like E-commerce systems and information systems

- a customer request to withdraw money from a bank account using an ATM
  - May be organized as a “pipe and filter” architecture

![](./pic/7_13.png)

**Information Systems**
- can be organized as a layered architecture

---
- **Language processing systems**:

---
## 7 Brief Introduction to OOP in Java
**Variables**
- **Primitive** data types: boolean, char, byte, short, int, long, float, double 
- **Reference** data type: Sting, Date, etc.

**Expressions** and **expression statements**
- Assignment operators: =, +=, -=, *=, /=, …
- Arithmetic operators: +, -, *, /, %
- Unary operators: +, -, ++, --, !
- Equality and relational operators: ==, !=, >, >=, <, <=
- Conditional operators: &&, ||, ?:
- Type comparison operators: instanceof
- Bitwise and bit shift operators: ~, <<, >>, >>>, &, ^, | 

**Control Structures**
- Selection: if, switch
- Loop: for, while, do-while, break, continue
- Exception handling: try, catch, finally

---
### 7.1 Class and Object
**Filed** **(instance variable/state)**: the values can be stored;
**Method**: the **operations** can be performed;
```java
// Hero.java 
class Hero{
  String name; // field
  int health; // field
  void initHero(){…} // method
  void increaseHealth(int amount){…} // method
}
```

> Both fields and methods are instance members
---
- **Object**
  - contains all the fields in the class, and takes space;
  - Methods do **NOT** take any space in objects;
  - Multiple references can point to the same object (aliasing);

- ***Reference***: only contain **NULL** or the **address of the object**;

```java
Hero heroA,heroB,heroC // only the Hero reference, NO Hero object
```
---
**Call method**: **Sending a message** to an object

---
**Constructors**: **special** kind of **methods** that are invoked to **initialize** objects
- **MUST** have the **same name as the class itself**
- **MUST**: No return type, not even void;
- May have parameters, **NOT** `this`;

```java
// a regular method called Hero
void Hero(){...} // NOT a constructor
// constructors
Hero(){...} // default constructor
Hero(String name){...} // constructor with parameter
```

---
**Method overload**:
- Method **signature** = **Method name** + **List of parameter types**;
- Using signature to distinguish different methods, even with the same name;

---
### 7.2 Encapsulation
**Information Hiding**
> Principle of Least Privilege
> > Every module must be able to access only the information and resources that are necessary for its legitimate purpose.

**Access control**:
public(all) > protected(package+subclass) > default(package) > private(same class only)

---
### 7.3 Inheritance
**IS-A** relationship, reuse.
- To be **part** of:
  - Instance variables of the superclass are **PART** of the objects of the subclass **(Whatever public, private, protected, default)**;
- To **inherit**:
  - **Public** variables of the superclass are **inherited** into the subclass, which means the subclass can access them directly by using the variable name in the superclass;

---
### 7.4 Polymorphism
> poly: many; morph: shape, form
> `extends`

```java
public class Hero{
  private String name;
  private int health;
  public Hero(){…}
  public void travel(){…}
}

// keyword: extends
public class Monster extends Hero{
  private boolean isAngry;
  public Monster(){…}
  public void travel(){…}
}

Hero h; 
h = new Hero(); 
h.travel();  // calling travel() defined in
Hero h = new Monster(); 
h.travel();  // calling travel() defined in Monster
```

> **Generic Programming**: need to know the precise type of an object.

---
###  7.5 Abstract Class and Methods
> A abstract method with NO any implementation within the current class 
- A class with at least one abstract method must be abstract 
  - can be inherited 
  - meant to be overridden

> The compiler does not allow to create any instance of an abstract class, as the class is not complete yet

---
### 7.6 Interface
> Groups of abstract methods
> provides a way to define **common behavior(s)** that multiple classes can adhere to, **WITHOUT** specifying the actual implementation details.
- **NO instance field** 
- All instance methods **MUST** be **public** and **abstract**.
  - Keywords public and abstract can be **omitted**;

```java
// Parent interface
interface Animal {
    void eat();
    void sleep();
}

// Child interface extending the Animal interface
interface Pet extends Animal {
    void play();
}

// Implementing the interfaces in classes
class Dog implements Pet {
    public void eat() {
        // Implementation for eating behavior
    }
    public void sleep() {
        // Implementation for sleeping behavior
    }
    public void play() {
        // Implementation for playing behavior
    }
}
```

---
## 8 Object-Oriented Analysis and Design

### 8.1 Object-Oriented Analysis (OOA)
- **Goal**: **understand** the problem and to begin to develop a model of what you are trying to build (**problem domain**)
- **Independent** of implementation and technology concerns. 
- Translating the **functional requirements** into software concepts.
  - get a rough cut at the object
  - 
Two types:
- **Function-oriented** analysis – concentrating on the **decomposition of complex functions** to simple ones. 
- **Object-oriented** analysis – identifying **objects** and the
**relationship** between objects.

![](./pic/8_1.png)

---
#### 8.1.1 Domain Model
> representation of conceptual classes in a domain of interest

- Using UML notation, a set of class diagrams
- It may show:
  - conceptual classes 
  - associations between the conceptual classes 
  - attributes of the conceptual classes
- NOT in domain model
  - Software artifacts, like window or a database 
  - Responsibilities, or
  - methods.

---
***1. Conceptual classes***
- **Real-world concept** or thing, NOT an implementation class
- It is better to **over-specify** a domain model with many fine-
grained conceptual classes than to under-specify it.

**Identify conceptual classes**
- Conceptual class category
![](./pic/8_2.png)

- Noun phrase identification
  - find noun phrases in the specification
![](./pic/8_3.png)

---
1. Discard some class:
   - Outside the current requirements, `Price Rule`
   - Redundant, `System`
   - Looks like an attribute more than a class, `Price`
   - NOT being considered in this iteration, `Receipt`
   - NO correct set of conceptual classes

2. Draw them in a domain model, i.e., a set of UML class diagram
3. Add associations and attributes

---
***2. Associations between conceptual classes***
> relationship between types (or instances of those types)
- Not a statement about data flows, instance variables, or object connections in a software solution

How to find relationship:
- It is more important to identify conceptual classes than to identify associations. 
- **Too many** associations confuse a domain model
- **Avoid** showing **redundant** or **derivable** associations.

---
***3. Attributes***
> logical data value of an object
- Mistake 1：may treat a class as an attribute;
  - Treat a `destination`(Airport) as a class than as a attribute of a flight
- Mistake 2: Add a kind of foreign key attribute, as is typically done in relational database designs,

---
### 8.2 Object-Oriented Design (OOD)
**Goal**: A process that uses the analysis results to produce a specification for implementing a system.
- Emphases on **defining** software objects and how they collaborate to **fulfill** the requirements.
  - look at class design in detail 
  - design activities like database design and interface design 
**Result**: the specification of a logical software solution in terms of software objects, 
- such as **classes**, **attributes**, **methods**, and **collaborations**.
- 
---
Two kinds of design models: **dynamic** and **static**.
- **Static**
  - definition of packages, class names, attributes, and method signatures (but not method bodies).
  - UML class diagram
  - Fundamental activity: Assigning **responsibilities** to classes/objects!
- **Dynamic**
  - the logic and the behavior of the code or the method bodies.
  - UML interaction diagram(e.g., sequence diagrams)

---
#### 8.2.1 Doing and Knowing Responsibilities
**Doing responsibilities**
- **Methods**:
  - **creating** an object or doing a calculation
- **Initiating** actions in other objects
- **Controlling** and coordinating activities in other objects
 
**Knowing responsibilities**
- knowing about private encapsulated data
- related objects
- Things it can **derive** or **calculate**

---
#### 8.2.2 Responsibility-Driven Design (RDD)
>  A general metaphor for thinking about OOD
>  Software **objects** are like **people** with **responsibilities** who collaborate to get **work done**
- Responsibilities are implemented by means of methods
  - Either act alone or collaborate with other methods and objects

---
**How to do RDD**
- Using **Class-Responsibility-Collaborator (CRC)** Cards
  - One card per class, shows its responsibilities and with which other class(es) it must collaborate to fulfill each responsibility 
  - A brief description of the class on the back of the card.

![](./pic/8_4.png)

- In the example, class `Foo` must collaborate with (send messages to) `ClassX` and `ClassY` in order to fulfill its responsibility to be able to "`do something`."

---
### 8.3 SOLID DESIGN PRINCIPLES
- **S**ingle responsibility principle
- **O**pen/closed principle
- **L**iskov substitution principle
- **I**nterface segregation principle
- **D**ependency inversion principle

---
#### 8.3.1 Single Responsibility Principle
> Each responsibility is a reason for change. 
> A class should have **ONLY ONE** reason to change.

![](./pic/8_5.png)
![](./pic/8_6.png)

---
#### 8.3.2 Open/Closed Principle
> Software entities should be **open** for **extension** (good for inheritance)
> but **closed** for **modification**.(modification should not be open to clients)

![](./pic/8_7.png)
![](./pic/8_8.png)
![](./pic/8_9.png)


---
#### 8.3.3 Liskov Substitution Principle
> Objects in a program should be **replaceable** with instances of their **subtypes** without **altering** the correctness of that program

![](./pic/8_10.png)
![](./pic/8_11.png)

---
#### 8.3.4 Interface Segregation Principle
> Many client-specific interfaces(small) are better than one general-purpose(big) interface. One interface for each responsibility.

![](./pic/8_12.png)

---
#### 8.3.5 Dependency Inversion Principle
> Limited reusability of the higher-level components
> High-level modules should not depend on low-level modules. Both should depend on **abstractions**(interface);
> **Abstractions** should **NOT** depend on **details**. Details should depend on **abstractions**.

![](./pic/8_13.png)

---
## 9 Software Testing
### 9.1 Program Testing
- **Testing** is intended to show that a program does what it is intended to do and discover program defects before it is used.
  - using input data and checking the results of the test run for errors, anomalies, or information about the program’s non-functional attributes.

**Goals:** 
- To **demonstrate** to the developer and the customer that the **software** **meets** its **requirements**.
-  To **discover** situations in which the behavior of the software is incorrect, undesirable or does not conform to its specification

![](./pic/9_1.png)

---
#### 9.1.2 Validation and Defect Testing
- first goal leads to **validation testing**
  - perform correctly using a given set of test cases
  - A successful test shows that the system operates as intended.
- second goal leads to **defect testing**
  - The test cases are designed to expose defects.
    - The test cases in defect testing can be deliberately obscure and need not reflect how the system is normally used.
  - A successful test makes the system perform incorrectly and expose a defect in the system.
  - Can reveal the presence of errors but NOT their absence.
  - Extreme case like, Integer.MAX_VALUE;

---
#### 9.1.3 Verification and Validation
> Testing is part of a more general V&V process

- Verification: The software should conform to its specification.
  - "Are we building the product right”. 
- Validation: The software should do what the user really requires.
  - "Are we building the right product.”
- Aim to establish confidence that the system is "fit for purpose"
  - Software purpose:The level of confidence depends on how critical the software is to an organization. 
  - User expectations: Users may have low expectations of certain software. 
  - Marketing environment: Getting a product to market early may be more important than finding defects in the program.

---
#### 9.1.4 Software Inspections
> examining the source representation with the aim of discovering anomalies and defects.
- Applicable to any representation of the system(Requirements, design,configuration data, test data, etc)
- During testing, errors can **mask**(hide) other errors.
  - a static process, do not have to be concerned with interactions between errors;
- broader quality attributes of a program, like compliance with standards, **portability**, **maintainability**, etc.

---
#### 9.1.5 Stages of Testing
- **Development testing**: test during development to discover bugs and defects. 
- **Release testing**: tests a complete version of the system before it is released to users.(separate testing teal)
- **User testing**: Users or potential users of a system are involved in testing

![](./pic/9_2.png)

---
### 9.2 DEVELOPMENT TESTING
#### 9.2.1 Development Testing
> Including **all** testing activities carried out by the development team

- **Unit testing**: Individual program units or object classes are
tested.
  - Focus on testing the functionality of objects or methods. 
- **Component testing**: Individual units are integrated to create composite components.
  - Focus on testing component interfaces.
- **System testing**: Some or all of the components in a system are integrated, and the system is tested as a whole.
  - Focus on testing component interactions.

**White** box testing vs. *black* box testing
- **With** vs. *without* knowledge about the internal structure, design, or implementation of the software

---
#### 9.2.2 Unit Testing
- The process of testing individual code units in isolation
  - Individual functions or methods within an object 
  - Object classes with several attributes and methods

**Object class testing**: Coverage of all the features of an object
- Getting and setting **ALL** object attributes 
- Testing **ALL** operations associated with an object 
- Exercising the object in **ALL** possible states. 
- Simulating **ALL** events that cause a state change.
- Inheritance makes it more difficult to design object class tests as the information to be tested is not localized.

**Automated Testing**
- unit test execution should be automated 
- **Automated Test Components**
  - A **setup** part, namely the inputs and expected results whe initiating the test
  - A **call** part, call the object or method to be tested
  - An **automated mechanism** to **compare** the **result** of the call with the **expected result**
- **Test Automation Framework**
  - like JUnit
  - use framework to write and run tests
  - provided generic test classes

---
**Testing Strategies**
- **Partition testing**
  - Identify groups have common characteristics
  - should be processed in the same way
  - Choose tests from within each of these groups.
- **Guideline-based testing**
  - **Software with sequences**
    - only a single value.
    - different sizes in different tests
    - Derive tests so that the sequence's first, middle, and last elements are accessed. 
    -  sequences of zero length.
  - **General software**
    - Choose inputs that force the system to generate all error messages
    - cause input buffers to overflow;
    - Repeat the same input or series of inputs numerous times;
    - Force computation results to be too large or too small.

---
#### 9.2.3 Component Testing
- Software **components** are often composite units comprising several interacting objects. 
- functionality is accessed through defined interface:
  - component interface behaves according to its specification. 
  - assume unit tests on individual objects within component is completed
  
---
**Interface Testing**
Goals: detect **faults** due to **interface errors** or **invalid interface assumptions**. 

**Interface types**
- Parameter interfaces. 
- Shared memory interfaces. 
- Procedural interfaces. 
- Message passing interfaces.

**Interface Errors**
- Interface misuse 
- Interface misunderstanding 
- Timing errors

---
**Interface Testing Guidelines**
- Design tests so that parameters to a called procedure are at the extreme ends of their ranges.
- Always test pointer parameters with null pointers. 
- Design tests that cause the component to fail. 
- Use stress testing in message-passing systems. 
- In shared memory systems, vary the order in which components are activated.

---
#### 9.2.4 System Testing
- Involves **integrating** components to create a system and then testing the integrated system.
  - Tests can be derived from the use cases 
  - checks that components are compatible, interact correctly, and transfer the right data at the right time
- System testing **overlaps** with component testing, but there are two important differences:
  - The complete system is tested. 
  - A collective rather than an individual process.
    - component testing may be **individual**

**Testing Policies**
- **Exhaustive** system testing is **impossible**;
- required system **test coverage** may be developed.
  - When to **stop** the testing;
- **Policies**:
  - Functions accessed through **menus** should be tested;
  - Combinations of functions (e.g., text formatting) that are **accessed through the same menu** must be tested;
  - On user input is provided, all functions must be tested with both **correct and incorrect input**.
  
---
**Regression testing**
> check that changes have not 'broken' previously working code.
- In a manual testing process, regression testing is expensive.
- With automated testing, it is simple and straightforward
- All tests are rerun every time a change is made to the program
- Tests must run 'successfully' before the change is committed.

---
### 9.3 Release Testing
#### 9.3.1 Release Testing
> testing a particular release of a system that is intended for use outside of the development team.
> Validation testing;
- to convince the supplier of the system that it is good enough for use(primary goal)
  - has to show system delivers specified functionality, performance, and dependability
  - no expected behaviors or results
- black-box testing process

---
#### 9.3.2 Release Testing and System Testing
- A form of system test
  - **Requirements-based** testing examines each requirement and developing or tests for it. 
  - **Scenario** testing uses typical scenarios to develop test cases for the system.

**Differences**
- separate team in release testing, NOT in system testing;
- Discovering bug is in System testing, NOT in release testing;
- Release testing: meets its requirements and is good enough for external use (validation testing).

---
**performance testing**
- performance and reliability. 
- Tests should reflect the profile of use of the system. 
- **Performance tests**: planning a series of tests where the load is steadily increased until the system performance becomes unacceptable. 
- **Stress testing**: a form of performance testing - system is **deliberately overloaded** to test its failure behavior.

---
### 9.4 User Testing
> users or customers provide input and advice on system testing.
- Essential than system and release testing have been carried out.
  - influences from the user’s working environment have a major effect on the reliability, performance, usability, and robustness of a system.

---
**Types of User Testing**
- **Alpha testing**: Users are involved, but still inside the develop team; from their site;
- **Beta testing**: **open to users** to allow them to experiment with a special release of software
> above are on how test performed.
- **Acceptance testing**
  - whether or not it is ready to be accepted from the system developers and deployed in the customer environment.
  - An inherent part of custom systems development.

---
**The Acceptance Testing Process**

![](./pic/9_3.png)

- Agile Methods and Acceptance Testing
  - user/customer is part of the development team and is responsible for making decisions on the acceptability of the system.
  - NO separate acceptance testing process.

---
## 10 Software Evolution
**Software change is inevitable**
- Errors must be repaired;
- Performance or reliability of the system may have to be improved.
- Business environment changes;
- New computers and equipment is added to the system;
- New requirements emerge when the software is used;

![](./pic/10_1.png)

**Evolution**
- The software system is in operational use
- Significant changes to the architecture and functionality are made
  
**Servicing**
- The software remains useful
- Only small tactical changes are made

**Retirement**
- **Only essential** changes are made, and users must work **around problems** 
- The software is taken out of use after its data is transferred

![](./pic/10_2.png)

---
### 10.1 Evolution Processes
**Depend** on
- type of software being maintained;
- development processes used;
- skills and experience of the people involved. 

**Proposals for change are the driver for system evolution**
- bug reports from system stakeholders
- requests for adaptation to the new environment
- new ideas for software improvement from the system development team 
- requests for new requirements

---
#### 10.1.1 General Model
![](./pic/10_3.png)

**Change Implementation**
- Iteration of the development process where the revisions to the system are designed, implemented, and tested. 
- Different between development and evolution
  - the **first stage** of **change implementation** may involve program understanding

#### 10.1.2 Change Management Process
> The process of analyzing the **costs** and **benefits** of proposed changes
> > approving those changes that are cost-effective, and tracking which components in the system have been changed.

![](./pic/10_4.png)

#### 10.1.3 Agile Methods and Evolution
- Agile methods are based on **incremental** development so the transition from **development** to **evolution** is a ***seamless*** one.
  - Evolution is simply a **continuation of the development process** based on **frequent system releases**. 
  - **Automated regression testing** is particularly valuable when changes are made to a system. 
  - Changes may be expressed as additional user stories.
- **Problems**
  - Development team $\to$ agile approach, however evolution team $\to$ plan-based approach
  - A plan-based approach has been used for development, but the evolution team prefer to use agile methods.

---
### 10.2 Software Maintenance
> Modifying a custom software after it has been put into use
> Generic software products evolve to create new versions. 
>> Does not normally involve **major changes** to the system’s **architecture**. 
>> Changes are implemented by modifying existing components and adding new components to the system.

**Types of maintenance**
- Fault repairs(24%)
- Environmental adaptation(19%)
- Functionality addition and modification(58%)

---
#### 10.2.1 Maintenance Cost
> greater than development costs (2* to 100* depending on the application). 
- Cost increases as software is maintained.
- Expensive to add new features to a system during **maintenance** than it is to add the same features during **development**
- **Reasons**s:
  - Program maintenance work is **unpopular**
  - Separating maintenance and development means **no incentive** for the development team to write maintainable software 
  - New team has to understand the programs being maintained 
  - As programs age, their structure **degrades**, and they become **harder to change**

---
#### 10.2.2 Software Re-engineering
- Restructuring or rewriting part or all of a legacy system without changing its functionality
  - make them easier to maintain.

![](./pic/10_5.png)

**Advantages of reengineering over replacement**
- Reduce risk
- Reduce cost

**Reengineering cost factors**
- **Quality** of the software to be reengineered.
- **Tool** support available for reengineering.
- **Extent of the data conversion** which is required.
- Availability of **expert** staff for reengineering. 

**Limitation**
- Converting the programming paradigm is impossible
- Major architectural or data management changes are **expensive**
- The resulting system probably is not as **maintainable** as a new system

---
### 10.2.3 Refactoring vs. Re-engineering
- **Refactoring**
  - A **continuous** process of improvement throughout the **development and evolution process**
     - When refactoring a program, you should **NOT** add **functionality** but rather **concentrate** on program improvement.
     - Like preventative maintenance
  -  It is intended to avoid the structure and code **degradation** that **increases** the **costs** and **difficulties** of maintaining a system.
- **Re-engineering**
  - Happens after a system has been maintained for **some** time and maintenance **costs** are **increasing** 
  - Uses automated tools to process and re-engineer a legacy system to create a new, more **maintainable** system.

---
### 10.3 Version Management
> The process of keeping **track** of **different versions** of software **components** or **configuration** items and the systems in which these components are used.
- Ensures that changes made by different developers to these versions do not interfere with each other.

---
#### 10.3.1 Codelines and Baselines
- **Codeline**
  - A sequence of versions of source code with later versions in the sequence derived from earlier versions. 
- **Baseline**
  - specifies the component versions included in a specific system and the libraries and configuration files, etc., used.

![](./pic/10_6.png)

---
#### 10.3.2 Version Control Systems
> **Identify**, **store** and **control** access to the **different versions of components**. 

- **Two types**
  - Centralized systems: a single master repository that maintains all versions of the software components that are being developed.
    - Example: Subversion
  - Distributed systems: Multiple versions of the component repository exist simultaneously.
    - Example: Git

- **Five Features**
  - Version and release identification 
  - Change history recording 
  - Support for independent development 
  - Project support 
  - Storage management

---
Version control systems vs. cloud storage systems
- VCS
  - Contains multiple changes;
  - Help to merge the changes
- CSS
  - Totally overwrite the old version, like Google Drive;

---
#### 10.3.3 Project Repository and Private Workspace
**Project Repository**
- Maintains the '**master**' version of all components, which is used to create **baselines** for system building.
  - When modifying components, developers copy (check-out) these from the repository into their workspace and work on these copies. 
  - When they have finished their changes, the changed components are returned (checked-in) to the repository.

**Centralized vs. distributed**
- In **centralized** version control, a **private workspace contains only components** from the project repository. 
- In **distributed** version control, a **clone** of the project repository.

![](./pic/10_7.png)

**Benefits of Centralized vs Distributed VC**
- **Centralized**
  - It is easier to learn and set up 
  - It takes less time and space to download part of a project
- **Distributed**
  - Provides a backup mechanism for the repository
  - Allows for offline working
  - faster
  - Project support is the default way of working 
  - Working on branches is easier 
  - Fewer merge conflicts with other developer’s code

---
#### 10.3.4 Organization of Open-Source Development

![](./pic/10_8.png)

---
#### 10.3.5 Branching and Merging
- Rather than a linear sequence of versions that reflect changes to the component over time, there may be several independent sequences.
- **Branch**:
  - Avoid to interfere with each other;
- **Merge**:
  - Merge codeline branches to create a new version of a component that includes all changes that have been made.
  - Improve the flexibility of the VCS; when new idea coming in;

---
#### 10.3.6 Storage Management
- Instead of keeping a complete copy of each version, the system **stores a list of differences (deltas)** **between one version and another**, because disk space was expensive. (Centralized VCS)
- Drawback:
  - Difficult to get the least version of the code; find from the first version from beginning;
  - chain of operations.

![](./pic/10_9.png)

---
**Git**
- (Distributed VCS)
- Git does **NOT** use **deltas** but
- applies a standard **compression** algorithm to stored files and their associated meta-information.
- **does not store duplicate copies of files**.
- simply involves decompressing it, with no need to apply a chain of operations.

![](./pic/10_10.png)

---
### 10.4 Legacy System
> **Older** systems that rely on languages and technology that are no longer used for new systems development.

**Problems**
- Legacy system replacement is risky and expensive
  -  Lack of complete system specification
  - Tight integration of system and business processes
  - Undocumented business rules embedded in the legacy system
  - New software development may be late and/or over budget 
- Legacy systems are expensive to change
  - No consistent programming style
  - Use of obsolete programming languages with few people available with these language skills 
  - Inadequate system documentation 
  - System structure degradation 
  - Program optimizations may make them hard to understand 
  - Data errors, duplication, and inconsistency

---
## 11 Software Reuse
**Reuse-based software engineering**
- System reuse 
- Application reuse 
- Component reuse 
- Object and function reuse

**Benefits**
- Accelerated development
- Effective use of specialists
- Increased dependability
- Lower development costs
- Reduced process risk
- Standards compliance

**Problems**
- Creating, maintaining, and using a component library
- Finding, understanding, and adapting reusable components
- Increased maintenance costs
- Lack of tool support
- Not-invented-here syndrome

---
### 11.1 Reuse Landscape
- Reuse is possible at a range of levels from simple functions to complete application systems. The reuse landscape covers the range of possible reuse techniques.

![](./pic/11_1.png)

**Approach**

|Approach|Description|
|:---:|:---:|
|Architectural patterns|Standard software architectures that support common types of application patterns system are used as the basis of applications|
|Program libraries|Class and function libraries that implement commonly used abstractions are available for reuse.|
|Application frameworks|Collections of abstract and concrete classes are adapted and extended to create application systems.|
|Software product lines|An application type is generalized around a common architecture so that it can be adapted for different customers.|
|Component-based software engineering|Systems are developed by integrating components (collections of objects) that conform to component-model standards.|
|Service-oriented systems|Systems are developed by linking shared services, which may be externally provided.|
|Design patterns|Generic abstractions that occur across applications are represented as design patterns showing abstract and concrete objects and interactions.|
|Model-driven engineering|Software is represented as domain models and implementation independent engineering models and code is generated from these models.|
|Application system integration|Two or more application systems are integrated to provide extended functionality|


![](./pic/11_2.png)

**Reuse Planning Factors**
- The development **schedule** for the software. 
- The expected software **lifetime**. 
- The **background**, skills and experience of the development team. 
- The **criticality** of the software and its **non-functional requirements**. 
- The application **domain**. 
- The execution platform for the software.

**Reasons not to reuse**
- Unwillingness to compromise the requirements
- Preference to known risks of development over unknown risks of reuse, even if the latter may be larger

---
### 11.2 APPLICATION FRAMEWORKS
> "an integrated set of software artifacts(such as classes, objects, and components) that collaborate to provide a **reusable** architecture for a family of related applications." 
- Classes are reused directly and may be extended using features such as inheritance and polymorphism.
- Frameworks support design **reuse** 
  - providing a skeleton architecture for the application
  - specific classes in the system. 
- Frameworks provide support for generic features
  - all applications of a similar type 
- The problem with frameworks is complexity, meaning a long time yo use effectively.

---
#### 11.2.1 Web Application Frameworks(WAFs)
- Commonly used to develop web applications
  - Spring for Java, Django for Python, and Angular for JavaScript. 
  - Support the **construction** of **dynamic** websites as a **front-end** for web applications.
    - Security, dynamic web pages, database support, session management, user interaction
  - Architecture of WAFs is based on MVC composite pattern.

![](./pic/11_3.png)

---
#### 11.2.2 Extending Frameworks
- Frameworks are generic and are extended to create a more specific application or sub-system. 
- Involves:
  - Adding concrete classes that inherit operations from abstract classes in the framework; 
  - Adding (callback) methods that are called in response to events that are recognized by the framework.

![](./pic/11_4.png)

---
### 11.3 SOFTWARE PRODUCT LINES
> A set of applications with a common architecture and shared components, with each application specialized to reflect different requirements.
> > Printer drivers, MS Office

- **Specialization**
  - Selecting from a library of existing components; 
  - Component and system configuration; 
  - Modifying components to meet new requirements. 
  - Adding new components to the system;

---
#### 11.3.1 Base System
- Software product lines usually emerge from existing applications. 
- Designing a generic product line involves 
  - identifying **common functionality** in product instances; 
  - developing a **base application** to **simplify** reuse and reconfiguration. 
- A base application includes
  - Core components that provide **infrastructure** support;
  - **Configurable** components that may be **modified** and **configured** to **specialize** them to a **new application**. 
  - Specialized, domain-specific components some or all of which may be **replaced** when a new instance of a product line is created.

![](./pic/11_5.png)

---
#### 11.3.2 Application Frameworks and Product Lines
- **Both** 
  - support a common architecture and components
  - require new development to create a specific version of a system. 
- **Differences**

|Application framework|Software product line|
|:---:|:---:|
|Application frameworks rely on object-oriented features|Product lines need not be object-oriented.|
|Application frameworks provide general rather than domain- specific support|Product lines embed domain and platform information.|
|Application frameworks are usually software-oriented.|Product lines are often control applications for equipment.|
|Application frameworks are Not|Product lines are made up of a family of applications, usually owned by the same organization.|


- The architecture of a software **product line** often reflects a **general, application-specific** architectural style or pattern.

![](./pic/11_6.png)

---
### 11.4 COMPONENT-BASED SOFTWARE ENGINEERING (CBSE)
> An **approach** to software development that relies on the reuse of entities called "software components"
- The failure of **object-oriented development** to support effective reuse: **Single object classes** are **too detailed** and **specific**. 
- Components are more **abstract** than object classes and can be **stand-alone** service providers.

- **CBSE essential**
  - Independent components specified by their interfaces.
  - Component standards to facilitate component integration.
  - Middleware that provides support for component inter-operability
  - A development process that is geared to reuse.

**Component Characteristics**

![](./pic/11_7.png)

---
#### 11.4.1 Components As Providers of Services
- A component is a provider of one or more services
  - an **independent executable entity** defined by its **interfaces**.
- In principle, all components have two related interfaces
  - The "**provides**" interface: defines the **services** provided by the component. 
  - The "**requires**" interface: specifies the **services** that **other components** in the system must provide if a component is to operate **correctly**.

![](./pic/11_8.png)

---
#### 11.4.2 Component Models
- A component model defines **standards** for component **implementation**, **documentation**, and **deployment**.
  - EJB model (Enterprise Java Beans) 
  - COM+ model (.NET model) 
  - CORBA Component Model (CCM)

- Basic elements
  - Interfaces 
  - Usage information 
  - Deployment

![](./pic/11_9.png)

---
**Component Model Implementation**
- A component model implementation provides **platform services** and **support services**

![](./pic/11_10.png)

- Components can be considered as being deployed in **containers**
  - A container is an **implementation** of these services **plus** a **definition** of the interfaces a component **MUST** provide to integrate it with the container.

---
#### 11.4.3 CBSE Processes
> Software processes that support component-based software engineering.
- Development **for** reuse: Process concerned with developing components or services that **will be reused** in other applications.
- Development **with** reuse: Process of developing **new** applications using **existing** components and services.

![](./pic/11_11.png)

**Supporting Processes**
- Component **acquisition** is the process of acquiring components for reuse or development into a reusable component.
  - involve accessing **locally-developed** components or services or finding these components from an **external** source.
- Component **management** is concerned with managing a company’s reusable components, ensuring that they are properly catalogued, stored and made available for reuse. 
- Component **certification** is the process of checking a component and certifying that it meets its specification.

---
### 11.5 SERVICE-ORIENTED ARCHITECTURES
> A way of building distributed applications using web services.
>> A web service is a loosely coupled, reusable software entity that encapsulates discrete functionality, which may be distribute and programmatically accessed.

- Service-oriented SE vs. Component-based SE
  - When building a **service-oriented** system, reference the external service; 
    - Each system that reused a component had to incorporate its own copy of that component.
  - **Components** are deployed in containers and rely on the containers' support to communicate with each other. 
    - Services communicate based on established protocols (e.g., HTTP, HTTPS) and data format (e.g., XML, Schemata)

---
**Benefits**
- Services can be offered by any service provider inside or outside of an organization. 
- The service provider makes information about the service public so that any authorized user can use the service. 
- **Applications can delay the binding of services until they are deployed or until execution.**
  - loosely coupled
  - can choose which service at run time;
  - flexible
- Opportunistic construction of new services is possible. 
- Service users can **pay for services** according to their use rather than their provision.  
- Applications can be made smaller, which is particularly important for mobile devices with limited processing and memory capabilities.

---
**Service-Oriented Architecture (SOA)**
> An architectural style that focuses on the **use of services to support business requirements.**
- **Service providers**
  - **design** and **implement** services and **specify the interface** to these services;
  - **publish** information about these **services** in an **accessible registry**. 
- **Service requestors(service clients)**
  - make use of a service **discover** the **specification** of that service and **locate the service provider**. 
  - **bind** their application to that **specific service** and **communicate** with it, using **standard service protocols**.

![](./pic/11_12.png)

---
**Service Engineering**
> The process of developing services for reuse in service-oriented applications
- **Service candidate identification**
  - **identify** possible **services** that might be implemented and **define** the service **requirements**. 
- **Service design**
  - design the **logical service interface** and its **implementation interfaces**. 
- **Service implementation and deployment**
  -  implement and **test** the **service** and make it **available** for use.

![](./pic/11_13.png)

---
***学习笔记，仅供参考***
