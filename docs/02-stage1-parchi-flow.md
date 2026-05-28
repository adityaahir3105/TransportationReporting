# Stage 1: Parchi Flow — Operator Side (Allowances)

## 1st Copy Process Flow

```mermaid
flowchart TD
    START([🚜 Machine Works on Site\nWheel Loaders & Excavators]) --> S1

    S1["1️⃣ PARCHI CREATED (24x4 Hours)\n──────────────────────\nCreated alternately by:\n• Hussain Bhai (Mon, Wed, Fri)\n• Suresh Bhai (Tue, Thu, Sat)\nFor Wheel Loaders & Excavators"]
    
    S1 --> S2["2️⃣ 1st COPY GIVEN TO OPERATOR\n──────────────────────\nOperator receives 1st copy\nas proof of 24 hours work\nOperator keeps it safe"]
    
    S2 --> S3["3️⃣ AUTHORIZED PERSON CHECKS PARCHI\n──────────────────────\nChecks all movements as per parchi\nExample:\n• 20 hours work\n• 140 liters diesel\n• Average 7 trips verified"]
    
    S3 --> S4["4️⃣ HAJRI (ATTENDANCE) CARD FILLED\n──────────────────────\nAuthorized person fills the\noperator's Hajri card\n⚠️ Operator does NOT fill it"]
    
    S4 --> S5["5️⃣ PARCHI TO ALLOWANCE GIVER\n──────────────────────\nChecked 1st copy (parchi)\ngoes to allowance authorized\nperson / patta staff"]
    
    S5 --> S6["6️⃣ DAILY ALLOWANCE PAID\n──────────────────────\nAllowance giver transfers daily\nallowance to operator's bank\n💰 ₹650 / ₹600 / ₹700 etc."]
    
    S6 --> DONE([✅ 1st COPY PROCESS COMPLETED])

    style START fill:#1a5276,color:#fff
    style S1 fill:#e74c3c,color:#fff
    style S2 fill:#e67e22,color:#fff
    style S3 fill:#f39c12,color:#000
    style S4 fill:#27ae60,color:#fff
    style S5 fill:#2980b9,color:#fff
    style S6 fill:#8e44ad,color:#fff
    style DONE fill:#117a65,color:#fff
```

## Parchi Data Captured

```mermaid
mindmap
  root((📝 PARCHI))
    Movement
      From Location
      To Location
      Equipment Used
    Cargo
      Type of Cargo
      Quantity (MT)
    Hours
      Start Time
      End Time
      Total Hours
    Trips
      Number of Trips
      Average per Day
    Diesel
      Liters Used
      Consumption Rate
    Loader / Equipment
      Equipment ID
      Equipment Type
      Wheel Loader
      Excavator
```

## Verification Checklist

```mermaid
flowchart LR
    subgraph CHECKS["Authorized Person Verification"]
        direction TB
        C1[✅ Hours Worked\n~20 hrs] --> C2[✅ Diesel Used\n~140 liters]
        C2 --> C3[✅ Trips Count\n~7 avg]
        C3 --> C4[✅ Movement\nVerified]
        C4 --> C5[✅ Cargo\nVerified]
    end

    PARCHI[📝 Parchi\n1st Copy] --> CHECKS
    CHECKS --> APPROVED[✅ Approved\nHajri Card Filled]
    CHECKS --> REJECTED[❌ Rejected\nSent Back]

    style PARCHI fill:#e74c3c,color:#fff
    style APPROVED fill:#27ae60,color:#fff
    style REJECTED fill:#c0392b,color:#fff
```

## Allowance Rates

| Allowance Type | Amount (₹) |
|---------------|-----------|
| Standard | 650 |
| Reduced | 600 |
| Premium | 700 |

> Note: Allowance amount may vary based on equipment type, shift, or operator category.
