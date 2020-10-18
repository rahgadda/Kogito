# Kogito

## Table of Content

- [Overview](#overview)
- [Architecture](#architecture)
- [Installation](#installation)
- [Modules](#modules)
- [Appendix](#appendix)

## Overview

- Kogito is a cloud-native business automation technology for building cloud-ready business applications by **Redhat**.
- Kogito derives from the Latin "Cogito", as in "Cogito, ergo sum" ("I think, therefore I am").
- The letter `K` has reference to Kubernetes, the base for OpenShift as the target cloud platform for Kogito, and to the Knowledge Is Everything (KIE) open source business automation project from which Kogito originates.
- Kogito adapts to your business domain instead of forcing you to modify your domain to work with Kogito.
- The core objective of Kogito is to help you mold a set of Business Process Model and Notation (BPMN), decisions(DMN), Drools Rule Language (DRL) or XLS spreadsheet decision tables into your own domain-specific cloud-native set of services.
- Kogito includes components that are based on well-known business automation KIE projects, specifically **Drools**, **jBPM**, and **OptaPlanner**, to offer dependable, open source solutions for business rules, business processes, and constraint solving.

---

## Architecture

- Kogito is designed to run and scale on a cloud infrastructure.
- We can use Kogito with the latest cloud-based technologies, such as Quarkus, Knative, and Apache Kafka.
![](01-Images\01-Architecture.png)
- The primary Java frameworks that Kogito supports are **Quarkus (recommended)** and **Spring Boot**. 

---

## Installation

- Dev Environment
  - Prerequisites:
    - [GraalVM 20 with jdk v11](https://github.com/graalvm/graalvm-ce-builds/releases/tag/vm-20.2.0)
    - [Quarkus VSCode extension](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-quarkus)
    - [Kogito Bundle VSCode extension](https://marketplace.visualstudio.com/items?itemName=kie-group.vscode-extension-kogito-bundle)
    - [Maven 3.6.2 or later](https://maven.apache.org/download.cgi)
  - For Persistence and Messaging:
    - [Infinispan](https://infinispan.org/)
    - [Strimzi](https://strimzi.io/)
    - [Keycloak](https://www.keycloak.org/)
    - Kogito Data Index
    - Kogito Jobs Service
    - Kogito Trusty Service
    - Kogito Explainability Service
    - Kogito Management Console
    - Prometheus
  - Create Quarkus [project](./02-MyDev/01-Person/person) using vscode plugin with below dependencies
    - quarkus-smallrye-openapi
    - kogito-quarkus
    - kogito-scenario-simulation [scope = test]
  - Delete below files from the template - Optional Step
    - Rest Resource file
    - Test Files
    - index.html from resources.
  - Create Person & KogitoScenarioJunitActivatorTest Java file, DMN, BPMN, and Scesim.
  - Commands
    ```sh
    mvn clean test
    mvn clean compile quarkus:dev
    mvn clean package
    mvn clean package -Dnative
    mvn clean package -Pnative
    mvn compile kogito:scaffold
    java -jar target/sample-kogito-1.0-SNAPSHOT-runner.jar
    ./target/sample-kogito-1.0-SNAPSHOT-runner
    ```
- Production
  - To deploy services we can use **Kogito Operator**. This is based on the **Operator SDK** and automates many of the deployment steps.
  - Kogito also offers a command-line interface (CLI) to simplify some of these deployment tasks.

---

## Modules
- [Modelers](./03-Modules/01-modeler.md)
- BPMN
- DMN

---

## Appendix
- References
  - [Kogito Documentation](https://docs.jboss.org/kogito/release/latest/html_single/#con-kogito-automation_kogito-docs)
  - [Kogito Examples](https://github.com/kiegroup/kogito-examples)