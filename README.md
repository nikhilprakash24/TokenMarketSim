
TokenMarketSim - The Token and AMM (DEX) Simulation Tool Suite
Executive Summary
TokenMarketSim is a pioneering Python-based tool suite designed to simulate and analyze the intricate dynamics of tokens within Automated Market Makers (AMMs), particularly in decentralized exchanges (DEXs). By focusing on the often-overlooked Liquidity Pool (LP) percentage, TokenMarketSim offers unparalleled insights into price volatility, trade impact, and market cap changes, filling a critical gap in the existing toolkit landscape. The suite empowers traders, liquidity providers, and researchers with granular control over simulations, enabling precise analysis and strategic decision-making in the fast-paced world of decentralized finance (DeFi).

Layman's Summary
TokenMarketSim is like a crystal ball for the world of cryptocurrency trading on decentralized platforms. It helps you see what might happen to a token's price if people start buying or selling in large amounts. The tool is particularly useful because it focuses on something crucial: how much of a token is sitting in the liquidity pool. This is important because the more tokens in the pool, the less the price changes when people trade. With TokenMarketSim, you can simulate all sorts of trading scenarios, helping you make better decisions in the unpredictable world of crypto.

Technical Summary
TokenMarketSim is a comprehensive simulation toolkit built to model the behavior of tokens within AMMs on decentralized exchanges. It leverages the constant product formula, 
𝑥
×
𝑦
=
𝑘
x×y=k, to simulate how trades affect token prices and liquidity. The suite provides granular control over key parameters, such as transaction step size and LP percentage, allowing users to simulate complex trading scenarios with high precision. By integrating core AMM logic with advanced market cap simulations and detailed buy/sell operation analyses, TokenMarketSim is a powerful tool for anyone needing to understand the intricate mechanics of token pricing and liquidity management in DeFi environments.

Introduction
Welcome to TokenMarketSim, the ultimate tool suite for simulating and analyzing token dynamics within Automated Market Makers (AMMs) on decentralized exchanges. In the wild west of DeFi, where markets are unpredictable and liquidity is king, understanding the impact of trades on token prices is both an art and a science. TokenMarketSim is your brush and canvas, allowing you to paint detailed scenarios and see how the story unfolds.

Why settle for guesswork when you can simulate your strategies, understand the ripple effects of your trades, and optimize your moves like a pro? Whether you're a trader trying to predict the next big price swing, a liquidity provider looking to maximize returns, or a researcher aiming to crack the code of decentralized markets, TokenMarketSim is designed with you in mind. With a focus on the crucial yet often neglected LP percentage, our tool suite provides insights that standard models overlook, offering you the edge in a competitive and rapidly evolving landscape.

So, put on your scientist's hat—or your cowboy boots—and let's dive into the numbers with TokenMarketSim!

Key Insights from Base Case Examples
During our extensive testing and simulations, several key insights emerged that highlight the importance of using TokenMarketSim for understanding AMM dynamics:

Granularity Matters: When simulating large trades, breaking them down into smaller, more granular steps significantly improves the accuracy of price predictions. Large, single-step trades often fail to capture the true impact on price, particularly when aiming for significant market cap increases.

LP Percentage Sensitivity: The LP percentage plays a critical role in determining the volatility of a token’s price. Lower LP percentages lead to greater price sensitivity, meaning even small trades can result in significant price shifts. Conversely, higher LP percentages stabilize the token’s price but require larger trades to achieve noticeable price changes.

Market Cap Projections: Simulating the journey from one market cap to another is complex, especially when considering multiple transactions. The simulations demonstrated that step-by-step increases allow for more accurate predictions of how much capital is needed to reach a desired market cap, making TokenMarketSim invaluable for strategic planning in DeFi.

Trade Size Impact: The toolkit’s ability to simulate varying trade sizes provided deep insights into how different trade amounts influence price movement. Smaller trades in larger LPs create minimal price changes, while larger trades or smaller LPs result in more volatile price adjustments.

Detailed Features
Core AMM Logic (core.py)
The heart of TokenMarketSim lies in its core AMM logic, implemented in core.py. Here, the ConstantProductAMM class encapsulates the fundamental mechanics of an AMM using the constant product formula 
𝑥
×
𝑦
=
𝑘
x×y=k. This file provides the foundation upon which all other simulations are built.

Key Attributes:

token_in_lp: The quantity of the token currently held in the liquidity pool.
paired_asset_in_lp: The quantity of the paired asset (e.g., ETH, USDT) held in the liquidity pool.
k: The constant product value, ensuring that the product of the token amount and paired asset remains constant after each trade.
Key Methods:

get_price(): Calculates and returns the current token price based on the ratio of the paired asset to the token in the liquidity pool.
swap_x_for_y(amount_x): Simulates the process of exchanging a given amount of the paired asset for tokens, adjusting the liquidity pool and price accordingly.
swap_y_for_x(amount_y): Simulates the process of exchanging a given amount of tokens for the paired asset, adjusting the liquidity pool and price.
add_liquidity(amount_x, amount_y): Adds liquidity to the pool, increasing both the token and paired asset amounts proportionally.
remove_liquidity(percentage): Removes a specified percentage of liquidity from the pool, decreasing the amounts of both the token and paired asset.
get_pool_state(): Returns a comprehensive snapshot of the pool's current state, including token amounts, the constant product value (k), the token price, and the LP percentage.
Simulating Buy and Sell Operations (unitaryBuySellSim.py)
This module builds on the core logic, allowing users to simulate individual buy and sell operations with precision. The SwapSimulator class provides methods to model how a single trade impacts the liquidity pool and token price.

SwapSimulator Class:

simulate_buy(amount_x): Simulates a buy operation where a specified amount of the paired asset is exchanged for tokens. The method returns the updated state of the liquidity pool after the transaction.
simulate_sell(amount_y): Simulates a sell operation where a specified amount of tokens is exchanged for the paired asset. The method returns the updated pool state, reflecting the new balance and price.
Handling Complex Trade Scenarios (fullBuySellSim.py)
For users who need to simulate more complex trading scenarios involving multiple transactions, fullBuySellSim.py offers advanced capabilities. The FullSwapSimulator class is designed to handle a series of buy or sell operations, providing detailed analysis on how cumulative trades affect the market.

FullSwapSimulator Class:

simulate_fixed_total_amount(num_transactions, total_amount, is_buy): Simulates a sequence of buy or sell operations where the total amount of the paired asset or token is fixed. The method returns the pool states after each transaction, along with the size of each individual trade.
simulate_fixed_transaction_count(num_transactions, amount_per_transaction, is_buy): Simulates a series of transactions with a fixed amount per trade. This method is ideal for modeling regular trading activities and observing their cumulative impact.
Market Cap Impact Simulations (toMarketCapSim.py)
The toMarketCapSim.py module extends the functionality of TokenMarketSim by simulating the impact of trades on a token's market capitalization. This advanced feature is particularly useful for understanding how large-scale trades or market shifts affect the broader financial metrics of a token.

MarketCapSimulator Class:

calculate_circulating_supply(total_supply, burned_tokens): Calculates the circulating supply of a token by subtracting burned tokens from the total supply.
simulate_to_market_cap(current_market_cap, desired_market_cap, total_supply, paired_asset_in_lp, step_size, is_buy): Simulates the sequence of trades required to achieve a desired market cap from a current market cap. The simulation takes into account the LP percentage, trade size, and other relevant parameters.
Installation and Setup
To get started with TokenMarketSim, follow these steps:

Clone the repository:

bash
Copy code
git clone https://github.com/yourusername/amm-simulation-toolkit.git
cd amm-simulation-toolkit
Run the example scripts:

Navigate to the directory where the example scripts are located and run them using Python:

bash
Copy code
python toMarketCapSim.py
Usage Examples
Example 1: Simulate a Single Buy Operation
python
Copy code
from core import ConstantProductAMM
from unitaryBuySellSim import SwapSimulator

amm = ConstantProductAMM(1000.0, 50000.0)  # 1000 tokens in LP, paired with $50,000 worth of ETH
simulator = SwapSimulator(amm)

result = simulator.simulate_buy(100)  # Simulate buying $100 worth of the token
print("After Buy:", result)
Example 2: Simulate a Market Cap Increase
python
Copy code
from toMarketCapSim import MarketCapSimulator
from core import ConstantProductAMM

amm = ConstantProductAMM(1000.0, 50000.0)  # 1000 tokens in LP, paired with $50,000 worth of ETH
market_cap_simulator = MarketCapSimulator(amm)

result = market_cap_simulator.simulate_to_market_cap(
    current_market_cap=450000, 
    desired_market_cap=900000, 
    total_supply=1000000, 
    paired_asset_in_lp=50000.0, 
    step_size=100, 
    is_buy=True
)
print("Market Cap Simulation Result:", result)
Example 3: Simulate Multiple Buys to Double Market Cap
python
Copy code
from toMarketCapSim import MarketCapSimulator
from core import ConstantProductAMM

amm = ConstantProductAMM(500.0, 10000.0)  # Smaller LP to observe higher volatility
market_cap_simulator = MarketCapSimulator(amm)

result = market_cap_simulator.simulate_to_market_cap(
    current_market_cap=20000, 
    desired_market_cap=40000, 
    total_supply=1000000, 
    paired_asset_in_lp=10000.0, 
    step_size=50, 
    is_buy=True
)
print("Market Cap Simulation Result:", result)
Example 4: Simulate a Series of Sells Impacting Market Cap
python
Copy code
from toMarketCapSim import MarketCapSimulator
from core import ConstantProductAMM

amm = ConstantProductAMM(2000.0, 50000.0)  # Larger LP to observe stable price impact
market_cap_simulator = MarketCapSimulator(amm)

result = market_cap_simulator.simulate_to_market_cap(
    current_market_cap=100000, 
    desired_market_cap=50000, 
    total_supply=1000000, 
    paired_asset_in_lp=50000.0, 
    step_size=100, 
    is_buy=False
)
print("Market Cap Simulation Result:", result)
Example 5: Simulate Fixed Transaction Counts for Buys
python
Copy code
from fullBuySellSim import FullSwapSimulator
from core import ConstantProductAMM

amm = ConstantProductAMM(1500.0, 30000.0)
full_simulator = FullSwapSimulator(amm)

result = full_simulator.simulate_fixed_transaction_count(
    num_transactions=10, 
    amount_per_transaction=100, 
    is_buy=True
)
for idx, state in enumerate(result):
    print(f"After Buy {idx+1}: {state}")
Example 6: Simulate Fixed Transaction Counts for Sells
python
Copy code
from fullBuySellSim import FullSwapSimulator
from core import ConstantProductAMM

amm = ConstantProductAMM(1500.0, 30000.0)
full_simulator = FullSwapSimulator(amm)

result = full_simulator.simulate_fixed_transaction_count(
    num_transactions=10, 
    amount_per_transaction=100, 
    is_buy=False
)
for idx, state in enumerate(result):
    print(f"After Sell {idx+1}: {state}")
Example 7: Granular Simulation of a Large Buy
python
Copy code
from fullBuySellSim import FullSwapSimulator
from core import ConstantProductAMM

amm = ConstantProductAMM(1000.0, 50000.0)
full_simulator = FullSwapSimulator(amm)

result = full_simulator.simulate_fixed_total_amount(
    num_transactions=50, 
    total_amount=5000, 
    is_buy=True
)
for idx, state in enumerate(result):
    print(f"After Buy {idx+1}: {state}")
Example 8: Large Step Simulation to Illustrate Price Caps
python
Copy code
from fullBuySellSim import FullSwapSimulator
from core import ConstantProductAMM

amm = ConstantProductAMM(500.0, 25000.0)
full_simulator = FullSwapSimulator(amm)

result = full_simulator.simulate_fixed_total_amount(
    num_transactions=1, 
    total_amount=20000, 
    is_buy=True
)
print("After Large Buy:", result)
Example 9: Market Cap Simulation with Varied LP Percentages
python
Copy code
from toMarketCapSim import MarketCapSimulator
from core import ConstantProductAMM

amm_10_percent = ConstantProductAMM(100.0, 10000.0)  # 10% of total supply in LP
market_cap_simulator_10 = MarketCapSimulator(amm_10_percent)

amm_25_percent = ConstantProductAMM(250.0, 10000.0)  # 25% of total supply in LP
market_cap_simulator_25 = MarketCapSimulator(amm_25_percent)

result_10 = market_cap_simulator_10.simulate_to_market_cap(
    current_market_cap=20000, 
    desired_market_cap=40000, 
    total_supply=1000, 
    paired_asset_in_lp=10000.0, 
    step_size=10, 
    is_buy=True
)
result_25 = market_cap_simulator_25.simulate_to_market_cap(
    current_market_cap=20000, 
    desired_market_cap=40000, 
    total_supply=1000, 
    paired_asset_in_lp=10000.0, 
    step_size=10, 
    is_buy=True
)
print("Market Cap Simulation (10% LP):", result_10)
print("Market Cap Simulation (25% LP):", result_25)
Example 10: Sensitivity Analysis on Trade Size
python
Copy code
from toMarketCapSim import MarketCapSimulator
from core import ConstantProductAMM

amm = ConstantProductAMM(2000.0, 100000.0)
market_cap_simulator = MarketCapSimulator(amm)

result_small = market_cap_simulator.simulate_to_market_cap(
    current_market_cap=100000, 
    desired_market_cap=110000, 
    total_supply=1000000, 
    paired_asset_in_lp=100000.0, 
    step_size=100, 
    is_buy=True
)
result_large = market_cap_simulator.simulate_to_market_cap(
    current_market_cap=100000, 
    desired_market_cap=110000, 
    total_supply=1000000, 
    paired_asset_in_lp=100000.0, 
    step_size=5000, 
    is_buy=True
)
print("Small Step Size Simulation:", result_small)
print("Large Step Size Simulation:", result_large)
Future Enhancements
While TokenMarketSim is already a powerful tool, we have exciting plans for further enhancements:

Impermanent Loss Calculation: We aim to incorporate calculations for impermanent loss, providing liquidity providers with insights into potential losses due to market fluctuations.
Dynamic Fee Structures: Implementing variable fee structures based on trade size or market conditions will further refine the simulation accuracy.
Real-Time Data Integration: Extending the toolkit to fetch real-time price data from oracles will enable simulations based on current market conditions, making TokenMarketSim even more applicable to live trading environments.
Web Application Interface: To make the toolkit more accessible, we plan to develop a frontend web application that allows users to interact with the simulations without needing to run scripts. This will broaden the toolkit’s usability, attracting a wider range of users who prefer web-based interfaces.
Sources
Uniswap V2 Core Smart Contract Documentation
“Automated Market Makers: Constant Function Market Makers Explained” by Binance Academy
“Understanding Liquidity Pools” by Ethereum Foundation
Contributions
We welcome contributions from the community! If you'd like to contribute, please fork the repository, create a new branch, and submit a pull request. Whether it's adding new features, improving existing code, or refining documentation, your input is valuable.

License
This project is licensed under the MIT License. For more details, see the LICENSE file in the repository.

Contact
For any questions or inquiries, feel free to reach out at yourname@yourdomain.com. We're always happy to help and discuss potential collaborations!

Next Steps
Upload the Files to GitHub:

Commit the latest set of files to your GitHub repository, ensuring all updates and corrections are included.
Unit Testing:

Conduct comprehensive unit tests to verify the functionality of the toolkit. After testing, update the README with the results and any necessary revisions.
Documentation Enhancement:

Update the README and other documentation with insights from the unit tests. Ensure all features are thoroughly documented, and consider adding more detailed usage examples.
Web Application Development:

Begin development of a frontend web application that will allow users to interact with the toolkit’s simulations through a user-friendly interface.
Community Engagement:

Promote the toolkit within relevant communities, encouraging feedback and contributions to refine and expand TokenMarketSim's capabilities.
