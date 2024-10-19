# Simplified Shamir's Secret Sharing Algorithm

## Project Overview

This program implements a simplified version of **Shamir's Secret Sharing algorithm**. It uses Lagrange interpolation to calculate the constant term of a polynomial, based on a set of points provided in JSON format. The y-values of these points are encoded in different numerical bases, and the program decodes and processes these values to find the secret.

## Steps the Program Takes

### 1. Read the JSON Input

The program receives the input in JSON format, which contains information such as:
- **n**: Total number of points.
- **k**: Minimum number of points needed to determine the polynomial.
- Each point consists of:
  - A number representing the **x value** (the position of the point).
  - A **base**, which tells how the y-value is encoded.
  - The **value**, which is the encoded y-value.

### 2. Convert the Encoded Values

The y-values provided in the JSON are encoded in different bases. The program converts each value into base 10 using the provided base. For example:
- If the value is `"111"` in base 2, it will be converted to `7` in base 10.
- If the value is `"213"` in base 4, it will be converted to `39` in base 10.

This conversion results in pairs of x and y values like:
- (1, 4)
- (2, 7)
- and so on.

### 3. Use Lagrange Interpolation

Once the x and y pairs are obtained, the program uses **Lagrange Interpolation** to calculate the constant term of the polynomial. Lagrange interpolation is a mathematical method that allows us to compute the value of the polynomial at any point, given several known points. 

In this case, the program calculates the value of the polynomial at **x = 0**, which gives us the constant term, denoted as **f(0)**.

### 4. Print the Result

After calculating the constant term using interpolation, the program prints the result, which is the **secret**.

## Example

### Sample Input:

```json
{
  "keys": {
    "n": 4,
    "k": 3
  },
  "1": {
    "base": "10",
    "value": "4"
  },
  "2": {
    "base": "2",
    "value": "111"
  },
  "3": {
    "base": "10",
    "value": "12"
  },
  "6": {
    "base": "4",
    "value": "213"
  }
}
