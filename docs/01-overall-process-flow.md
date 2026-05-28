# Overall Process Flow — Parchi to Billing

## Complete End-to-End Flow

```mermaid
flowchart LR
    subgraph FIELD["🏗️ FIELD (Stage 1)"]
        A[Machine Works\non Site] --> B[Parchi Created\nby Manager]
    end

    subgraph OPERATOR["👷 OPERATOR SIDE"]
        B --> C[1st Copy to\nOperator]
        C --> D[Authorized Check\n& Hajri Card Filled]
        D --> E[Allowance Paid\nto Operator]
    end

    subgraph OFFICE["🏢 OFFICE SIDE (Stage 2)"]
        B --> F[2nd Copy to\nRegister Staff]
        F --> G[Data Entry in\nComputer - Excel]
        G --> H[Verification &\nApproval]
        H --> I[Salary Sheet\nCreated]
    end

    subgraph BILLING["💰 BILLING (Stage 3)"]
        I --> J[Internal Billing\nHours & MT]
        J --> K[Bill Sent to\nCompanies]
    end

    style FIELD fill:#1a5276,color:#fff
    style OPERATOR fill:#117a65,color:#fff
    style OFFICE fill:#b7950b,color:#000
    style BILLING fill:#922b21,color:#fff
```

## Parchi Copy Distribution

```mermaid
flowchart TD
    P[📝 Parchi Created\n24x4 Hours] --> |"1st Copy"| OP[Operator\nFor Allowance]
    P --> |"2nd Copy"| RS[Register Staff\nFor Office Records\nSalary & Billing]

    OP --> AP[Authorized Person\nChecks & Verifies]
    AP --> HC[Hajri Card Filled]
    HC --> AG[Allowance Giver]
    AG --> BANK["💰 Daily Allowance\nPaid to Bank"]

    RS --> REG[Register / Movement\nSheet Book]
    REG --> OS[Office Staff\nExcel Entry Daily]
    OS --> VER[Month End\nVerification]
    VER --> SAL[Salary Sheet]
    SAL --> BILL["📊 Internal Billing\nHours & MT"]

    style P fill:#e74c3c,color:#fff
    style BANK fill:#27ae60,color:#fff
    style BILL fill:#2980b9,color:#fff
```

## Manager Schedule

```mermaid
gantt
    title Parchi Creation Schedule (Weekly)
    dateFormat  YYYY-MM-DD
    section Hussain Bhai
        Monday    :h1, 2024-01-01, 1d
        Wednesday :h2, 2024-01-03, 1d
        Friday    :h3, 2024-01-05, 1d
    section Suresh Bhai
        Tuesday   :s1, 2024-01-02, 1d
        Thursday  :s2, 2024-01-04, 1d
        Saturday  :s3, 2024-01-06, 1d
```

## Summary Flow (Text)

```
1st Copy Flow:
  Parchi → Operator → Authorized Person Checks
  → Hajri Card Filled → Allowance Giver → Daily Allowance Paid ✅

2nd Copy Flow:
  Parchi → Sunil & Omprakash (Register Book) → Office Staff (Excel Entry Daily)
  → Month End (Hajri Verification) → Salary Sheet → Internal Billing (RKT & Shu Shipping) ✅
```
