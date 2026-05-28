# Data Model — Transportation Reporting System

## Entity Relationship Diagram

```mermaid
erDiagram
    OPERATOR {
        int operator_id PK
        string name
        string bank_account
        string category
        float daily_allowance_rate
    }

    EQUIPMENT {
        int equipment_id PK
        string equipment_type
        string equipment_name
        string status
    }

    MANAGER {
        int manager_id PK
        string name
        string schedule_days
    }

    PARCHI {
        int parchi_id PK
        date created_date
        int manager_id FK
        int operator_id FK
        int equipment_id FK
        string shift
        float total_hours
        float diesel_liters
        int trip_count
        string cargo_type
        float metric_tons
        string movement_from
        string movement_to
        string status
    }

    HAJRI_CARD {
        int hajri_id PK
        int operator_id FK
        string month_year
        string authorized_person
        date collection_date
        string verification_status
    }

    HAJRI_ENTRY {
        int entry_id PK
        int hajri_id FK
        date work_date
        boolean present
        float hours_worked
        string remarks
    }

    DAILY_REGISTER {
        int register_id PK
        int parchi_id FK
        date entry_date
        string entered_by
        string register_book_ref
    }

    EXCEL_ENTRY {
        int excel_id PK
        int parchi_id FK
        date entry_date
        string equipment_type
        string operation
        string cargo_type
        string godown
        string party_name
        float tons
        float metric_tons
        float hours_worked
        int trips
        float diesel
        string entered_by
    }

    ALLOWANCE_PAYMENT {
        int payment_id PK
        int operator_id FK
        int parchi_id FK
        date payment_date
        float amount
        string payment_method
        string approved_by
    }

    SALARY_SHEET {
        int salary_id PK
        int operator_id FK
        string month_year
        float gross_salary
        float advance_deduction
        float other_deductions
        float net_salary
        string approved_by
        date created_date
    }

    CARGO_RATE {
        int rate_id PK
        string cargo_type
        float rate_per_mt
        date effective_from
        date effective_to
    }

    HOUR_RATE {
        int rate_id PK
        string association_name
        float rate_per_hour
        date effective_date
    }

    BILLING {
        int billing_id PK
        int operator_id FK
        int equipment_id FK
        string company_name
        string billing_period
        float ton_amount
        float hour_amount
        float total_amount
        date created_date
        string status
    }

    OPERATOR ||--o{ PARCHI : "works on"
    MANAGER ||--o{ PARCHI : "creates"
    EQUIPMENT ||--o{ PARCHI : "used in"
    OPERATOR ||--o{ HAJRI_CARD : "has"
    HAJRI_CARD ||--o{ HAJRI_ENTRY : "contains"
    PARCHI ||--o| DAILY_REGISTER : "recorded in"
    PARCHI ||--o| EXCEL_ENTRY : "entered as"
    OPERATOR ||--o{ ALLOWANCE_PAYMENT : "receives"
    PARCHI ||--o| ALLOWANCE_PAYMENT : "triggers"
    OPERATOR ||--o{ SALARY_SHEET : "has"
    OPERATOR ||--o{ BILLING : "billed for"
    EQUIPMENT ||--o{ BILLING : "billed for"
    CARGO_RATE ||--o{ BILLING : "rate used"
    HOUR_RATE ||--o{ BILLING : "rate used"
```

## Key Entities

### Core Entities
| Entity | Description |
|--------|-------------|
| **Operator** | The machine operator working on site |
| **Equipment** | Wheel loaders, excavators, etc. |
| **Manager** | Field managers who create parchi (Hussain Bhai / Suresh Bhai) |
| **Parchi** | The primary document — a 24-hour work slip |

### Process Entities
| Entity | Description |
|--------|-------------|
| **Hajri Card** | Monthly attendance card for each operator |
| **Hajri Entry** | Daily attendance record within a Hajri card |
| **Daily Register** | Physical register book entry (2nd copy) |
| **Excel Entry** | Digital data entry of parchi in Excel |

### Financial Entities
| Entity | Description |
|--------|-------------|
| **Allowance Payment** | Daily allowance paid to operator from 1st copy |
| **Salary Sheet** | Monthly salary after verification and deductions |
| **Cargo Rate** | Rate per MT for different cargo types |
| **Hour Rate** | Hourly rate from association (changes daily) |
| **Billing** | Final internal billing sent to companies |

## State Diagrams

### Parchi Lifecycle

```mermaid
stateDiagram-v2
    [*] --> Created: Manager creates parchi
    Created --> CopyDistributed: Split into 1st & 2nd copy
    
    state CopyDistributed {
        [*] --> FirstCopy
        [*] --> SecondCopy
        
        state FirstCopy {
            [*] --> WithOperator
            WithOperator --> Checked: Authorized person verifies
            Checked --> HajriFilled: Attendance card updated
            HajriFilled --> AllowancePaid: Payment transferred
            AllowancePaid --> [*]
        }
        
        state SecondCopy {
            [*] --> Registered: Entered in register book
            Registered --> ExcelEntered: Data entered in Excel
            ExcelEntered --> Verified: Month-end verification
            Verified --> SalaryProcessed: Salary sheet created
            SalaryProcessed --> Billed: Internal billing done
            Billed --> [*]
        }
    }
    
    CopyDistributed --> Completed: Both flows complete
    Completed --> [*]
```

### Billing Status Flow

```mermaid
stateDiagram-v2
    [*] --> DataCollected: Excel entries compiled
    DataCollected --> RatesApplied: Cargo & Hour rates applied
    RatesApplied --> Calculated: TON AMT + HOUR AMT
    Calculated --> ReviewPending: Sent for manager review
    ReviewPending --> Approved: Manager approves
    ReviewPending --> Rejected: Discrepancy found
    Rejected --> DataCollected: Re-verify data
    Approved --> Dispatched: Bill sent to company
    Dispatched --> [*]
```
