# Prosper Loan data Exploration
## by Shubhangi


## Prosper Loans:

> This project investigates the data from Prosper Loan which is a lending platform(Peer-to-Peer).
The main features of interest are:
1. What factors affect the loan's outcome status? Does it depend on Credit scores, purpose of the loan, term of the loan, Income Range of the loanee?
2. What factors affect the Borrower's APR i.e. Annualized Payment Rate? Are some borrowers more credit-worthy that others? How far is it justified? 
3. Are there differences between loans depending on how large the loan amount was?Are larger loans less predictable and riskier or vice-versa? Does the number of investors funding a loan have any impact on diversification/mitigation of risk?

> Data wrangling :
1. Created a column which shows the purpose of the loan from the ListingCategory (numeric) : replaced the numerals with what they signify and merge the categories '11' and '20' into a single category of 'wedding loans'.
2. Filled the null values of EmploymentStatus with 'NA' and merged this with 'Not Available'. Also, merged 'Self-employed', 'Employed','Full-time', 'Part-time' into a single category.
3. Converted LoanStatus into a Categorical type variable .Merge 'ChargedOff' and 'Completed' ; Past Due (1-15 days) and Past Due(15-30 days) because all other payment delay categories have a uniform difference of 30 days.
4. Performed data imputation for some variables as well.
5. Data Engineering : I have created three columns : CostofBorrowing , *LoanSize and CreditScore ; both of these are functions of the existing variables, however they will help us investigate the data set better.

> Complete details of the data be found from : https://docs.google.com/spreadsheets/d/1gDyi_L4UvIrLTEC6Wri5nbaMmkGmLQBk-Yx3z0XDEtI/edit#gid=0


## Summary of Findings

> In the exploration I found the following things:
> BorrowerAPR:
1. *LoanStatus* : Defaulted loans have lower BorrowerAPR than the ones Charged off and the ones with delays. 
2. *LoanSize*: Anomaly : **The BorrowerAPR is higher and more variable for lower range loans**. It decreases with increase in Loan Amount.
3. *CreditScore* and *ProsperRating* :  The average Borrower APR increases with decrease in the quality of ratings.**There is a small caveat here : for people with credit score in the range of 420 - 519, the interest rates are lower than the ones in the range of 520 - 599.**
4. *PurposeOfLoan* : **Interestingly the "Unknown" category has the lowest interest rates. Debt Consolidation has lower interest charges than student loans. Debt Consolidation interest rates are amongst the lowest rates charged.**
5. *Income Range* and *EmploymentStatus* :  **with increase in income the APR reduces.** And this not a factor of higher loan sizes or debt to Income Ratios.

> LoanStatus :
6. Interaction of ***LoanStatus*** with various variables : $Credit Score$ People between 460 - 799 form a potential risk group with (640 -659) witnessing highest defaults. This should be rectified. People with better credit score should have lower defaults. $PurposeofLoan$ **Debt Consolidation and Unknown** loans form another risk factor in giving out loans. $ProsperRating (Alpha)$ **Unrated loans** have led to maximum defaults. This risk can be should be eliminated.
7. Interaction of ***LoanStatus*** with : $DebtToIncomeRatio$ : Delayed and Defaulted loans generally have higher DBI. $LenderYield$ : Increase in delays have generally led to higher Lender yields. This can be explained by $Cost of Borrowing$ : which increases with increase in delays, however for loans under defaulted category, cost of borrowing falls(this is because such loans were never paid up). $Investors$ : Charged off, Delayed and Defaulted loans in the past have seen higher number of investors.

> Loan Size :
8. *LenderYield* : With increase in the loan size, the lender's yield decreases. 
9. *CostofBorrowing* : Borrowing smaller loans attracts higher borrowing costs. **This is interesting**.
10. *Investors* : As the loan size increases, the amount of investors too increase. This helps in risk diversification.
11. *DebtToIncomeRatio* : People who have taken larger loans have slightly higher DBI as compared to the smaller loans.
12. A major chunk of the large and small sized loans fall under "Charged Off", "Current" and "Defaulted" categories. Also, as we now know that the employed section is the largest loan taker. **"Not Employed" and "Retired" sections mostly take smaller loans**. Another interesting feature to note here is that **"NA"** section is the next largest loan taker. The status of Employment should be registered and verified by the administration.
13. Large size loans are mostly taken for Debt Consolidation, Unknown, Business and Home Improvement Purposes. While the smaller loans are taken for Debt Consolidation, Business, Personal loans, Vacation etc. Loan between (12000 - 35000) dollars are given to people with credit scores in between 520 - 879. Smallest category of loans are given to people with 460 - 879.


## Key Insights for Presentation

> For the presentation, I focused on Borrower's APR and its relationship with qualitative variables like Loan Status(Categorical), Loan Size(categorical), Employment Status and Purpose of the loan.
1. **For the same sized loans, people with lower incomes pay higher interest rates.**
2. For the same purpose of the loan, people with lower incomes pay higher interest rates.
3. **Lower income groups are paying higher charges for the same status of the loan.

**These relationships are potentially due to **Unrated, Unknown purposes and Lack of employment status and income range** of the loanees. This anomaly can be rectified by addressing these.

> Sources :
1. Udacity - example project template.
