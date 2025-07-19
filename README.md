# stock-portfolio-tracker



stock_prices = {
    "APPLE": 180,
    "TESLA": 250,
    "GOOGLE": 2800,
    "AMAZON": 3500,
    "MICROSOFT": 300
    "RELIANCE": 3000
}

# Dictionary to hold user's portfolio
portfolio = {}

print("📈 Welcome to the Stock Portfolio Tracker!")
print("Available Stocks: ", ", ".join(stock_prices.keys()))

# Taking user input
while True:
    stock = input("Enter stock symbol (or type 'done' to finish): ").upper()
    if stock == 'DONE':
        break
    if stock not in stock_prices:
        print("❌ Stock not found! Please choose from available stocks.")
        continue
    try:
        quantity = int(input(f"Enter quantity of {stock} shares: "))
        if quantity <= 0:
            print("❌ Quantity must be greater than 0.")
            continue
        if stock in portfolio:
            portfolio[stock] += quantity
        else:
            portfolio[stock] = quantity
    except ValueError:
        print("❌ Please enter a valid number.")

# Calculate total investment
total_value = 0
print("\n🧾 Your Portfolio Summary:")
for stock, qty in portfolio.items():
    value = qty * stock_prices[stock]
    total_value += value
    print(f"{stock} - {qty} shares x ₹{stock_prices[stock]} = ₹{value}")

print(f"\n💰 Total Investment Value: ₹{total_value}")

# Optional: Save to file
save = input("Do you want to save this report to a file? (yes/no): ").lower()
if save == "yes":
    with open("stock_portfolio_report.txt", "w") as file:
        file.write("Stock Portfolio Report\n")
        file.write("======================\n")
        for stock, qty in portfolio.items():
            value = qty * stock_prices[stock]
            file.write(f"{stock} - {qty} shares x ₹{stock_prices[stock]} = ₹{value}\n")
        file.write(f"\nTotal Investment: ₹{total_value}\n")
    print("✅ Report saved as 'stock_portfolio_report.txt'.")

print("\n✅ Task Completed Successfully!")
