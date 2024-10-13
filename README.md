# TOPSIS Implementation for Pretrained Models

This repository contains a Python implementation of the Technique for Order of Preference by Similarity to Ideal Solution (TOPSIS) method for multi-criteria decision-making, specifically designed for evaluating pretrained models based on various performance metrics.

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
python main.py <input_file> <weights> <impacts> <output_file>
```

### Parameters:
- `<input_file>`: Path to the input CSV file containing the data of pretrained models.
- `<weights>`: Comma-separated weights for each metric (7 metrics total).
- `<impacts>`: Comma-separated impacts for each metric (use `+` for maximization, `-` for minimization).
- `<output_file>`: Path to save the output CSV file containing the ranking results.

## Input Format

The input CSV file should contain the following columns:

- `Text`: Descriptive text for each alternative.
- `Models`: Names of the pretrained models being evaluated.
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
T1,M1,0.874824242,0.86397102,0.866292063,0.787965132,0.800558851,0.307478073,43.51307945
T1,M2,0.782911707,0.867429751,0.798649873,0.710205397,0.391623313,0.348639973,49.03517235
T1,M3,0.942434754,0.809224629,0.967893125,0.746601719,0.601112492,0.905180709,27.17225883
T1,M4,0.840798193,0.933295791,0.841402636,0.717565508,0.1784601,0.151815711,36.50223168
T2,M1,0.77146663,0.691751002,0.796855844,0.879122367,0.579905838,0.531860097,47.77962214
T2,M2,0.94949699,0.83928956,0.667346702,0.679191417,0.804303887,0.868645004,38.69904406
T2,M3,0.7593,0.68929,0.75686,0.64329,0.58999,0.858594,44.75962
T2,M4,0.807365646,0.861118265,0.621799757,0.674585067,0.883719322,0.945757611,28.66920061
T3,M1,0.78789097,0.937625792,0.666929863,0.808062334,0.513732773,0.854395162,13.98813745
T3,M2,0.903664546,0.799158839,0.678174898,0.967411043,0.353994712,0.224380606,46.64783135
T3,M3,0.75363,0.68699,0.73686,0.64329,0.58999,0.858594,44.75962
T3,M4,0.843937973,0.861311924,0.781525739,0.718820799,0.991019686,0.614104438,40.82035939
T4,M1,0.969755765,0.905344473,0.972856729,0.639753161,0.281571792,0.393740442,16.75167982
T4,M2,0.93532879,0.677662824,0.877676776,0.780456701,0.766463053,0.222599902,13.32805894
T4,M3,0.75363,0.68699,0.73686,0.64329,0.58999,0.858594,44.75962
T4,M4,0.736747799,0.634274056,0.708427036,0.893754862,0.636450759,0.948835609,31.8981984
T5,M1,0.711851408,0.620463311,0.616297724,0.816825026,0.5081015,0.821914174,22.98044425
T5,M2,0.982713191,0.752502632,0.973967421,0.836746931,0.376125953,0.53481296,42.25650894
T5,M3,0.732142276,0.602357268,0.662849807,0.780011661,0.584109712,0.74043356,27.43155177
T5,M4,0.756738216,0.874037423,0.796287063,0.698088531,0.181579448,0.168143716,30.10110621
```

## Output Format

The output CSV file will contain the following columns:

- `Text`: Descriptive text for each alternative.
- `Models`: Names of the pretrained models being evaluated.
- Metrics: The metrics used for evaluation.
- `Performance_Score`: The performance score calculated by TOPSIS.
- `Rank`: The rank of each alternative based on the performance score.

### Example of an Output CSV file (output.csv):

```csv
Text,Models,Accuracy,Precision,Recall,F1 Score,BLEU Score,ROUGE Score,Perplexity,Performance_Score,Rank
T1,M1,0.874824242,0.86397102,0.866292063,0.787965132,0.800558851,0.307478073,43.51307945,0.745,1
T1,M2,0.782911707,0.867429751,0.798649873,0.710205397,0.391623313,0.348639973,49.03517235,0.651,3
T1,M3,0.942434754,0.809224629,0.967893125,0.746601719,0.601112492,0.905180709,27.17225883,0.863,2
T1,M4,0.840798193,0.933295791,0.841402636,0.717565508,0.1784601,0.151815711,36.50223168,0.700,4
...
```

## Sample Input and Output

### Sample Command:

```bash
python main.py input.csv "0.3,0.2,0.2,0.1,0.1,0.05,0.05" "+,+,+,+,+,+,-" output.csv
```

### Sample Output:

After running the command, the `output.csv` file will contain the calculated performance scores and ranks based on the provided weights and impacts.

## License

This project is licensed under the MIT License. See the LICENSE file for more details.


