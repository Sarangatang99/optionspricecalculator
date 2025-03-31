# optionspricecalculator
def options_profit_loss(trade_type, strike_price, premium_paid, contracts, expiry_price):
    """
    General Options Profit/Loss Calculator.
    
    Parameters:
    trade_type (str): 'call' or 'put' indicating the option type.
    strike_price (float): Strike price of the option.
    premium_paid (float): Premium paid per contract.
    contracts (int): Number of contracts traded.
    expiry_price (float): Underlying asset price at expiration.
    
    Returns:
    float: Total profit/loss in dollars.
    """
    
    if trade_type.lower() == 'call':
        intrinsic_value = max(expiry_price - strike_price, 0)
    elif trade_type.lower() == 'put':
        intrinsic_value = max(strike_price - expiry_price, 0)
    else:
        raise ValueError("Invalid trade type. Use 'call' or 'put'.")
    
    profit_loss_per_contract = intrinsic_value - premium_paid
    total_profit_loss = profit_loss_per_contract * contracts * 100
    
    return total_profit_loss

# Example usage
trade_type = 'call'  # 'call' or 'put'
strike_price = 50
premium_paid = 2.5
contracts = 10  # Example contract size
expiry_price = 55  # Example underlying price at expiration

profit_loss = options_profit_loss(trade_type, strike_price, premium_paid, contracts, expiry_price)
print(f"Total Profit/Loss: ${profit_loss:.2f}")
