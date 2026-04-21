# Star Schema – Cloud Data Pipeline

## 📌 Overview
This star schema represents the Gold Layer of the data pipeline where transformed and curated data is stored for analytics and reporting.

- **Fact Table**: Stores measurable business metrics
- **Dimension Tables**: Provide descriptive context

---

## 🟦 Fact Table

### FACT_SALES
| Column Name      | Description |
|-----------------|------------|
| order_id         | Unique order identifier |
| customer_id      | Foreign key to DIM_CUSTOMER |
| product_id       | Foreign key to DIM_PRODUCT |
| date_id          | Foreign key to DIM_DATE |
| store_id         | Foreign key to DIM_STORE |
| quantity         | Number of items sold |
| sales_amount     | Total sales value |
| discount         | Discount applied |
| profit           | Profit earned |

---

## 🟩 Dimension Tables

### DIM_CUSTOMER
| Column Name   | Description |
|--------------|------------|
| customer_id   | Primary key |
| customer_name | Customer name |
| email         | Email address |
| phone         | Contact number |
| city          | City |
| state         | State |
| country       | Country |

---

### DIM_PRODUCT
| Column Name   | Description |
|--------------|------------|
| product_id    | Primary key |
| product_name  | Product name |
| category      | Product category |
| sub_category  | Sub category |
| price         | Product price |

---

### DIM_DATE
| Column Name | Description |
|------------|------------|
| date_id     | Primary key |
| date        | Full date |
| day         | Day |
| month       | Month |
| quarter     | Quarter |
| year        | Year |

---

### DIM_STORE
| Column Name | Description |
|------------|------------|
| store_id    | Primary key |
| store_name  | Store name |
| location    | Store location |
| region      | Region |

---

## 🔗 Relationships

- FACT_SALES.customer_id → DIM_CUSTOMER.customer_id
- FACT_SALES.product_id → DIM_PRODUCT.product_id
- FACT_SALES.date_id → DIM_DATE.date_id
- FACT_SALES.store_id → DIM_STORE.store_id

---

## 🎯 Use Cases

- Sales trend analysis
- Customer behavior insights
- Product performance tracking
- Regional sales reporting

---
