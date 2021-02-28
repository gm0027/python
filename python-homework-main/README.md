# python-homework

from pathlib import Path
import csv

# Total number of months 

csvpath = Path("/Users/georgem/Downloads/budget.csv")
with open(csvpath,newline ='') as csvfile:
    csvreader = csv.reader(csvfile, delimiter = ',')
    print(csvreader)
    csv_header = next(csvreader)
    month = []
    revenue = []
    revenue_change = []
    monthly_change = []
    print(f"Header:{csv_header}")
    for row in csvreader:
        month.append(row[0])
        revenue.append(row[1])
print(len(month))


# Total amount of profit 
revenue_int = map(int,revenue)
total_revenue = (sum(revenue_int))
print(total_revenue)

# Average Change 
i = 0
for i in range(len(revenue) - 1):
    profit_loss = int(revenue[i+1]) - int(revenue[i])
    revenue_change.append(profit_loss)
    Total = sum(revenue_change)
    monhtly_change = Total / len(revenue_change)
    
monthly_change = Total / len(revenue_change)
print(monthly_change)

# Greatest increase in profits 
profit_increase = max(revenue_change)
print(profit_increase)
greatest_increase = revenue_change.index(profit_increase)
month_increase = month[greatest_increase+1]

# Greatest decrease in losses 
profit_decrease = min(revenue_change)
print(greatest_decrease)

month_decrease = revenue_change.index(profit_decrease)
month_decrease2 = month[month_decrease+1]


print(f'Financial Analysis')
print(f'----------------------------')
print("Total Number of Months: " +str(len(month)))
print("Total Revenue: $ " +str(total_revenue))
print("Average Change: $" + str(monthly_change))
print(f"Greatest Increase in Profits: {month_increase} (${profit_increase})")
print(f"Greatest Decrease in Profits: {month_decrease2} (${profit_decrease})")
