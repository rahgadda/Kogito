# Decision Model and Notation - DMN

## Overview
- Decision Model and Notation (DMN) is used to model decision service graphically.
- It is a standard established by the **Object Management Group (OMG)** for describing and modeling operational decisions.
- DMN decision model are determined by below
  - **DRD:** 
    - A decision requirements diagrams trace business decisions from start to finish.
    - Each decision node use logic defined in DMN boxed expressions such as decision tables.
    - A DRD can represent part or all of the DMN model.
    - DRD components and connector details are available [here](https://docs.jboss.org/kogito/release/latest/html_single/#_using_dmn_models_in_kogito_services)
  - **DRG:**
    - A Decision Requirements Graph models a domain of decision-making, showing the most important elements involved in it and the dependencies between them.
    - The elements modeled are **decisions**, **input data**, and **knowledge sources**. 
    - The visual representation of a DRG is called DRD.
- Kogito provides design and runtime support for **DMN 1.2** models at **conformance level 3**.
- It provides runtime-only support for DMN 1.1 and 1.3 models at conformance level 3. 
- DMN 1.1 and 1.3 models are currently not supported in the Kogito DMN modeler.

## FEEL
- Friendly Enough Expression Language (FEEL) is an expression language defined by the Object Management Group (OMG) DMN specification.
- FEEL is designed to facilitate both decision modeling and execution by assigning semantics to the decision model constructs.

## Appendix
- References
  - [OMG DMN](https://www.omg.org/spec/DMN)