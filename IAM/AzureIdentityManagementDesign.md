## Designing For Azure Identity Management

1. Azure AD Domain Services
  - provides managed domain services
    - Domain join
    - Group policy
    - LDAP
    - Kerberos/NTLM authentication
  - fully compatible with traditional on-prem Active Directory
  - No need for deployment/management of domain controllers in the cloud
  - Integrates with the existing Azure AD tenant and makes it possible for users to login with their corporate credentials
  - Existing user accounts and groups can be leveraged to secure access to resources
  - Companies leveraging a hybrid IT infrastructure will typically synchronize its identity information from their on-prem directories to the Azure AD tenant
    - Password sync is mandatory for a hybrid organization to use Azure AD Domain Services
    - This is required because users' credentials are needed for authen tication via NTLM and Kerberos in the managed domain that is provided by Azure AD Domain Services
    - The managed domain is a stand-alone domain, __NOT__ and extension of the on-prem AD Domain

2. Hybrid Identities
  - authentication methods
    - Password Hash Synchronization (PHS)
      - accomplished with __Azure AD Connect__ by synchronizing a hash, of the hash, of a user's on-prem AD password to a cloud-based Azure AD instance
      - useful to signing in to Azure AD services like Office 365 with the same passwod as an on-prem AD account which reduces end-user impact
      - required an organization ton install Azure AD Connect
    - Pass-Through Authentication (PTA)
      - allows users to sign in to both on-prem and cloud-basded apps with the same password
      - validates user passwords directly against the on-prem Active Directory instead of using a synced password hash
      - a key benefit of PTA over PHS is that it affords organizations the ability to enforce their on-prem AD security and password policies
      - by combing PTA with e Seamless Single Sign-On feature, organizations can allow users to access applications on coporate machines inside the network, without the need to type in their passwords again
      - offers end users the ability to complete self-service password management tasks in the cloud
      - only needs a lightweight agent to be installed on-prem
      - improved security over PHS becasue on-prem passwords are never stored in the cloud
      - another benefit of PTA is that the agent only makes outbound connections from the network, removing all requirements fro a DMZ as part of the solution
      - communication is secured via cert-based authentication
    - Federation
      - a collection of domains with an established trust, which typically includes authentication and almost always includes authorization
      - might include multiple organizations that have established trust for shared access to as set of resources
      - ensures that all user authentication happens on-prem and it provides administrators with the ability to implement more rigorous levels of access control
      - to protect against a failure of the ADFS infrasture when using federation with ADFS, organizations can setup password hash synchronizationm or PHS as a backup

3. Azure Role-based Access Control
  - relies on role assignment for access control, each role assignment consists of three parts:
    - security principal
      - an obejct that represents either a user, a group a service principal or a managed identity that requires access to resources in Microsoft Azure
    - role definition
      - a collection of permission
      - four fundamental roles available
        - Owner
        - Contributor
        - Reader
        - User Access Administrator
    - scope
      - can be specified at the:
        - Management group level
        - Subscription level
        - Resource Group level
        - Specific resources
      - structured in parent-child relationship, access that is granted at the parent scope level will be inherited by the child scopes
      - free and is included with all Azure subscriptions

4. Single Sign-on
  - allows users to sign in once with one account in order to access domain-joined devices coporate resource SaaS apps and even web apps
  - cloud apps can use for single sign-on
    - SAML: most secure
    - Passowrd based
    - linked
    - disabled methods 
    - header based: require PingAccess

5. Multi Factor Authentication
  - available as:
    - Passwords
    - Security Questions
    - Email Address
    - App
    - OATH hardware token
    - SMS
    - Voice call
    - App passwords
  - offered in two flavors
    - Azure Multi Factor Authentication Service
    - Azure MFA Server
  - Supportability
    - Conditional Access Polivy: A way to temporarily bypass MFA for Azure MFA Server users
    - Can be minimized for users that are on the local network
      - can be accomplished with trusted IPs or named locations

6. Azure Active Directory Business-to-Busuness
  - allows an organization to securely share company applications and company services with guest uers from other organizations, while retaining control over company data
  - allow app and group owners to manage their own guest users

7. Azure Active Directory Business-to-Customer
  - offers organizations the ability to customize and control how customers interact with corporate applications
  - completes identity takss by interacting, in sequence with identity providers, users, other systems and with the local directory
  - the Identity Experience Framenwork establishes multi-party trust and completes these steps
  - Along with a Trust Framework policy, this framework defines the actors, actions, protocol and sequence of steps that needs to be complete to make things work
  - makes use of SYN cookies and rate and connection limits
    - SYN cookie is a technique used to resist IP address spoofing attacks.

8. Self-service password reset (SSPR)
  - without the need for a call to the helpdesk

9. Managed Identities for Azure Resources
  - System-Assigned Managed Identity: Enabled directly on an Azure service instance
  - User-Assigned Managed Identity: Created as a standaline Azure resource