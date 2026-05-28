# Stage 3: Billing — Excel Report & Final Bill

## Billing Calculation Flow

```mermaid
flowchart TD
    INPUT([📊 Salary Sheet &\nVerified Data]) --> CALC

    subgraph CALC["BILLING CALCULATION ENGINE"]
        direction TB
        
        subgraph TON_CALC["💎 Tonnage-Based Calculation"]
            T1[TON Rate] --> T2[Cargo Rate\nPer MT]
            T2 --> T3["TON AMT = MT × TON RATE"]
            T3 --> TAMT[T.AMT\nTotal Amount MT]
        end
        
        subgraph HOUR_CALC["⏰ Hours-Based Calculation"]
            H1[Hour Rate] --> H2[Association Rate\nPer Hour]
            H2 --> H3["HOUR AMT = NET HOURS × HOUR RATE"]
            H3 --> HAMT[H.AMT\nTotal Amount Hours]
        end
        
        TAMT --> TOTAL["🧮 TOTAL AMOUNT\n= TAMT + HAMT"]
        HAMT --> TOTAL
    end
    
    TOTAL --> OUTPUT[📄 Final Bill\nGenerated]

    style INPUT fill:#2c3e50,color:#fff
    style CALC fill:#1a1a2e,color:#fff
    style TON_CALC fill:#1a5276,color:#fff
    style HOUR_CALC fill:#117a65,color:#fff
    style TOTAL fill:#e74c3c,color:#fff
    style OUTPUT fill:#27ae60,color:#fff
```

## Excel Report Structure

```mermaid
block-beta
    columns 10
    
    block:header:10
        h["📋 OFFICE REPORT / EXCEL FORMAT (Final Calculation Sheet)"]
    end
    
    Date Shift Equipment Operation Cargo Godown Party TON MT Rates
    
    style header fill:#1a5276,color:#fff
```

### Billing Column Details

| Column | Description | Example |
|--------|-------------|---------|
| Date | Entry date | 2024-01-15 |
| Shift | Day/Night shift | Day |
| Equipment | Loader/Excavator ID | WL-01 |
| Operation | Type of operation | Loading |
| Cargo | Type of cargo | NPK, DAP, MOP |
| Godown | Warehouse/storage | Godown-A |
| Party | Client/company name | RKT |
| TON | Tonnage amount | 50 |
| MT | Metric Tons | 50 |
| TON RATE | Rate per MT (cargo-wise) | ₹400 |
| HOUR RATE | Rate per hour | ₹1500 |
| T.AMT | TON Amount | ₹20,000 |
| H.AMT | HOUR Amount | ₹30,000 |
| TOTAL | T.AMT + H.AMT | ₹50,000 |

## Cargo-wise MT Rates

```mermaid
xychart-beta
    title "Cargo-wise MT Rates (₹)"
    x-axis ["NPK", "DAP", "MOP", "APL", "IRON"]
    y-axis "Rate Per MT (₹)" 350 --> 550
    bar [400, 480, 500, 450, 530]
```

| Cargo | Rate (Per MT) ₹ |
|-------|-----------------|
| NPK | 400 |
| DAP | 480 |
| MOP | 500 |
| APL | 450 |
| IRON | 530 |

## Hour Rate (Association)

| Parameter | Value |
|-----------|-------|
| Rate (Per Hour) | ₹1,500 |
| Note | Rate changes as per Association daily |

## Amount Calculation Formulas

```mermaid
flowchart LR
    subgraph FORMULA["📐 Billing Formulas"]
        direction TB
        F1["TON AMT = MT × TON RATE\n(Cargo-specific rate)"]
        F2["HOUR AMT = NET HOURS × HOUR RATE\n(Association rate)"]
        F3["TOTAL AMOUNT = TAMT + HAMT"]
        F1 --> F3
        F2 --> F3
    end

    style FORMULA fill:#2c3e50,color:#fff
```

### Example Calculation

```
Operator: Ram Kumar
Date: 2024-01-15
Equipment: Wheel Loader WL-01
Cargo: NPK

Tonnage Calculation:
  MT loaded    = 50 MT
  TON RATE     = ₹400/MT (NPK rate)
  TON AMT      = 50 × 400 = ₹20,000

Hours Calculation:
  Net Hours    = 20 hours
  HOUR RATE    = ₹1,500/hour
  HOUR AMT     = 20 × 1500 = ₹30,000

TOTAL AMOUNT   = ₹20,000 + ₹30,000 = ₹50,000
```

## Final Outputs Generated

```mermaid
flowchart TD
    SYSTEM[📊 Billing System] --> O1[📄 Party-wise Bill]
    SYSTEM --> O2[💰 Driver Allowance]
    SYSTEM --> O3[📦 Cargo-wise Report]
    SYSTEM --> O4[🔧 Machine Utilization]
    SYSTEM --> O5[📈 Machine Productivity]
    SYSTEM --> O6[📋 Daily / Monthly\nStatements]
    SYSTEM --> O7[⛽ Diesel Average]
    SYSTEM --> O8[🏢 Internal Billing\nRKT & Shu Shipping]

    style SYSTEM fill:#8e44ad,color:#fff
    style O1 fill:#3498db,color:#fff
    style O2 fill:#27ae60,color:#fff
    style O3 fill:#e67e22,color:#fff
    style O4 fill:#1abc9c,color:#fff
    style O5 fill:#2ecc71,color:#fff
    style O6 fill:#9b59b6,color:#fff
    style O7 fill:#e74c3c,color:#fff
    style O8 fill:#c0392b,color:#fff
```
