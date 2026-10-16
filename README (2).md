# AcxiomCRM

AcxiomCRM is a browser-based Customer Relationship Management (CRM) prototype for managing customers, leads, sales opportunities, follow-ups, activities, reports, and audit events. It demonstrates common CRM workflows and role-based views in a single HTML file.

> **Project status:** The attached implementation is a standalone HTML/CSS/JavaScript prototype. Its records are stored in in-memory JavaScript objects, and its API Console simulates REST API responses in the browser. It is not yet the ASP.NET Core MVC + Entity Framework Core + SQL Server application described in the planned project specification.

## Features in the Current Prototype

- **Role-based demo login:** Admin, Manager, and Sales Executive views.
- **Dashboard:** Summary cards for customers, leads, opportunities, and pipeline value, plus Chart.js charts for lead status, opportunity pipeline, and monthly won sales.
- **Customers:** Create, edit, delete, search, sort, paginate, and export records as CSV.
- **Leads:** Manage lead details and status transitions; qualified leads can be converted into a customer and an opportunity.
- **Opportunities:** Track amount, probability, expected close date, stage, customer, and owner.
- **Follow-ups:** Schedule follow-ups, mark them complete, and identify overdue planned follow-ups.
- **Activities:** Record calls, meetings, emails, and tasks.
- **Reports:** Customer, lead, follow-up, opportunity, pipeline, conversion, user activity, and audit reports, with filtering and CSV export.
- **User and role demo:** Change demo roles, activate/deactivate accounts, and clear demo lockouts.
- **Audit log:** Records selected demo events such as login attempts, record changes, conversions, and role changes.
- **API Console:** Try simulated requests for customers, leads, opportunities, follow-ups, and the pipeline report.
- **Responsive interface:** Sidebar navigation, tables, forms, and light/dark theme support.
- **Basic form validation:** Email, phone, required fields, amount, probability, dates, duplicate customers, and lead status transitions.

## Technology Used

- HTML5
- CSS3
- JavaScript (client-side)
- [Chart.js 4.4.1](https://www.chartjs.org/) for dashboard charts, loaded from a CDN

The current HTML file does **not** use ASP.NET Core MVC, Entity Framework Core, ASP.NET Core Identity, or SQL Server.

## Getting Started

### Requirements

- A modern web browser
- An internet connection for Chart.js to load from its CDN

### Run locally

1. Save the supplied file as `AcxiomCRM.html`.
2. Open the file in a modern browser.
3. Use one of the demo accounts listed below.

No build step or database installation is required to run this prototype.

## Demo Accounts

| Role | Email | Password |
|---|---|---|
| Admin | `admin@acxiom.com` | `Admin@123` |
| Manager | `manager@acxiom.com` | `Manager@123` |
| Sales Executive | `sales@acxiom.com` | `Sales@123` |
| Sales Executive | `sales2@acxiom.com` | `Sales@123` |

The prototype locks an account for **1 minute** after five failed login attempts. These credentials are for demonstration only and must not be reused in a production system.

## How to Try the Main Workflows

1. Sign in with one of the demo accounts.
2. Open **Customers** to create or edit a customer.
3. Open **Leads** and move a lead through its allowed statuses.
4. Open a **Qualified** lead and select **Convert**. The prototype creates a customer and an opportunity, provided the customer email and phone are not duplicates.
5. Create an opportunity and try invalid amounts, probabilities, or close dates to see validation messages.
6. Schedule a follow-up and mark it complete.
7. Open **Reports** and export a report as CSV.
8. Open **API Console** and use the preset requests to inspect simulated HTTP status codes and JSON responses.
9. Sign in under different demo roles to compare the navigation and record visibility.

## Important Limitations

This file is a demonstration prototype, not a production-ready CRM.

- **In-memory data:** Changes are lost when the page is reloaded.
- **Demo-only authentication:** User passwords are present in client-side JavaScript and are not securely hashed. The browser-only login must not be treated as real authentication.
- **Simulated API:** The API Console calls local JavaScript functions; it does not send HTTP requests to a backend.
- **Client-side access rules:** Role and record restrictions are implemented in browser code and can be bypassed. They do not provide server-side authorization.
- **Audit log:** Audit entries exist only in memory, and the displayed IP address is a fixed demo value.
- **No database persistence:** There is no SQL Server database or Entity Framework Core integration in this file.
- **Not all security controls are production-grade:** Browser validation can be bypassed; the prototype does not provide ASP.NET antiforgery protection, secure server-side sessions, or server-side password lockout.
- **Prototype reporting:** The charts and reports use the sample/in-memory records included in the file.

Do not use real customer information, real credentials, or this prototype as a deployed business system.

## Planned ASP.NET Core MVC Implementation

The intended full application can be developed in phases:

- ASP.NET Core MVC controllers, Razor views, and ViewModels
- Entity Framework Core with SQL Server and database migrations
- ASP.NET Core Identity with hashed passwords, password policy, lockout, and role management
- Persistent Customer, Lead, Opportunity, FollowUp, Activity, and AuditLog entities
- Server-side validation and business rules
- Server-enforced role authorization and record-level access checks
- Persistent audit logging
- Real REST API controllers using DTOs and appropriate HTTP status codes
- Search, filtering, sorting, pagination, and reports backed by the database
- Automated tests and a security review

These items are **planned work** unless implemented separately in the ASP.NET Core project.

## Suggested Repository Structure for the Planned Application

```text
AcxiomCRM/
├── Controllers/
├── Data/
│   └── ApplicationDbContext.cs
├── Models/
├── Services/
├── ViewModels/
├── Views/
├── wwwroot/
├── Migrations/
├── appsettings.json
├── Program.cs
└── README.md
```

This is a suggested structure for the ASP.NET Core application, not a description of the single-file HTML prototype.

## License

No license is specified in the supplied project file. Add a license before distributing or reusing the project if required.
