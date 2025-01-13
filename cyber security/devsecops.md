# DevSecOps

Developer Operations (DevOps) 

Following the infinite loop of the DevOps diagram, let's expand on some DevOps tools and processes that we'll look at as we follow the DevSecOps pathway and how they help an organization:

- **CI/CD** – Continuous Integration and Continuous Deployment deal with the frequent merging of code and adding testing in an automated manner to perform checks as new code is pushed and merged. This helps detect bugs early and decreases the effort of maintaining modular code, introducing reliable rollbacks of versions/code.
- **Infrastructure as Code (IaC)** – A way to manage and provision infrastructure through code and automation. This approach helps with consistent resource creation and management. Standard tools for IaC are Terraform, Vagrant, etc.
- **Configuration Management** – Manages the state of infrastructure constantly and applies changes efficiently, making it more maintainable. IaC can be used for configuration management.
- **Orchestration** – The automation of workflows helps achieve stability. For example, by automating the planning of resources, we can have fast responses whenever there is a problem (e.g., health checks failing).
- **Monitoring** – Focuses on collecting data about the performance and stability of services and infrastructure. This enables faster recovery, cross-team visibility, better root-cause analysis, and automated responses.
- **Microservices** – An architecture that breaks an application into many small services. This provides flexibility, reduced complexity, and more options for choosing technology across microservices.

## Shifting Left

In the past, security testing was implemented at the end of the development cycle. As the industry evolved, security teams performed various analyses and security testing in the final stages of the lifecycle. This development approach to shifting left in DevOps can be referred to as DevSecOps.

## What is the value?

DevSecOps helps reduce vulnerabilities, maximize test coverage, and intensify the automation of security frameworks. This reduces risk, assists organizations in preventing brand reputation damage and economic losses due to security flaws, and makes auditing and monitoring easier.

## Security Silos

It is common for many security teams to be left out of DevOps processes, portraying security as a separate entity. This creates a silo around security and prevents engineers from understanding the necessity of security or applying security measures from the beginning. Security should be a supportive function to help other teams scale and build security, sharing responsibilities across all team members instead of having a specialized security engineer.

## Lack of Visibility & Prioritization

Aim to create a culture where security is treated as a regular aspect of the application. Developers can then focus on development with confidence about security. Trust should be built between teams, and security should promote the autonomy of teams by establishing processes that instill security.

## Stringent Processes

Every new experiment or piece of software must not go through a complicated process and verification against security compliances before being used by developers. Procedures should be flexible to account for these scenarios. Developers need environments to test new software without common security limitations. These environments are known as "SandBox," which are temporarily isolated environments with no connection to any internal network and no customer data.

## What is Software Development Lifecycle (SDLC)?

The Software Development Lifecycle is a set of practices that make up a framework to standardize building software applications. SDLC defines the tasks to perform at each software development stage. This methodology aims to improve the quality of the software and the development process to exceed customer expectations and meet deadlines and cost estimates.

## How does SDLC work?

The Software Development Life Cycle provides the guidance required to create a software application by splitting tasks into phases. Standardizing the tasks within each phase increases the efficiency of the development process. Each phase divides into granular tasks that can be measured and tracked, introducing the capability of monitoring to ensure projects stay on track. The aim of SDLC is to establish repeatable processes and predictable outcomes from which future projects can benefit. SDLC phases are usually divided into 6-8 phases.

The seven phases of the Software Development Life Cycle are:

1. **Planning**: Encompasses all aspects of project and product management, including resource allocation, project scheduling, cost estimation, etc.
2. **Requirements Definition**: Determines what the application is supposed to do and its requirements.
3. **Design & Prototyping**: Establishes how the software application will work, including programming language, methods of communication, architecture, etc.
4. **Software Development**: Entails building the program, writing code, and documentation.
5. **Testing**: Ensures components work and can interact with each other, and that there are no performance lags.
6. **Deployment**: The application or project is made available to users.
7. **Operations & Maintenance**: Engineers respond to issues in the application or bugs and flaws reported by users and sometimes plan additional features for future releases.
