README — Java & Co. Staff Scheduling Optimisation

**1. Project Overview**

This repository contains the complete analytical and computational work for the Java & Co. weekly staff-scheduling optimisation project. The objective of the analysis is to design an efficient staffing schedule that meets hourly customer demand while minimising labour cost and complying with contractual constraints.

A Mixed-Integer Linear Programming (MILP) model is used to evaluate four scenarios:

1.Baseline Scheduling
2.Early Closing at 19:00
3.Part-Time Minimum Hours: 16 Hours
4.Fairness Variant (Minimising Hmax – Hmin under a Cost Constraint)

For each scenario, the model generates total weekly labour cost, individual barista hours, and a block-by-block staffing plan. These results support operational decision-making at Java & Co.

**2. Repository Structure**

📂 java-co-scheduling/
│
├── data/
│   ├── contracts.xlsx
│   ├── demand.xlsx
│   └── wage_rates.xlsx
│
├── code/
│   ├── java_co_staff_scheduling.ipynb
│   └── java_co_model.py
│
├── results/
│   ├── baseline.txt
│   ├── close_19.txt
│   ├── parttime16.txt
│   └── fairness.txt
│
└── README.md

**3. How to Run the Code**
Requirements:
Install Python 3.9+ and the following libraries:

pip install pandas pulp numpy openpyxl

Option A — Run the Jupyter Notebook

1. Open: code/java_co_staff_scheduling.ipynb
2. Run all cells.
3. All scenario results will print automatically and export to /results/.

Option B — Run the Python Script

From the repository root:
python code/java_co_model.py

This will automatically:

load the datasets,
run all four scheduling scenarios,
print the outputs,
save results into /results/.

**4. Input Data Description**
contracts.xlsx

Contains barista-level contractual information:

-Barista name
-Minimum weekly hours
-Maximum weekly hours
-Employment type (part-time or full-time)

demand.xlsx

Includes required staffing per 4-hour block (Mon–Sat):

-07:00–11:00
-11:00–15:00
-15:00–19:00
-19:00–23:00

wage_rates.xlsx

Contains hourly wage rates for:

-Part-time staff
-Full-time staff

All input files must remain in the /data folder.

**5. Scenario Descriptions**

1. Baseline Scenario

-Full operating hours (07:00–23:00)
-Part-time minimum = 12 hours
-Objective: minimise weekly labour cost
-Resulting weekly cost: IDR 12,600,000

2. Early Closing at 19:00

-Removes the 19:00–23:00 block
-No change in hourly contracts
-Resulting weekly cost: IDR 12,600,000
-Early closure does not reduce cost due to fixed full-time hours.

3. Part-Time Minimum = 16 Hours

-Raises part-time minimum hours
-Increases cost due to forced scheduling in low-demand periods
-Resulting weekly cost: IDR 13,200,000

4. Fairness Variant

-Objective: minimise the difference between maximum and minimum hours
-Constraint: cost ≤ 102% of baseline
-Requires additional unnecessary staffing
-Resulting weekly cost: IDR 24,000,000

**6. Outputs**

The model produces the following items for each scenario:

-Total weekly labour cost
-Hours assigned to each barista
-Staffing allocation for each day × block

These are saved in /results/ as text files.

**7. Author**

Nicholas William
Course: MSCI 151 Tools and Techniques for Business Analytics
This repository forms part of the individual coursework submission.
