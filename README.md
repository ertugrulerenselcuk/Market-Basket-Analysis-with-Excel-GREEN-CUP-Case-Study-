FILES GOOGLE DRIVE = https://docs.google.com/spreadsheets/d/1UPa3jx6PvV1LzqoOk116dlq6ExTGr-rO/edit?usp=drive_link&ouid=102618739620148941630&rtpof=true&sd=true

# 🥜 Market Basket Analysis with Excel (GREEN CUP Case Study)

This project demonstrates how to conduct **Market Basket Analysis** using Excel formulas and Pivot Tables. The analysis focuses on the product **GREEN CUP** to find out which other items are most commonly purchased with it.

---

## 📅 Step 1: Counting Product Frequencies per Basket
We begin by loading the dataset and counting how many products exist per invoice (basket).

![Step 1](https://github.com/user-attachments/assets/941ef137-b4ff-433d-9a76-58962e1505f3))

---

## 📊 Step 2: Creating a Pivot Table
Using a Pivot Table, we count how many invoices each product appears in. This helps us later calculate **support values**.

![Step 2]![image10](https://github.com/user-attachments/assets/4f29ec4a-f642-4104-b600-87f7e176d4f5)


---

## 🔍 Step 3: Identifying Target Product (GREEN CUP)
We filter the data to only include invoices containing the product **GREEN CUP**.

![Step 3]![image12](https://github.com/user-attachments/assets/2211923a-9623-4ca4-a4e8-5c1c28d054ed)


---

## 📋 Step 4: Extract Target Baskets
We define the invoices that include GREEN CUP as our **target baskets**.

![Step 4]![image13](https://github.com/user-attachments/assets/4ed4376d-6810-471a-9143-ec5f587963d2)


---

## ⚙️ Step 5: Mark Target Baskets in the Main Dataset
Using the formula below, we tag rows as "TARGET BASKET" if their invoice number matches one from the GREEN CUP list:

```excel
=IFERROR(VLOOKUP(B6, $N$5:$O$1019, 2, FALSE), "Not this product")
```

![Step 5]![image14](https://github.com/user-attachments/assets/0e6383b3-e9e2-4e6a-894f-5323263c5af2)


---

## ✔️ Step 6: Calculating Support
**Support** measures how frequently a product appears across all baskets:

```excel
Support(Product) = Baskets_with_Product / Total_Baskets
```

Example:
- GREEN CUP appears in 1,000 baskets
- Total baskets = 20,000

```excel
Support = 1000 / 20000 = 0.05 (5%)
```

![Step 6]![image20](https://github.com/user-attachments/assets/9c9f11d6-0181-4100-a427-48176a2b99e3)


---

## 📈 Step 7: Jump to Confidence
**Confidence (A → B)** measures the likelihood of buying product B when product A is bought:

```excel
Confidence(GREEN CUP → RED PLATE) = Baskets_with_both / Baskets_with_GREEN_CUP
= 750 / 1000 = 0.75
```

![Step 7]![image21](https://github.com/user-attachments/assets/d1d121ab-37db-4e63-bce3-bf8ed775afbf)


---

## 🔢 Step 8: Fetch Support Using INDEX-MATCH
We use INDEX-MATCH to fetch support values of related products to compute metrics like Lift later.

![Step 8]![image22](https://github.com/user-attachments/assets/5cc48ca4-f7eb-478d-abde-036530b72c6f)


---

## 🧹 Step 9: Match by Product Name
We match related products by name (ex: GREEN CUP) to find their associated support and co-occurrence.

![Step 9]![image23](https://github.com/user-attachments/assets/4e52b2b8-b55b-4db5-a8f3-be7a02c2b07f)


---

## 📊 Step 10: Final Confidence Table
We construct a final table showing how confidence spikes from low-support items based on association.

![Step 10]![image24](https://github.com/user-attachments/assets/80bbc16b-84ca-48ea-a015-fcbebb3c3169)


---

## 🧠 Key Metrics Explained

### 1. SUPPORT
Indicates how frequently a product appears across all transactions.

```excel
Support(A) = Number of baskets containing A / Total number of baskets
```

---

### 2. CONFIDENCE
Indicates the likelihood that product B is purchased when product A is purchased.

```excel
Confidence(A → B) = Baskets with both A and B / Baskets with A
```

---

### 3. LIFT
Compares the likelihood of purchasing A and B together with the likelihood of purchasing them independently.

```excel
Lift(A → B) = Confidence(A → B) / Support(B)
```

---

### 🔢 Sample Dataset:

| Invoice | Product       |
|---------|---------------|
| 1001    | GREEN CUP     |
| 1001    | RED PLATE     |
| 1002    | GREEN CUP     |
| 1002    | BLUE MUG      |
| 1003    | RED PLATE     |
| 1004    | GREEN CUP     |
| 1004    | RED PLATE     |
| 1005    | YELLOW FORK   |
| 1006    | GREEN CUP     |
| 1006    | RED PLATE     |

---

### ✅ Calculations: GREEN CUP → RED PLATE

#### Support(GREEN CUP)
- GREEN CUP is in invoices: 1001, 1002, 1004, 1006 → 4 baskets
- Total unique invoices: 6

```excel
Support(GREEN CUP) = 4 / 6 = 0.6667
```

#### Support(RED PLATE)
- RED PLATE is in invoices: 1001, 1003, 1004, 1006 → 4 baskets

```excel
Support(RED PLATE) = 4 / 6 = 0.6667
```

#### Support(GREEN CUP ∩ RED PLATE)
- Both in invoices: 1001, 1004, 1006 → 3 baskets

```excel
Support(GREEN CUP ∩ RED PLATE) = 3 / 6 = 0.5
```

#### Confidence(GREEN CUP → RED PLATE)

```excel
= 3 / 4 = 0.75
```

75% of GREEN CUP buyers also purchased RED PLATE.

#### Lift(GREEN CUP → RED PLATE)

```excel
= 0.75 / 0.6667 ≈ 1.125
```

Lift > 1 means RED PLATE is purchased with GREEN CUP more often than by chance.

---

## 🔍 Key Takeaways:
- GREEN CUP had only 5% **support** but led to a 75% **confidence** with RED PLATE.
- Association Rule Metrics like **Support**, **Confidence**, and **Lift** reveal powerful cross-selling insights.

You can apply these insights in:
- E-commerce product bundling
- Supermarket promotions
- Recommendation systems

---

> Built in Excel — No code, just formulas 📃📊

