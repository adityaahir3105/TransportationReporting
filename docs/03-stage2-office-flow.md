# Stage 2: Office Record Flow — Office Side

## 2nd Copy Process Flow

```mermaid
flowchart TD
    START([📋 2nd Copy of Parchi]) --> S1

    S1["1️⃣ 2nd COPY TO REGISTER STAFF\n──────────────────────\nGiven to Sunil & Omprakash\nEntered in Register / Movement\nSheet type book\nAll reports maintained in single\nbook for daily movement"]
    
    S1 --> S2["2️⃣ REPORT TO OFFICE STAFF (EVENING)\n──────────────────────\nIn the evening, the register\nreport is given to Office Staff"]
    
    S2 --> S3["3️⃣ DATA ENTRY IN COMPUTER (EXCEL)\n──────────────────────\nOffice Staff enters same details\nin Excel / Computer daily:\n• Movement\n• Cargo\n• Hours\n• Trips\n• Diesel\n• Loader/Equipment wise"]
    
    S3 --> S4["4️⃣ MONTH END — HAJRI CARD COLLECTION\n──────────────────────\nAt end of month, all Hajri cards\nfilled by Kandia staff (authorized\nperson) are sent to Office Staff"]
    
    S4 --> S5{"5️⃣ HAJRI CARD VERIFICATION\n& CHECKING\n──────────────────────\nOffice Staff checks Hajri cards\nwith daily entries in Excel\n(filter by name)\nIs Hajri attested and correct?"}
    
    S5 --> |"✅ Yes - Approved"| S6["6️⃣ MANAGER & ACCOUNTANT\nCONFIRMATION\n──────────────────────\nOffice Staff calls Managers for\nother items like:\n• Advance\n• Deductions\n• Other adjustments\nAccountant provides list of\nadvances and deductions"]
    
    S5 --> |"❌ No - Discrepancy"| REJECT[🔄 Sent Back for\nRe-verification]
    REJECT --> S5
    
    S6 --> S7["7️⃣ SALARY SHEET CREATION\n──────────────────────\nAfter all verifications and\ndeductions (Advance, etc.)\nOffice Staff creates final\nSalary Sheet of operators"]
    
    S7 --> S8["8️⃣ INTERNAL BILLING CREATION\n(BY HOURS & MT)\n──────────────────────\nOffice Staff creates internal\nbilling by Hours and Metric Tons\nEntries filtered by:\n• Company wise\n• Loader wise\nBills prepared and sent to\ninternal companies / other firms"]
    
    S8 --> RKT[📧 RKT — Billing created\nand sent to RKT\nDedicated Office Staff]
    S8 --> SHU[📧 SHU SHIPPING LOGISTICS\nBilling created and sent\nDedicated Office Staff]
    
    RKT --> DONE([✅ 2nd COPY PROCESS COMPLETED])
    SHU --> DONE

    style START fill:#1a5276,color:#fff
    style S1 fill:#2980b9,color:#fff
    style S2 fill:#3498db,color:#fff
    style S3 fill:#1abc9c,color:#fff
    style S4 fill:#16a085,color:#fff
    style S5 fill:#f39c12,color:#000
    style S6 fill:#e67e22,color:#fff
    style S7 fill:#9b59b6,color:#fff
    style S8 fill:#8e44ad,color:#fff
    style RKT fill:#e74c3c,color:#fff
    style SHU fill:#c0392b,color:#fff
    style DONE fill:#117a65,color:#fff
    style REJECT fill:#e74c3c,color:#fff
```

## Daily Data Entry Fields

```mermaid
erDiagram
    DAILY_ENTRY {
        date entry_date
        string shift
        string equipment_id
        string equipment_type
        string operation_type
        string cargo_type
        string godown
        string party_name
        float tons
        float metric_tons
        float hours_worked
        int trip_count
        float diesel_liters
        string loader_id
        string operator_name
    }
```

## Office Workflow Timeline

```mermaid
flowchart LR
    subgraph DAILY["📅 Daily Process"]
        D1[Morning:\nParchi 2nd Copy\nReceived] --> D2[Register Entry\nby Sunil/Omprakash]
        D2 --> D3[Evening:\nReport to\nOffice Staff]
        D3 --> D4[Excel Data\nEntry]
    end

    subgraph MONTHLY["📆 Monthly Process"]
        M1[Hajri Cards\nCollected] --> M2[Cross-Check\nwith Excel]
        M2 --> M3[Manager &\nAccountant\nConfirmation]
        M3 --> M4[Salary Sheet\nCreated]
        M4 --> M5[Internal\nBilling]
    end

    DAILY --> |"Month End"| MONTHLY

    style DAILY fill:#2c3e50,color:#fff
    style MONTHLY fill:#1a5276,color:#fff
```

## Billing Recipients

```mermaid
flowchart TD
    BILL[📊 Internal Billing\nCreated] --> FILTER{Filter By}
    
    FILTER --> |"Company Wise"| CW[Company-wise\nBreakdown]
    FILTER --> |"Loader Wise"| LW[Loader-wise\nBreakdown]
    
    CW --> RKT[🏢 RKT\nDedicated Staff]
    CW --> SHU[🏢 Shu Shipping\nLogistics\nDedicated Staff]
    CW --> OTHER[🏢 Other Internal\nCompanies]
    
    LW --> L1[Wheel Loader 1]
    LW --> L2[Wheel Loader 2]
    LW --> L3[Excavator 1]

    style BILL fill:#8e44ad,color:#fff
    style RKT fill:#e74c3c,color:#fff
    style SHU fill:#c0392b,color:#fff
```

## Summary — 2nd Copy Flow

```
2nd Copy → Sunil & Omprakash (Register Book) 
  → Office Staff (Excel Entry Daily) 
  → Month End (Hajri Verification) 
  → Salary Sheet 
  → Internal Billing (RKT & Shu Shipping Logistics)
```
