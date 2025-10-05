# ERP Smart Home / BMS Scope Document

## 1. Project Creation (Pre-Cycle Rule)
- Only the Director can create a new project.
- Each project must have a unique Project ID (auto-generated or customizable).
- Mandatory data: name, type, address, owner, stakeholders (architect/electrician).
- Each project is assigned to only one Project Manager (one-to-one).
- Project Managers see only their own assigned projects and notifications relevant to them.
- Stage 1 (Design) cannot start unless the project is created and assigned.

## 2. Project Lifecycle (8 Stages)
- **Stage 0:** Confirmation from Sales Department.
- **Stage 1:** Design → Upload DWG and approvals (PM/Director/Architect).
- **Stage 2:** Pipes & Boxes → Site visit report and approval.
- **Stage 3:** Cable Pulling → Inspection and approval.
- **Stage 4:** Ordering Items → Create PR/PO and Finance approval.
- **Stage 5:** Installation → Field verification and Channel Map.
- **Stage 6:** Programming → Execute client scenarios.
- **Stage 7:** Testing & Training → Client training and acceptance.
- **Stage 8:** Handover → Generate PDF report and officially close the project.

## 3. Project Management Module
- Director Dashboard: all projects.
- Project Manager Dashboard: only assigned projects.
- Manage project stages, approvals, and attachments.
- Attachments: invoices, DWG files, reports.
- 48-hour notifications and automatic generation of PR/PO at Stage 4.

## 4. Engineering Documentation
- Store files by project and stage.
- Version control and serial numbers for documents.
- Mandatory upload of visit reports before stage approval.
- Audit log and daily backups for safety.

## 5. Financial Tracking
- Initial budget entry and revisions.
- PR → PO → Invoice → Payment flow.
- Stage completion blocked until Finance approval is obtained (where required).
- Automatic calculation of actual budget at project handover.

## 6. Human Resources (HR)
- Staff profiles: name, role, hourly rate.
- Availability calendar and conflict prevention.
- Attendance records: actual hours, travel, accommodation.
- Automatic integration with Finance for cost tracking.

## 7. Management Reporting
- Delay Notification Report.
- Material Request Report (orders/returns).
- Handover Report (final client delivery).
- Project Status Report (live progress overview).
- General Management Report (company-wide insights).

## 8. User and Role Management
- Only Director/Admin can add or edit users.
- Roles: Admin, PM, Designer, Programmer, Finance, Staff.
- Permissions limited: PM sees only their own projects.
- Audit log of all changes for accountability.

## 9. Company Information
- Store company profile: name, address, logo, phone, email, website.
- Auto-injected into all generated reports.

## 10. Automation and Notification Rules
- 48-hour reminder before any scheduled visit.
- No stage can be marked complete without required visit report and financial approval.
- At project handover:
  - Set `actual_closing_date` to today.
  - Calculate `actual_budget` as invoices + labor + travel/accommodation.
  - Auto-generate and archive handover report.

## 11. Core Database Tables
- `projects`: `id`, `name`, `type`, `owner`, `pm_id`, `budget`, `dates`.
- `project_stages`: `stage_no`, `status`, `report_id`, `approval`.
- `documents`: `version`, `serial`, `uploader`, `path`.
- `finance`: PR, PO, Invoices, Payments.
- `hr_staff`, `hr_assignments`, `hr_costs`.
- `delays`, `delay_reasons`.
- `users`: `id`, `name`, `role`, `dept`, `status`.
- `company_info`: `name`, `logo`, `contact`.
