# CodeAlpha_StockPortfolioTracker
# Stock Portfolio Tracker

# Step 1: Define hardcoded stock prices
stock_prices = {
    "AAPL": 180,
    "TSLA": 250,
    "GOOGL": 140,
    "AMZN": 130
}

# Step 2: Ask user for stock details
portfolio = {}

print("📈 Welcome to the Stock Portfolio Tracker!")
print("Enter your stock details. Type 'done' when finished.\n")

while True:
    stock = input("Stock symbol (e.g., AAPL): ").upper()
    if stock == "DONE":
        break
    if stock not in stock_prices:
        print("❌ Stock not found. Try again.")
        continue
    try:
        quantity = int(input(f"Quantity of {stock}: "))
        portfolio[stock] = portfolio.get(stock, 0) + quantity
    except ValueError:
        print("❌ Please enter a valid number.")

# Step 3: Calculate total investment
total_value = 0
print("\n📊 Portfolio Summary:")
for stock, qty in portfolio.items():
    price = stock_prices[stock]
    value = price * qty
    total_value += value
    print(f"{stock}: {qty} shares × ₹{price} = ₹{value}")

print(f"\n💰 Total Investment Value: ₹{total_value}")

# Step 4: Save to file (with UTF-8 encoding)
save = input("\nDo you want to save this summary to a file? (yes/no): ").lower()
if save == "yes":
    with open("portfolio_summary.txt", "w", encoding="utf-8") as file:
        for stock, qty in portfolio.items():
            price = stock_prices[stock]
            value = price * qty
            file.write(f"{stock}: {qty} shares × ₹{price} = ₹{value}\n")
        file.write(f"\nTotal Investment Value: ₹{total_value}")
    print("✅ Saved to 'portfolio_summary.txt'")
