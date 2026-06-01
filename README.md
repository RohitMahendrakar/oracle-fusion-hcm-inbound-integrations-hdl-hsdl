# Oracle Fusion HCM Inbound Integrations using HDL & HSDL

## 📌 Project Overview

This project demonstrates Oracle Fusion HCM inbound integration concepts using:

- HCM Data Loader (HDL)
- HCM Spreadsheet Data Loader (HSDL)

The project includes:
- HDL file structure
- Worker and work structure loads
- Source keys and user keys
- Date-effective changes
- HSDL spreadsheet-based integrations
- Error handling and troubleshooting
- Practical implementation screenshots

> Note:
> - Workflow and approval-related topics are intentionally excluded.
> - Payroll Batch Loader is excluded because it is discontinued for current implementations.

---

# 🛠 Technologies & Concepts Covered

## Oracle Fusion HCM Modules
- Core HR
- Workforce Structures
- Worker Management

## Integration Technologies
- HCM Data Loader (HDL)
- HCM Spreadsheet Data Loader (HSDL)

---



---

# 🔹 HCM Data Loader (HDL)

## What is HDL?

HCM Data Loader is Oracle Fusion HCM’s file-based bulk data loading tool used to:

- Create records
- Update records
- Maintain date-effective history
- Load large volumes of hierarchical data

HDL validates the data, loads it into staging tables, performs business validations, and finally pushes valid records into Fusion HCM base tables.

---

# 🔹 HDL File Structure

HDL files are pipe-delimited (`|`) text files.

## Common HDL Instructions

| Instruction | Purpose |
|---|---|
| METADATA | Defines object attributes |
| MERGE | Insert or update records |
| DELETE | Delete supported records |
| COMMENT | Add comments |
| SET | Override HDL behavior |

---

# 🔹 Sample HDL File

## Job Load Example

```text
COMMENT Data for Business Object: Job

METADATA|Job|JobCode|EffectiveStartDate|EffectiveEndDate|Name|SetCode

MERGE|Job|TECH_DEV|2024/01/01|4712/12/31|Technical Developer|COMMON
```

---

# 🔹 HDL Supported Business Objects

## Workforce Structures
- Jobs
- Departments
- Locations
- Positions
- Grades

## Worker Objects
- Worker
- Work Relationship
- Work Terms
- Assignment
- Person Name
- Person Legislative Data
- Person Email
- Person Phone

---

# 🔹 Worker Load Example

```text
METADATA|Worker|PersonNumber|EffectiveStartDate|EffectiveEndDate|StartDate|DateOfBirth|ActionCode|SourceSystemOwner|SourceSystemId

MERGE|Worker|4001|2024/01/01|4712/12/31|2024/01/01|1995/01/10|HIRE|LEGACY|EMP4001

METADATA|PersonName|EffectiveStartDate|EffectiveEndDate|PersonNumber|LegislationCode|NameType|FirstName|LastName|SourceSystemOwner|SourceSystemId

MERGE|PersonName|2024/01/01|4712/12/31|4001|US|GLOBAL|John|Smith|LEGACY|EMP4001
```

---

# 🔹 HDL Keys

HDL supports multiple key types for identifying records.

## Key Types

| Key Type | Description |
|---|---|
| GUID | Fusion internal identifier |
| Surrogate ID | Backend numeric identifier |
| Source Keys | SourceSystemOwner + SourceSystemId |
| User Keys | Business-visible keys |

## Recommended Approach

For integrations and conversions:
- Use Source Keys during initial loads
- Use User Keys for future maintenance where applicable

---

# 🔹 Date Effective Changes

HDL supports complete date-effective history maintenance.

## Examples
- Hire
- Promotion
- Transfer
- Assignment Change
- Location Change
- Termination

---

# 🔹 Assignment Change Example

```text
METADATA|Assignment|AssignmentNumber|EffectiveStartDate|EffectiveEndDate|EffectiveLatestChange|EffectiveSequence|WorkTermsNumber|LegalEmployerName|PersonNumber|DateStart|WorkerType|AssignmentStatusTypeCode|BusinessUnitShortCode|ActionCode|JobCode|LocationCode|DepartmentName|PrimaryAssignmentFlag|SourceSystemOwner|SourceSystemId

MERGE|Assignment|E4002|2024/05/01|4712/12/31|Y|1|ET4002|Vision Corporation|4002|2024/01/01|E|ACTIVE_PROCESS|Vision BU|ASG_CHANGE|HR_MANAGER|US_NY|HR_DEPT|Y|LEGACY|ASG4002
```

---

# 🔹 HCM Spreadsheet Data Loader (HSDL)

## What is HSDL?

HSDL is an Excel-based data loading framework built on top of HDL.

It allows users to:
- Load data directly from Excel
- Validate records
- Correct errors in spreadsheet
- Reload failed records

---

# 🔹 HSDL Features

- User-friendly Excel templates
- ADF Desktop Integration
- Error correction support
- Reduced technical complexity
- Faster business-user adoption

---

# 🔹 HSDL Requirements

## Required Components

- Oracle ADF Desktop Integration Add-in
- Microsoft Excel
- Fusion HCM Spreadsheet Templates

## Important Rules

- Do not rename worksheet tabs
- Do not delete mandatory columns
- Do not hide status columns
- Use predefined templates only

---

# 🔹 HDL Error Handling

## Physical Errors
Examples:
- Incorrect instruction tags
- Invalid delimiters
- Metadata mismatch
- Missing parent objects

## Logical Errors
Examples:
- Invalid business values
- Invalid lookup codes
- Missing referenced objects
- Date-effective conflicts

---

# 🔹 HDL Troubleshooting

## Common Troubleshooting Methods

### 1. Import and Load Data UI
- Review failed rows
- Analyze object errors

### 2. HDL Data Set Summary
- Review failed objects
- Validate successful loads

### 3. Backend Validation
- Validate source keys
- Validate user keys
- Verify object relationships

---

# 🔹 Screenshots Included

This repository also contains screenshots of the implementation process for reference and learning purposes.

## Screenshot Coverage
- HDL File Creation
- Worker Load Implementation
- Job and Department Loads
- HSDL Spreadsheet Loads
- Error Handling
- Import and Load Process
- Successful Data Load Validation

> Please refer to the `Screenshots` folder to view the implementation steps and outputs.

---

# 🔹 Key Learning Outcomes

By completing this project, you will understand:

- Oracle Fusion HCM inbound integration architecture
- HDL file creation and processing
- HSDL spreadsheet integrations
- Worker and work structure loading
- Date-effective updates
- Source key handling
- HDL troubleshooting and diagnostics

---

# 🚀 Use Cases

This project can be used for:

- Oracle Fusion HCM implementation practice
- Real-time data conversion scenarios
- Integration learning
- Resume and portfolio projects
- Oracle Fusion technical interview preparation

---

# 📚 Concepts Covered

- HDL
- HSDL
- Source Keys
- User Keys
- Date Effective Records
- Worker Loading
- Work Structure Loading
- Error Handling
- Troubleshooting

---

# 👨‍💻 Author

Rohit Anand

Oracle Fusion HCM Technical Learning Project  
Inbound Integrations using HDL & HSDL
