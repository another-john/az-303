## Azure Resource Manager Intro
1. Recommended ways to interact with ARM when deploying large or repeated deployments
  - Azure Powershell
  - Azure CLI 
2. ARM Templates
  - Templates are idempotent, which means that changes are pplied only once.
  - Repeatability, each time we apply the template we get the same result.
  - The template is submitted as one object and Azure Resource Manager works out the order that resources hsould be created in
    - so dependency management and orchestration of deployment operations are carried out correctly
  - JSON format allows for nested and hierachical resources
  - you can divide up a deployment into multiple linked files
  - default mode: incremental
  - Five sections
    - Parameters
      - A parameter has a name and a type
    - Functions
      - in addition to the ARM template built-in functions
      - no facility for iterations or for-loops
    - Variables
      - key-value pairs
      - more like constants
    - Resources
      - name
      - type
      - tags
      - dependencies
    - Outputs
      - displaying information or
      - daisy-chaining templates
