# Higher Order Functions Project

This project involves creating higher-order functions to process data from a CSV file. The functions created will be used to count occurrences and compute averages in a functional programming style.

## Project Overview

You will create two higher-order functions and use them to process sales data from a CSV file named `1kSalesRec.csv`.

### Functions to Implement

1. **count()**: Returns the frequency of an element in an iterable.
    - **Parameters**:
      - `predicate`: A function that, when evaluated to True, increments a counter by one.
      - `itr`: The collection containing the element of interest.
      
2. **average()**: Returns the average of elements in an iterable of numbers.
    - **Parameter**:
      - `itr`: The collection to be averaged.

The `count()` function is a special type of `filter()` function that returns the number of occurrences of an element instead of returning a Boolean value. The `average()` function will compute the arithmetic mean of a collection recursively to adhere to functional programming principles.

### Example Usage

You will use these functions to process sales data from a CSV file called `1kSalesRec.csv`.

## Getting Started

### Prerequisites

- Python 3.6 or higher
- Pandas library

### Installing

1. Clone the repository:

    ```bash
    git clone https://github.com/your-username/higher-order-functions.git
    cd higher-order-functions
    ```

2. Install the required library:

    ```bash
    pip install pandas
    ```

### Running the Project

1. Implement the `count()` function:

    ```python
    from functools import reduce
    
    def count(predicate, itr):
        return reduce(lambda acc, x: acc + 1 if predicate(x) else acc, itr, 0)
    ```

2. Implement the `average()` function recursively:

    ```python
    def average(itr):
        if len(itr) == 1:
            return itr[0]
        else:
            return (itr[0] + average(itr[1:]) * (len(itr) - 1)) / len(itr)
    ```

3. Process the sales data:

    ```python
    import pandas as pd

    # Load the sales data
    df = pd.read_csv('1kSalesRec.csv')

    # Example usage of count()
    num_sales_over_1000 = count(lambda x: x > 1000, df['Item Cost'])
    print(f"Number of sales over $1000: {num_sales_over_1000}")

    # Example usage of average()
    avg_sales = average(df['Item Cost'].tolist())
    print(f"Average sales cost: {avg_sales}")
    ```

## Authors

- **Your Name** - [your-username](https://github.com/your-username)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.
