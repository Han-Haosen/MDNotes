# MSCI 261 Engineering Economics Notes

## Lecture 1 

5% Homework, 5% Quiz on tutorial, 20% Assignment, 30% Midterm, 40% Final

Principles of Finance with Excel 

Repalcing existing machine with newer, faster, more expensive machine 

how to do this? 

Cost and profit analysis 

Sunk cost 

equity -- the value of the shares issued by a company. OR 

the loan on a stuff you own 

8 Principles of finance 

1. Buy assets that add value, don't buy those that don't add value 
2. Cash is King
3. Time dimension is important 
4. KNow how to compute the cost of financial alternatives(i.e loan)
5. Minimize cost of financing
6. Take risk into account
7. Market are efficient and deal well with information 
8. Diversification is important 

EXCEL 

most essential technical skill 

Both Finance and Excel 

## Lecture 2 

Chapter 2 

Time value of money 

simple interest  = 10% 

t | amount  | interest 
---------|----------|---------
 0 | 100 | 10
 1 | 110 | 10
 2 | 120 | 


compound interest: 

got interest of interest 

still 10 percent 

t | amount  | interest 
---------|----------|---------
 0 | 100 | 10
 1 | 110 | 11
 2 | 110(1+r) = 121 |  10
 3 | 100(1+r)^3

 Excel functions 

 FV future value 

 PV present value 

 NPV Net Present Value : the difference between the present value of cash inflows and the present value of cash outflows over a period of time.
 
 PMT : Excel PMT function payment function calculate repayment amount on a loan 
 
 NPER : Returns the number of periods for an investment based on periodic, constant payments and a constant interest rate.
 
 RATE 

 100/(1+i)^N = PV of 100 in the future 

 net present value 


## Lecture 3 

future value and present value 

sum together each year's PV becomes the whole pv of the future value 

## Lecture 4 

PV type = 1 for beginning of period payments

Time value of money 

Loan : term?

use PMT for a loan, i.e payment for a loan

PMT(interest,term = years, principal of payment)

use goal seek 

NPV = - amount initial + cash/(1+r)^year

IRR A > IRR B means preferrable: Not really 

## Lecture 5 

IRR interdependent project 

Cash Flow 


Column A | Column B | Column C
---------|----------|---------
 -2500 | -1000 | C1
 150 | 500 | C2
 2000 | 570 | C3
 5000 | 750 | 

 IRR = ?

 Crossover point IRRa = IRRb
  
compute IRR of differentail cash flows 

NPV rule with differnt life spans 

EAC 

a constant future cash flow whose present value is equal to the NPV of the project 

CF0 + NPV(...)

for IRR, the IRR difference is when discount rate changes to such that one is better than the other 

EAC = -PMT()

NPV = C5 + NPV(...)

### Loan

Interest only loan : principal repaid at the end of terminal 

equal amortization term loan: each period, equal amount of loan principle. Interest in each period is the paid on the outstanding principal at beginnign of period 

Term Loan: mortgage loan, equal payments are paid in every period. 

break down of payments between interest and repayment of principal varies by period 

Amortization table 

Loan Balance at begin | Interest payment = r* A | principal repayment | Total payment = B + C | Loan Principal Balance at end of year = A - C | 


## Lecture 6 

Loans and Amortization tables

100000 = PMT/(1+r)^year

PMT converts PV of mortage to A(annuity) equal payments

after 3 years interval -- renegotiate

leverage & returns 

