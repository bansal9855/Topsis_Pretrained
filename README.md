# TOPSIS Implementation

This repository contains a Python implementation of the Technique for Order of Preference by Similarity to Ideal Solution (TOPSIS) method for multi-criteria decision-making. The code evaluates and ranks alternatives based on various performance metrics.

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [Input Format](#input-format)
- [Output Format](#output-format)
- [Sample Input and Output](#sample-input-and-output)
- [License](#license)

## Installation

To run the TOPSIS script, you need to have Python 3.x installed along with the necessary libraries. You can install the required packages using pip:

```bash
pip install pandas numpy
```

## Usage

You can run the TOPSIS script from the command line using the following syntax:

```bash
python topsis.py <input_file> <weights> <impacts> <output_file>
```

### Parameters:
- `<input_file>`: Path to the input CSV file containing the data.
- `<weights>`: Comma-separated weights for each metric (7 metrics total).
- `<impacts>`: Comma-separated impacts for each metric (use `+` for maximization, `-` for minimization).
- `<output_file>`: Path to save the output CSV file containing the ranking results.

## Input Format

The input CSV file should contain the following columns:

- `Text`: Descriptive text for each alternative.
- `Models`: Names of the models being evaluated.
- Metrics: The following metrics are required (all must be numeric):
  - `Accuracy`
  - `Precision`
  - `Recall`
  - `F1 Score`
  - `BLEU Score`
  - `ROUGE Score`
  - `Perplexity`

### Example of an Input CSV file (input.csv):

```csv
Text,Models,Accuracy,Precision,Recall,F1 Score,BLEU Score,ROUGE Score,Perplexity
"Model A", "A1", 0.85, 0.80, 0.75, 0.78, 0.65, 0.70, 30.5
"Model B", "B1", 0.90, 0.85, 0.80, 0.83, 0.70, 0.75, 28.0
"Model C", "C1", 0.80, 0.75, 0.70, 0.73, 0.60, 0.65, 35.0
```

## Output Format

The output CSV file will contain the following columns:

- `Text`: Descriptive text for each alternative.
- `Models`: Names of the models being evaluated.
- Metrics: The metrics used for evaluation.
- `Performance_Score`: The performance score calculated by TOPSIS.
- `Rank`: The rank of each alternative based on the performance score.

### Example of an Output CSV file (output.csv):

```csv
Text,Models,Accuracy,Precision,Recall,F1 Score,BLEU Score,ROUGE Score,Perplexity,Performance_Score,Rank
"Model A", "A1", 0.85, 0.80, 0.75, 0.78, 0.65, 0.70, 30.5, 0.620, 2
"Model B", "B1", 0.90, 0.85, 0.80, 0.83, 0.70, 0.75, 28.0, 0.740, 1
"Model C", "C1", 0.80, 0.75, 0.70, 0.73, 0.60, 0.65, 35.0, 0.500, 3
```

## Sample Input and Output

### Sample Command:

```bash
python topsis.py input.csv "0.4,0.3,0.1,0.1,0.05,0.05,0.05" "+,+,+,+,+,+,-" output.csv
```

### Sample Output:

After running the command, the `output.csv` file will contain the calculated performance scores and ranks based on the provided weights and impacts.

## License

This project is licensed under the MIT License. See the LICENSE file for more details.
```

