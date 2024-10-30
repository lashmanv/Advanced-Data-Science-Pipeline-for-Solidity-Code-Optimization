# Solidity Code Optimization with Data Science Pipeline

This project provides a data science-driven framework for optimizing gas usage in Solidity smart contracts. Using tools like Brownie for Ethereum interactions, along with `pandas` and `scikit-learn`, this framework identifies functions with high gas usage, predicts gas consumption based on input patterns, and recommends targeted optimizations.

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [Workflow](#workflow)
- [Optimization Suggestions](#optimization-suggestions)
- [Results and Analysis](#results-and-analysis)
- [License](#license)

## Installation

1. **Clone the Repository**
    ```bash
    git clone https://github.com/lashmanv/Advanced-Data-Science-Pipeline-for-Solidity-Code-Optimization.git
    cd Advanced-Data-Science-Pipeline-for-Solidity-Code-Optimization
    ```

2. **Install Required Libraries**

    Install Python dependencies:
    ```bash
    pip install pandas scikit-learn brownie
    ```

3. **Set Up Ethereum Test Network**

    Install and set up Ganache or Hardhat to deploy contracts locally for gas testing:
    ```bash
    npm install -g ganache
    ganache-cli  # Run on default port 8545
    ```

4. **Compile and Deploy Contract**

    Ensure your Solidity contract (e.g., `MyContract.sol`) is in the `contracts` folder. Update the file path in the code to match your setup.

## Usage

1. **Run the Script**: The main optimization pipeline can be run by executing the script in Python.
    ```bash
    python optimize_solidity.py
    ```

2. **View Results**: Gas usage data and optimization suggestions will be output to the console. Key performance metrics for the gas prediction models will also be displayed.

## Workflow

### 1. Measure Gas Usage
The script connects to the Ethereum test network, loads the contract, and calls each function with test parameters to measure gas usage.

### 2. Data Collection and Analysis
Collected data is stored in a Pandas DataFrame, with metrics such as gas usage, input size, and loop counts. This data is then split into training and testing sets for model training.

### 3. Predictive Modeling
Regression models (`LinearRegression` and `RandomForestRegressor`) predict gas consumption based on inputs to identify functions with high gas costs.

### 4. Optimization Suggestions
High gas functions are flagged for optimization, with example suggestions for reducing gas usage.

## Optimization Suggestions

The framework provides common optimization tips for Solidity, such as:
- **Using mappings instead of arrays** for cheaper storage if random access isn’t required.
- **Storing repetitive calculations in memory** for reduced gas consumption.
- **Reducing loop usage on-chain** where possible.

## Results and Analysis

Upon execution, the model outputs:
- **R² Scores**: Indicating model accuracy in predicting gas usage.
- **High Gas Functions**: Identified functions with high predicted gas consumption.
- **Optimization Suggestions**: Targeted tips to reduce gas costs for flagged functions.

### Example Output

```
Linear Regression R2 Score: 0.78
Random Forest R2 Score: 0.90

Functions with High Gas Usage:
function_name | gas_used | predicted_gas
----------------------------------------
storeValue    | 30000    | 32000
addToArray    | 45000    | 47000

Optimization for storeValue: Consider storing values in memory for reduced access time
Optimization for addToArray: Use mappings instead of arrays if random access is not required
```

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for more details.
