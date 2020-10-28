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
![](./01-Images/01-Architecture.png)
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
    - [Prometheus](https://prometheus.io/)
    - [Grafana](https://grafana.com/)
    - [All Kiegroup Service](https://quay.io/organization/kiegroup)
    - [Kogito Management Console](https://quay.io/repository/kiegroup/kogito-management-console): It is a user interface for viewing the state of all available Kogito services and managing process instances.
    - [Kogito Data Index](https://quay.io/repository/kiegroup/kogito-data-index): 
      - It consumes the Kafka cloud events and index this information into the storage service. 
      - It is a Quarkus application based on VertX and reactive messaging that exposes a GraphQL endpoint.
    - [Kogito Jobs Service](https://quay.io/repository/kiegroup/kogito-jobs-service)
      - It is responsible for scheduling jobs that aim to be fired at a given time. 
      - The service does not execute the job itself, it triggers a callback that could be an HTTP request on a given endpoint specified on the job request, or any other callback that could be supported by the service.
      - It is a Quarkus application based on VertX.
    - [Kogito Trusty Service](https://quay.io/repository/kiegroup/kogito-trusty)
      - It stores all Kogito tracing events related to decisions made in Kogito services. 
      - It uses the Kafka cloud events from Kogito services, and then processes the tracing events and stores the data in the storage service.
    - [Kogito Trusty UI](https://quay.io/repository/kiegroup/kogito-trusty-ui)    
    - [Kogito Explainability Service](https://quay.io/repository/kiegroup/kogito-explainability)
      - It is a complementary service for the Trusty Service to identify why the decision were made.
    - [Kogito Task Console](https://quay.io/repository/kiegroup/kogito-task-console)
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
Below are details of building blocks of Kogito
- [Modelers](./03-Modules/01-modeler.md)
- [DMN](./03-Modules/02-dmn.md)
- [BPMN]()

---

## Appendix
- References
  - [Kogito Documentation](https://docs.jboss.org/kogito/release/latest/html_single/#con-kogito-automation_kogito-docs)
  - [Kogito Examples](https://github.com/kiegroup/kogito-examples)
  - [DMN 1.2 OMG Specification](https://www.omg.org/spec/DMN/1.2/PDF)