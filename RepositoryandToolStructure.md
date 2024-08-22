# Project Structure
```
Project_Root/
├── core.py
│ ├── ConstantProductAMM
│ │ ├── **init** ()
│ │ ├── get_price()
│ │ ├── swap_x_for_y()
│ │ ├── swap_y_for_x()
│ │ └── update_lp_percentage()
│
├── unitaryBuySellSim.py
│ ├── SwapSimulator
│ │ ├── **init** ()
│ │ ├── simulate_buy()
│ │ ├── simulate_sell()
│ │ └── _apply_swap_logic()
│
├── fullBuySellSim.py
│ ├── FullSwapSimulator
│ │ ├── **init** ()
│ │ ├── simulate_fixed_total_amount()
│ │ ├── simulate_fixed_transaction_count()
│ │ └── _apply_full_simulation_logic()
│
└── toMarketCapSim.py
├── MarketCapSimulator
│ ├── **init** ()
│ ├── calculate_market_cap()
│ ├── simulate_to_market_cap()
│ ├── _calculate_price_impact()
│ └── _adjust_for_liquidity_changes()

```markdown
# Explanation of the Structure

## Project Root
Contains the main Python files.

- **core.py**: Contains the core logic for the AMM (Automated Market Maker).
- **unitaryBuySellSim.py**: Handles simulations for individual buy and sell operations.
- **fullBuySellSim.py**: Extends the logic to simulate multiple trades and their cumulative effects.
- **toMarketCapSim.py**: Focuses on simulating the impact of trades on market capitalization.

## Mapping of Functions

### `core.py`
- **ConstantProductAMM Class**:
  - **`__init__()`**: Initializes the AMM with given liquidity pool values.
  - **`get_price()`**: Returns the current price based on the liquidity pool's state.
  - **`swap_x_for_y()`**: Simulates swapping the paired asset for tokens.
  - **`swap_y_for_x()`**: Simulates swapping tokens for the paired asset.
  - **`update_lp_percentage()`**: Updates the liquidity pool percentage after each transaction.

### `unitaryBuySellSim.py`
- **SwapSimulator Class**:
  - **`__init__()`**: Initializes the simulator with a given AMM instance.
  - **`simulate_buy()`**: Simulates a buy operation for a specified amount of the paired asset.
  - **`simulate_sell()`**: Simulates a sell operation for a specified number of tokens.
  - **`_apply_swap_logic()`**: Internal function that applies the swap logic based on the transaction type.

### `fullBuySellSim.py`
- **FullSwapSimulator Class**:
  - **`__init__()`**: Initializes the simulator for full buy/sell simulations.
  - **`simulate_fixed_total_amount()`**: Simulates a series of transactions with a fixed total amount.
  - **`simulate_fixed_transaction_count()`**: Simulates a fixed number of transactions.
  - **`_apply_full_simulation_logic()`**: Internal function to handle the logic for cumulative simulations.

### `toMarketCapSim.py`
- **MarketCapSimulator Class**:
  - **`__init__()`**: Initializes the market cap simulator with AMM parameters.
  - **`calculate_market_cap()`**: Calculates the current market cap based on the token price and supply.
  - **`simulate_to_market_cap()`**: Simulates the trades needed to reach a specific market cap.
  - **`_calculate_price_impact()`**: Internal function to calculate the price impact of trades.
  - **`_adjust_for_liquidity_changes()`**: Internal function to adjust calculations based on liquidity changes.
```
