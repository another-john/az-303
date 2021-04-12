## Managing Azure Subscriptions and Resource Groups
1. Role-Based Access Roles
  - Contributor
    - Full access to manage all Azure resources
    - Cannot assign roles to other users
  - Owner
    - Full access to manage all Azure resources
    - Also allows to assign roles to other users
  - Reader
    - View resources but not allowed to make any changes
  - User Access Administrator
    - Allowed to manage user access to Azure resource s
    - No access to the actual resources
2. You can also create custom roles if required
3. Azure Security Center creates a default security policy automatically for each Azure subscription
  - Security Center policies can be extended by using Azure Policy
  - Azure Policy is a service in Azure that you use to create assign and manage policies

4. Resource Group
  - a logic container to group a collection of Azure resources into logical groups for easy provisioning, monitoring and access control
  - Resources contained within a resource group can span multiple reigons
  - The requirement of a resource group being deployed to a specific region comes from the need to store the deployment metadata and definitions associated with the resource group in a specific location
5. Resource Policies
  - Azure Policy evaluates deployed respirces and scams for tjpse mpt compliant with the policies that ahave defined
6. Resource Locks
  - CanNotDelete
  - ReadOnly
  - When a lock is applied at a parent scoe all resources within that scope inherit the lock
  - Resources added later will also inherit the lock from the parent
  - To create or delete management locks, you must have access to these actions:
     - Microsoft.Authorization/*
     - Microsoft.Authorization/locks/*actions
  - Only the built-in __Owner__ and __User Access Administrator__ roles are granted these actions

7. Tagging
  - Applying tags to Azure resources provides metadata that's used to logically organize those resources intoa taxonomy
  - number limitations like 15 tag name/value pairs for each resource or resource group
  - Tags that are applied to a resource group are not inherited by the resources within the resource
  - Tags cant be applied to the classic resources such as Cloud Services
  - Tags can't contain special characters
  - Requires __write__ access to that resource type
  - Use the __Contributor__ role to enable the ability to apply tags to all resource types
    - e.g. to apply tags to virtual machiens, use the __Virtual Machine Contributor__
8. Moving Reources Across Resources
  - When moving, source group and the target group are locked duing the operation
  - Thus resource cant be added, updated or deleted in the locked resource groups while the move is in progress
  - Location of resource cannot be changed
  - Preparation Steps
    - The source and destination subscriptions must exist within the same Azure Active Directory tenant
    - The destination subscription must be registered for the resource provider of the resource being moved
    - The account moving the resources must have the permissions
    - Before moving resources, ensure the subscription quotas for the subscription you are moving the resource to will support the resources you plan to move
    - It's best to break large moves into separate smaller move operations
    - Resource Manager will immediately fail if there is an attemp to move __more than 800__ resources in a single move