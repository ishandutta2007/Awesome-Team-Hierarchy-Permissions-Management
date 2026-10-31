# Awesome-Team-Hierarchy-Permissions-Management

## Top Team Hierarchy & Permissions Management Ecosystem



**Curated List of SaaS Products & Open-Source GitHub Projects**  

*Focused on Organizational Hierarchy, Role-Based Access & Self-Hosted Identity Governance*  

**Last updated: October 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **Team Hierarchy & Permissions Management**. These tools enable organizations to model reporting structures, assign roles, enforce least privilege, and automate access reviews—ensuring the right people have the right access to the right resources as teams grow and reorganize.



**Examples** include HubSpot Team Management, Okta, Microsoft Entra ID, OneLogin, JumpCloud, Rippling, BambooHR, Ping Identity, Workday, and Lumos (the category leaders).



**Open-source emphasis**: Team Hierarchy & Permissions Management is a domain where open-source tooling is **surprisingly capable but requires assembly across distinct layers**. **Keycloak 26.6+** now offers **Organization Groups**—isolated hierarchical group structures within each organization, solving the multi-tenant naming collision problem that plagued realm-level groups . **ZITADEL** provides native B2B organizations with unlimited multi-tenancy and full audit trails as immutable event streams . **midPoint** is the closest open-source equivalent to enterprise IGA, with practitioners confirming it handles provisioning, access reviews, and role management in production—though documentation is not beginner-friendly and requires identity engineering experience . For HR hierarchy foundations, **Frappe HR** provides the employee lifecycle, reporting lines, and organizational structure that feeds access decisions . The critical gap: **no open-source project provides the turnkey access request workflow** of Lumos—where an employee requests Slack access and the platform automatically provisions it with manager approval .



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents

- [SaaS/Hosted Platforms](#saas-products)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **[HubSpot Team Management](https://www.hubspot.com/)**  

  Native team and user management within HubSpot; assign roles (Super Admin, Marketing, Sales, Service) and permissions per user, with SSO support on higher tiers. Focused on HubSpot-internal access rather than cross-application provisioning.



- **[Okta](https://www.okta.com/)**  

  Leading identity cloud with Universal Directory, SSO, MFA, Lifecycle Management (automated provisioning/deprovisioning via SCIM and HR-driven workflows), and Identity Governance for access certifications. The benchmark for turnkey user provisioning across thousands of app integrations.



- **[Microsoft Entra ID](https://www.microsoft.com/en-us/security/business/microsoft-entra)**  

  Microsoft's cloud identity service with Lifecycle Workflows (joiner/mover/leaver triggered by HR events), entitlement management, access reviews, and provisioning to SaaS apps via SCIM. Deep integration with Microsoft 365 and Azure.



- **[OneLogin](https://www.onelogin.com/)**  

  Identity and access management platform (now part of One Identity) with SSO, MFA, and automated user provisioning workflows.



- **[JumpCloud](https://jumpcloud.com/)**  

  Cloud directory platform with Directory-as-a-Service lifecycle management, SSO, device management, and LDAP; automates user onboarding/offboarding across connected systems.



- **[Rippling](https://www.rippling.com/)**  

  Unified HR/IT platform with Identity and Access Management built on a single Employee Graph; automates onboarding/offboarding and enforces role-based access across 650+ integrations.



- **[BambooHR](https://www.bamboohr.com/)**  

  HRIS for small to mid-sized businesses with employee records, reporting structures, and time-off tracking; the HR data source that feeds downstream provisioning workflows.



- **[Ping Identity](https://www.pingidentity.com/)**  

  Identity platform (merged with ForgeRock) with AI-driven IGA, lifecycle management, and fraud/risk protection; PingOne for Workforce includes provisioning and governance capabilities.



- **[Workday](https://www.workday.com/)**  

  Enterprise HCM and financial management platform with organizational hierarchies, supervisory orgs, and role assignments; the authoritative source for workforce structure in large enterprises.



- **[Lumos](https://www.lumos.com/)**  

  Identity governance platform focused on **app access requests, approvals, and automated provisioning**; positioned for mid-market companies wanting Okta-like governance without full IGA complexity.



## Open-Source GitHub Projects



### Hierarchical Organization & Multi-Tenancy



- **[Keycloak (Organization Groups)](https://www.keycloak.org/2026/04/org-groups)**  

  Keycloak 26.6.0 introduced **Organization Groups**—hierarchical group management within each organization, enabling isolated team/department structures that don't collide across tenants . Features: nested groups mirroring real org charts (`/Engineering/Frontend`, `/Sales/EMEA`), automatic group assignment via Identity Provider mappers (hardcoded or claim-based, e.g., `department=backend` → `/Engineering/Backend`), and group memberships embedded in OIDC tokens and SAML assertions . **The strongest open-source foundation for B2B multi-tenant hierarchy**—but group memberships cannot be used in Keycloak authorization policies (realm groups are still needed for that) .



- **[ZITADEL](https://github.com/zitadel/zitadel)**  

  Open-source IAM platform (Apache-2.0) with **native B2B organizations and unlimited multi-tenancy**; the hierarchy is strictly modeled as Instance → Organization → Project, with data isolation at every level . Features: **full audit trail as immutable event streams** (every change is an event, accessible via API or streamed to external systems via webhooks), SSO, MFA, Passkeys (FIDO2), OIDC, SAML, SCIM, and API-first design (gRPC + REST) . Docker Compose deployment in under 3 minutes. **Best for teams building B2B platforms or SaaS products** needing per-tenant isolation with auditable hierarchy changes.



- **[Casdoor](https://github.com/casdoor/casdoor)**  

  UI-first open-source IAM/SSO platform (Apache-2.0) with OAuth 2.0, OIDC, SAML, CAS, LDAP, and RBAC; includes SCIM 2.0 server, built-in LDAP server, and MCP server for AI agent access . Supports 70+ identity providers and syncers for Keycloak, Okta, Entra ID, and Active Directory. **Developer-friendly** for smaller teams wanting a clean admin UI with multi-tenant support.



### Identity Governance & Access Reviews



- **[midPoint (Evolveum)](https://github.com/Evolveum/midpoint)**  

  The closest open-source equivalent to enterprise **IGA** (Apache-2.0); practitioners describe it as genuinely capable for **full provisioning, access reviews, role management, and connector library** covering AD/LDAP, Microsoft Graph, Exchange, and more . One practitioner at REWE Group was "reasonably happy with it in production"; another got HR data in and created AD accounts with group assignments within days of starting evaluation . **Honest constraints**: documentation is not beginner-friendly, requires identity engineering experience, community activity could be more active, and self-hosting means owning infrastructure and upgrades . **Best for organizations with in-house technical capability** who cannot support commercial licensing or want to avoid US vendor dependency .



- **[COmanage](https://github.com/COmanage/registry)**  

  Open-source **person registry** (Apache 2.0) designed for Virtual Organizations; supports **hierarchical/delegated administration** via COUs (Collaborative Organizational Units) similar to LDAP OUs . Administrators can add roles and manage attributes for participants within their COU, with roles driving group memberships that control service access. Features: enrollment flows (invitation, self-signup, admin-driven), expiration policies with grace periods, **transaction history and point-in-time audit capabilities**, and plugin-based provisioning (LDAP out of the box) . **Best for research collaborations and federated identity scenarios**—not a general enterprise IGA.



### HR Hierarchy Foundations



- **[Frappe HR](https://github.com/frappe/hrms)**  

  Open-source HR and Payroll software (complete HRMS with 13+ modules) that provides the **employee lifecycle, reporting lines, and organizational structure** that feed downstream access decisions . Features: Employee Management (onboarding, promotions, transfers, exit interviews), Leave and Attendance, Expense Claims with multi-level approval workflows, Performance Management with goals/KRAs, and Payroll/Taxation . Built on Frappe Framework (Python/JavaScript) with REST API. **Best for organizations wanting an integrated HR foundation** that can feed hierarchy data into an IAM/IGA layer.



### Additional Strong Open-Source Options



- **LARA (Lightweight Access Review Application)** — Open-source IGA solution for **access certification campaigns** directly against existing LDAP directories (Active Directory, eDirectory, OpenLDAP) with no data migration . Supports LDAP Group Memberships and NetIQ Identity Manager RBAC models, plus SCIM and CSV entitlement models . **Demo limited to 60 users**; production requires a license key . Best for organizations needing auditor-required access reviews without a full IGA suite.

- **@torquedev/bundle-iam** — MIT-licensed IAM bundle (npm) with authentication, **RBAC, teams with per-team roles**, and admin dashboard; designed as a drop-in module for Node.js applications . **Developer-focused**—for building custom apps, not enterprise identity governance.



**Frameworks for building custom systems**: For **multi-tenant hierarchy in an IAM platform**, Keycloak Organization Groups or ZITADEL . For **full IGA with provisioning and access reviews**, midPoint (accepting the engineering investment) . For **HR hierarchy data foundation**, Frappe HR . For **audit-required access certification**, LARA against existing LDAP . No open-source project provides the **turnkey access request + auto-provisioning workflow** of Lumos—that requires assembling an IGA layer (midPoint) with a request portal and provisioning connectors.



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- Team hierarchy and permissions platforms handling identity data must comply with applicable privacy regulations (GDPR, CCPA) and security frameworks (SOC 2, ISO 27001); **improper role assignments or missed access reviews create audit findings and breach risk**.

- **Open-source hierarchy and permissions management is capable but requires assembly**—Keycloak Organization Groups and ZITADEL handle multi-tenant hierarchy , midPoint handles IGA , and Frappe HR handles HR data . However, **no open-source project provides the turnkey access request and auto-provisioning workflow** of Lumos or the managed compliance experience of Okta. Organizations requiring full lifecycle automation with vendor support should evaluate commercial platforms or invest in custom integration.

- Verify license terms for commercial use; Keycloak uses Apache-2.0, ZITADEL uses Apache-2.0 , midPoint uses Apache-2.0 , and Frappe HR uses GPL-3.0 .



---



**Made for identity architects, IT administrators, security engineers, and HR operations teams.**  

Let's make team hierarchy and permissions management more open, but with clear eyes about the IGA engineering investment and access request workflow gaps that remain.
