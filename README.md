# Auto Ticket Classification using Flow Designer

## 📌 Project Overview

**Auto Ticket Classification using Flow Designer** is a ServiceNow-based automation project that automatically classifies newly created IT support tickets according to the issue described by the user.

The system uses **ServiceNow Flow Designer** with keyword-based conditions to identify common IT issues and automatically assign the appropriate **Category** and **Subcategory**.

This project was developed as part of the **ServiceNow Administrator Project** under the Naan Mudalvan training program.

---

## 👥 Project Team

**Project done by:**

- **Logajit S**
- **Manellore Kusuma Keerthi**

---

## 🎯 Objective

The main objective of this project is to reduce manual ticket classification and make IT support ticket processing more structured and consistent.

When a new ticket is created, the system:

1. Detects the newly created record.
2. Reads the ticket's Short Description.
3. Checks the description against predefined keywords.
4. Automatically determines the appropriate Category.
5. Automatically determines the corresponding Subcategory.
6. Sends a confirmation email to the caller.

---

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| ServiceNow | Application and IT service management platform |
| Flow Designer | Workflow automation and ticket classification |
| ServiceNow Custom Table | Stores IT workflow tickets |
| ServiceNow Email | Sends ticket confirmation notifications |
| Update Sets | Packages configuration for deployment |
| GitHub | Project documentation and submission |

---

## 🗃️ Custom Table

The project uses a custom ServiceNow table:

**Incident Workflow**

Table name:

```text
u_incident_workflow
```

### Main Fields

- Number
- Caller
- Category
- Subcategory
- Short Description
- Description
- State
- Assigned Group
- Assigned To

The table also uses ServiceNow auto-numbering for ticket identification.

---

## ⚙️ Classification Logic

The Flow Designer checks the **Short Description** of a newly created ticket.

| Issue detected | Category | Subcategory |
|---|---|---|
| Wi-Fi / Network | Network | Wi-Fi |
| Projector | Hardware | Projector |
| Forgot Password | Access | Forgot Password |
| Slow Computer | Performance | Slow Computer |

### Example

If a user creates a ticket with:

```text
Wi-Fi not working in library
```

the flow automatically updates it to:

```text
Category    → Network
Subcategory → Wi-Fi
```

---

## 🔄 Flow Designer

The main automation is named:

```text
Auto Classify School IT Tickets
```

The workflow operates as follows:

```text
Record Created
      ↓
Check Short Description
      ↓
┌───────────────────────────────┐
│ Wi-Fi / Network               │ → Network / Wi-Fi
├───────────────────────────────┤
│ Projector                     │ → Hardware / Projector
├───────────────────────────────┤
│ Forgot Password               │ → Access / Forgot Password
├───────────────────────────────┤
│ Slow Computer                 │ → Performance / Slow Computer
└───────────────────────────────┘
      ↓
Update Incident Workflow Record
      ↓
Send Email to Caller
```

---

## 📧 Email Notification

After classification, the flow sends a confirmation email to the caller.

### Subject

```text
Your Request for the issue has been submitted.
```

The email informs the user that their IT support request has been successfully submitted and automatically classified.

---

## 🧪 Testing

The project was tested using actual ServiceNow records and Flow Designer execution history.

### Tested functionality

- Record creation trigger
- Real-time ticket classification
- Wi-Fi / Network classification
- Projector / Hardware classification
- Password / Access classification
- Slow Computer / Performance classification
- Category and Subcategory dependency
- Email notification
- Flow execution

A real-time Wi-Fi classification test successfully produced:

```text
Category    → Network
Subcategory → Wi-Fi
```

The Flow Designer execution history was inspected to verify that the correct branch and update actions were executed.

---

## 🐛 Development & Debugging

During development, the initial saved-trigger configuration caused a newly created record to remain unclassified.

The issue was investigated through Flow Designer execution history.

The final implementation replaced the problematic saved trigger with a standard:

```text
Record Created
```

trigger.

After replacing the trigger, the dependent Flow Designer actions and branch conditions were reconnected to the new trigger's data pills.

The flow was then tested again using a real ServiceNow record, and real-time classification worked successfully.

---

## 📦 Update Set

The completed ServiceNow configuration has been exported as an Update Set XML file.

Location:

```text
Update-Set/
```

The Update Set provides the ServiceNow configuration package used for deployment.

---

## 📁 Repository Structure

```text
Auto-Ticket-Classification-Flow-Designer/
│
├── README.md
│
├── Documentation/
│   └── Final Project Documentation
│
├── Phasewise-Templates/
│   ├── 1. Ideation Phase/
│   ├── 2. Requirement Analysis/
│   ├── 3. Project Design Phase/
│   ├── 4. Project Planning Phase/
│   ├── 5. Project Development Phase/
│   └── 6. Project Documentation/
│
├── Screenshots/
│   ├── 01-Update-Set/
│   ├── 02-Custom-Table/
│   ├── 03-Fields-and-Choices/
│   ├── 04-Flow-Designer/
│   ├── 05-Flow-Execution/
│   ├── 06-Email/
│   └── 07-Testing/
│
└── Update-Set/
    └── ServiceNow Update Set XML
```

---

## ✅ Project Status

**Status: Completed**

- [x] ServiceNow Update Set
- [x] Custom Incident Workflow table
- [x] Required fields
- [x] Category choices
- [x] Subcategory choices
- [x] Category/Subcategory dependency
- [x] Flow Designer automation
- [x] Ticket classification
- [x] Email notification
- [x] Real-time testing
- [x] Flow execution verification
- [x] Update Set XML export
- [x] Project documentation
- [x] Phasewise templates
- [x] GitHub repository

---

## ⚠️ Current Limitations

The current implementation uses rule-based keyword matching.

Therefore:

- Classification depends on configured keywords.
- Unrecognized or ambiguous descriptions may not be classified.
- The system currently supports the predefined issue categories.
- Performance testing was performed at individual-record level rather than production-scale load testing.

---

## 🚀 Future Scope

The project can be extended with:

- A configurable keyword/rules table.
- Automatic assignment to support groups.
- More IT issue categories.
- More advanced notification templates.
- Multilingual keyword recognition.
- NLP or machine-learning-based ticket classification using historical ticket data.
- Reporting and analytics dashboards.
- Integration with additional ServiceNow ITSM workflows.

---

## 📚 Project Documentation

This repository contains:

- Complete project documentation
- Phasewise project templates
- ServiceNow implementation screenshots
- Flow execution evidence
- Testing evidence
- Update Set XML

Together, these resources provide the implementation details and supporting evidence for the project.

---

## 👨‍💻 Authors

**Logajit S**  
**Manellore Kusuma Keerthi**

### Project

**Auto Ticket Classification using Flow Designer**

**Platform:** ServiceNow  
**Project Type:** ServiceNow Administrator Project  
**Program:** Naan Mudalvan
