# 💸 Cash Flow Minimizer: Settling Debts with the Minimum Number of Transactions

This project focuses on minimizing the **number of transactions** required to clear all debts among a group of individuals. It ensures that all dues are settled with the **least total money exchanged**, using a graph-based greedy algorithm.

---

## 🧠 Project Overview

In scenarios like roommate bills, group trips, or business partnerships, people owe each other money. Instead of everyone paying everyone, this project figures out an optimized set of transactions to settle all debts.

---

## 📊 Algorithm Explained

The project uses **graph theory** and a **priority queue (heap)** based greedy approach:

### ➤ Phase 1: Net Calculation

- For each person, calculate:
netAmount = total_incoming - total_outgoing

### ➤ Phase 2: Transaction Minimization

- Build:
- Max-heap for **creditors** (positive net)
- Min-heap for **debtors** (negative net)

- While both heaps are non-empty:
- Pop top debtor and creditor
- Transfer `min(creditor, -debtor)`
- Update and reinsert if balances remain

---

## 💻 Example Code (C++)

```cpp
vector<string> people = {"Eli", "Barb", "Mike"};
CashFlowMinimizer minimizer(people);

minimizer.addDebt("Eli", "Barb", 1000);
minimizer.addDebt("Eli", "Mike", 2000);
minimizer.addDebt("Barb", "Mike", 5000);
minimizer.addDebt("Mike", "Eli", 3000);

vector<Transaction> transactions = minimizer.minimizeTransactions();

✅ Sample Execution
🧾 Input:
Eli → Barb: $1000

Eli → Mike: $2000

Barb → Mike: $5000

Mike → Eli: $3000

🧮 Net Balances:
Eli: 0

Barb: -$4000

Mike: +$4000
