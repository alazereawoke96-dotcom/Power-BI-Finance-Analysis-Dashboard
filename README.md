# Power-BI-Finance-Analysis-Dashboard
I’m excited to share my latest Power BI Finance Analysis project, where I transformed transaction data into an interactive dashboard to generate meaningful financial insights.

overview-analysis-Dashboard
<img width="960" height="511" alt="finance_img" src="https://github.com/user-attachments/assets/4914492d-ad26-4058-b351-f773f0d9969f" />

transaction
<img width="960" height="510" alt="finance_img2" src="https://github.com/user-attachments/assets/22d68037-4fef-490c-97d1-214fdfd3d397" />


DAX Measures – Financial Analysis Dashboard
The following DAX measures were created to calculate key financial KPIs and support interactive business analysis.
1. Total Amount
Calculates the total transaction amount.

Total Amount = SUM(finance_transactions[amount])

2. Total Transactions
Calculates the total number of unique transactions.
Total Transaction = DISTINCTCOUNT(finance_transactions[transaction_id])
3. Average Transaction Value
Avg Transaction value = AVERAGE(finance_transactions[amount])
4. Total Fee
Calculates the total transaction fees.
Total fee = SUM(finance_transactions[fee_amount])
5. Total Tax
Calculates the total tax collected from transactions.
Total tax = SUM(finance_transactions[tax_amount])
 
6.Dynamic Measure Selection
Dynamic Measure = {
    ("Total Amount", NAMEOF('finance_transactions'[Total Amount]), 0),
    ("Total Transaction", NAMEOF('finance_transactions'[Total Transaction]), 1),
    ("Total tax", NAMEOF('finance_transactions'[Total tax]), 2),
    ("Total fee", NAMEOF('finance_transactions'[Total fee]), 3)
}

7.Year on Year of Amount
YOY = [Total Amount]- [Previous-year-Amount]

8.Year on Year of Transaction 
YoY Transaction = [Total Transaction]-[Previous-year-Transaction]


9.Year on Year of avg Transaction
YoY avg Transaction = [Avg Transaction value]-[Previous-year-avg Transaction] 

10.Year on Year of fee
YOY Fee = [Total fee]- [Previous-year-Fee]

11.Year on Year of tax
YOY Tax = [Total tax]- [Previous-year-tax]
