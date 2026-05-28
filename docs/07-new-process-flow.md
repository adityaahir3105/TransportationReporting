# New Digitalized Process Flow

## Overall New Flow (Simplified)

```mermaid
flowchart LR
    subgraph FIELD["🏗️ FIELD"]
        A[Machine Works\non Site] --> B[Parchi Created\nby Manager]
        B --> C[1st Copy to\nOperator]
        C --> D[Authorized Person\nVerifies on Site]
    end

    subgraph APP["📱 APP (Single Entry Point)"]
        D --> E[Office Staff Enters\nParchi Data in App]
        E --> F[Auto: Attendance\nRecorded]
        E --> G[Auto: Allowance\nCalculated & Queued]
    end

    subgraph AUTO["⚡ AUTO-GENERATED"]
        F --> H[Salary Sheet]
        G --> I[Allowance Report]
        E --> J[Billing\nHours & MT]
        E --> K[All Reports\nOne Click]
    end

    style FIELD fill:#1a5276,color:#fff
    style APP fill:#117a65,color:#fff
    style AUTO fill:#922b21,color:#fff
```

## Detailed New Process Flow

```mermaid
flowchart TD
    START([🚜 Machine Works on Site]) --> S1

    S1["1️⃣ PARCHI CREATED (Field)\n━━━━━━━━━━━━━━━━━━━\nManager creates parchi on site\n(same as before — physical slip)\nHussain Bhai / Suresh Bhai"]

    S1 --> COPY1["📄 1st Copy → OPERATOR\nProof of 24-hour work\n(same as before)"]

    S1 --> S2["2️⃣ AUTHORIZED PERSON VERIFIES\n━━━━━━━━━━━━━━━━━━━\nChecks movements, hours,\ndiesel, trips on site\n(same as before)"]

    S2 --> |"✅ Verified"| S3["3️⃣ PARCHI DATA ENTERED IN APP\n━━━━━━━━━━━━━━━━━━━\nOffice Staff enters data directly\nfrom verified parchi into app:\n• Operator  • Equipment\n• Cargo     • Hours\n• Trips     • Diesel\n• Movement  • Shift"]

    S2 --> |"❌ Rejected"| REJ[Return to\nField Manager]
    REJ --> S1

    S3 --> AUTO1["⚡ AUTO: Attendance Recorded\nOperator marked present\nfor that date automatically"]

    S3 --> AUTO2["⚡ AUTO: Allowance Calculated\nBased on configured rules\n(equipment type, shift, category)"]

    AUTO2 --> S4["4️⃣ ALLOWANCE APPROVED & PAID\n━━━━━━━━━━━━━━━━━━━\nAllowance giver reviews queue\nin app → approves → pays\nPayment tracked in app"]

    S3 --> DAILY["📊 REAL-TIME DASHBOARD\nManagement sees daily:\n• Fleet status\n• Operator activity\n• Diesel consumption\n• Cargo moved"]

    AUTO1 --> MONTH["📅 MONTH END\n━━━━━━━━━━━━━━━━━━━\nAll attendance already recorded\nAll data already verified\nNo collection / cross-check needed"]

    MONTH --> S5["5️⃣ ACCOUNTANT REVIEWS\n━━━━━━━━━━━━━━━━━━━\nAdds advances / deductions\nin app (if any)\nDigital approval"]

    S5 --> S6["6️⃣ AUTO: SALARY SHEET GENERATED\n━━━━━━━━━━━━━━━━━━━\nApp calculates:\n• Days worked (from attendance)\n• Total hours\n• Gross salary\n• Minus deductions\n• = Net salary"]

    S5 --> S7["7️⃣ AUTO: BILLING GENERATED\n━━━━━━━━━━━━━━━━━━━\nApp calculates using configured rates:\n• TON AMT = MT × Cargo Rate\n• HOUR AMT = Hours × Hour Rate\n• TOTAL = TAMT + HAMT\nFiltered by Company & Loader"]

    S6 --> EXPORT["📤 EXPORT\nExcel / PDF download\nfor salary disbursement"]

    S7 --> SEND["📧 BILLS SENT\n• RKT\n• Shu Shipping Logistics\n• Other companies"]

    S3 --> REPORTS["📊 AUTO REPORTS (Any Time)\n• Party-wise Bill\n• Cargo-wise Report\n• Machine Utilization\n• Machine Productivity\n• Daily/Monthly Statements\n• Diesel Average\n• Driver Allowance Report"]

    style START fill:#2c3e50,color:#fff
    style S1 fill:#e74c3c,color:#fff
    style COPY1 fill:#e67e22,color:#fff
    style S2 fill:#f39c12,color:#000
    style S3 fill:#27ae60,color:#fff
    style AUTO1 fill:#1abc9c,color:#fff
    style AUTO2 fill:#16a085,color:#fff
    style S4 fill:#2980b9,color:#fff
    style DAILY fill:#3498db,color:#fff
    style MONTH fill:#9b59b6,color:#fff
    style S5 fill:#8e44ad,color:#fff
    style S6 fill:#2ecc71,color:#fff
    style S7 fill:#e74c3c,color:#fff
    style EXPORT fill:#1a5276,color:#fff
    style SEND fill:#c0392b,color:#fff
    style REPORTS fill:#117a65,color:#fff
    style REJ fill:#7f8c8d,color:#fff
```

## Old vs New — Side by Side

```mermaid
flowchart TD
    subgraph OLD["❌ OLD PROCESS (8 Steps)"]
        direction TB
        O1[Parchi Created] --> O2[1st Copy → Operator]
        O1 --> O3[2nd Copy → Register Staff]
        O2 --> O4[Authorized Check]
        O4 --> O5[Hajri Card Filled]
        O5 --> O6[Allowance Paid]
        O3 --> O7[Register Book Entry]
        O7 --> O8[Evening Report]
        O8 --> O9[Excel Data Entry]
        O9 --> O10[Month-end Hajri Collection]
        O10 --> O11[Manual Cross-check]
        O11 --> O12[Manager Confirm]
        O12 --> O13[Manual Salary Sheet]
        O13 --> O14[Manual Billing]
    end

    subgraph NEW["✅ NEW PROCESS (4 Steps)"]
        direction TB
        N1[Parchi Created] --> N2[1st Copy → Operator]
        N1 --> N3[Authorized Check]
        N3 --> N4["📱 Enter in App\n(single entry)"]
        N4 --> N5["⚡ Auto: Attendance\n+ Allowance Queue"]
        N5 --> N6["⚡ Auto: Salary Sheet"]
        N5 --> N7["⚡ Auto: Billing"]
        N5 --> N8["⚡ Auto: All Reports"]
    end

    style OLD fill:#e74c3c,color:#fff
    style NEW fill:#27ae60,color:#fff
```

## New Daily Workflow Timeline

```mermaid
flowchart LR
    subgraph MORNING["🌅 Morning"]
        M1[Parchi from\nprevious 24hrs\narrives at office]
    end

    subgraph DAYTIME["☀️ During Day"]
        M1 --> D1[Office Staff\nenters parchi\ndata in app]
        D1 --> D2[App auto-records\nattendance &\ncalculates allowance]
    end

    subgraph EVENING["🌆 Evening"]
        D2 --> E1[Allowance giver\nreviews & approves\nin app]
        E1 --> E2[Payment made\nto operator bank]
    end

    subgraph ANYTIME["⏰ Any Time"]
        D1 --> A1[Dashboard shows\nreal-time data]
        D1 --> A2[Reports available\non demand]
    end

    style MORNING fill:#e67e22,color:#fff
    style DAYTIME fill:#f39c12,color:#000
    style EVENING fill:#8e44ad,color:#fff
    style ANYTIME fill:#2980b9,color:#fff
```

## Month-End Workflow (New — Simplified)

```mermaid
flowchart TD
    START([📅 Month End]) --> CHECK

    CHECK{All parchi entries\nfor the month\ncomplete?}

    CHECK --> |"Yes"| ACC["Accountant adds\nAdvances / Deductions\nin app"]
    CHECK --> |"Missing entries"| FIX["Flag missing dates\nOffice staff enters\npending parchis"]
    FIX --> CHECK

    ACC --> APPROVE["Manager approves\nvia app"]

    APPROVE --> |"✅ Approved"| GEN["App auto-generates:\n• Salary Sheet\n• Billing (Hours & MT)\n• All Reports"]
    APPROVE --> |"❌ Rejected"| ACC

    GEN --> EXPORT["Export as:\n• Excel\n• PDF"]

    EXPORT --> DONE([✅ Month-End Complete\nin ~1 day instead of ~5])

    style START fill:#2c3e50,color:#fff
    style CHECK fill:#f39c12,color:#000
    style ACC fill:#8e44ad,color:#fff
    style APPROVE fill:#2980b9,color:#fff
    style GEN fill:#27ae60,color:#fff
    style EXPORT fill:#1a5276,color:#fff
    style DONE fill:#117a65,color:#fff
    style FIX fill:#e74c3c,color:#fff
```

## Role-Based Access in App

```mermaid
flowchart TD
    APP[📱 Transportation\nReporting App] --> R1
    APP --> R2
    APP --> R3
    APP --> R4

    R1["👷 MANAGER (Field)\n─────────────\n• View parchi entries\n• View operator status\n• Dashboard (read-only)"]

    R2["👨‍💼 OFFICE STAFF\n─────────────\n• Enter parchi data\n• View/edit entries\n• Generate reports\n• Mark allowance queue"]

    R3["💰 ACCOUNTANT\n─────────────\n• Add advances/deductions\n• Approve salary sheets\n• View billing\n• Export reports"]

    R4["👔 ADMIN / OWNER\n─────────────\n• Configure rates\n• Manage users\n• View all dashboards\n• Full report access\n• Approve billing"]

    style APP fill:#2c3e50,color:#fff
    style R1 fill:#3498db,color:#fff
    style R2 fill:#27ae60,color:#fff
    style R3 fill:#9b59b6,color:#fff
    style R4 fill:#e74c3c,color:#fff
```
