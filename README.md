# Analysis of Random Number Generation Methods

**Author**: Alejandro Santiago Baca Eyssautier

---

## Overview

This Python project is a detailed exploration of different random number generation methods, including both theoretical and empirical analyses of their behavior and effectiveness. The project evaluates the performance of the **Middle-Square Method** and **Linear Congruential Generators (LCGs)**, two foundational techniques in the field of pseudorandom number generation (PRNG). The primary focus is to investigate their randomness, limitations, and potential biases in number generation through statistical analysis and graphical representations.

The project's key objectives are:

- To understand the workings of these methods and the mathematical principles behind them.
- To assess the randomness and distribution of numbers produced by these methods using correlation analysis and graphical plots.
- To identify limitations, such as cyclical behaviors or inherent biases in these algorithms.

The analysis of these algorithms includes detailed mathematical formulations and their applications, making this project suitable for both academic study and practical implementation in stochastic optimization or random sampling tasks.

---

## Methods and Mathematical Concepts

### 1. **Middle-Square Method**

The **Middle-Square Method** is a simple random number generation algorithm proposed by John von Neumann in 1949. It works by squaring a number and extracting the middle digits to produce the next number in the sequence. However, it suffers from several limitations, especially when the sequence includes a number whose most significant digits are zero. This can lead to degeneracy where numbers shrink rapidly, eventually reaching zero.

#### Mathematical Formulation

Given a number `X_i` with `2n` digits, the next number is generated as:

$$ X_{i+1} = \text{middle}_{2n}(X_i^2) $$

#### Disadvantages

- If the number contains zeros in its most significant digits, the successive numbers become smaller, eventually collapsing to zero. This is an inherent issue of the algorithm, which limits its use for long random sequences.

### 2. **Linear Congruential Generator (LCG)**

The **Linear Congruential Generator** is one of the most well-known PRNG methods. It generates a sequence of numbers using the following recurrence relation:

$$ X_{n+1} = (a \cdot X_n + c) \mod m $$

Where:

- `a` is the multiplier,
- `c` is the increment,
- `m` is the modulus,
- `X_0` is the seed or initial value.

#### Key Mathematical Properties

- **Correlation**: The algorithm's randomness is highly dependent on the values of `a`, `c`, and `m`. Certain combinations can lead to patterns in the number sequences, reducing randomness.
- **Periodicity**: The method exhibits periodic behavior, especially when poor parameter choices result in short cycles where sequences repeat.

---

## Randomness Analysis and Correlation Tests

The project includes multiple steps to test the randomness of the generated sequences:

### 1.**Middle-Square Method**

- For initial seeds, the project explores how quickly the sequence degenerates to zero.
- We generate sequences of random numbers and analyze their behavior using correlation tests to determine how independent each number is from the previous one.

### 2.**Linear Congruential Generator (LCG)**

- We generate 500 random numbers using two sets of parameters: `a = 17` and `a = 85` with `m = 2^{13} - 1`.
- **Correlation**: Successive pairs of numbers (`x_i` and `x_{i+1}`) are plotted to observe patterns and lines, revealing the degree of randomness. A similar test is conducted for `x_i` and `x_{i+2}`.

### Results

- With `a = 17`, the points align on 17 straight lines, suggesting structural dependency and reduced randomness.
- With `a = 85`, the correlation is weaker, indicating better randomization.
  
---

## Graphical Representations

### 1.**Scatter Plots**

Scatter plots of successive pairs (`x_i` vs. `x_{i+1}`) and non-successive pairs (`x_i` vs. `x_{i+2}`) reveal the underlying structure of the random number sequences.

### 2. **Correlation Analysis**

Using **NumPy’s correlation coefficient**, we calculate the strength of correlation between successive and non-successive pairs. The correlations provide a numerical measure of the randomness of the generated sequences.

---

## Applications

This project has practical applications in fields such as:

- **Stochastic Optimization**: Where random sampling is crucial for finding optimal solutions in uncertain environments.
- **Monte Carlo Simulations**: Where random number generation is fundamental to simulating random processes or systems.
- **Cryptography**: Although not suitable for modern cryptographic purposes, the study of PRNG methods highlights the importance of randomness and periodicity in securing cryptographic systems.

---

## Conclusion

This project provides a comprehensive analysis of two classical random number generation techniques. Through mathematical formulation, empirical testing, and graphical visualization, we explore the limitations and patterns inherent in the **Middle-Square Method** and **Linear Congruential Generators**. The findings reveal that certain parameter choices can introduce unwanted patterns, reducing the quality of randomness. The analysis underscores the need for careful parameter selection and method choice in applications requiring high-quality random sequences.

The project concludes with a demonstration of how random number generators can deviate from true randomness, reinforcing the importance of thorough testing in PRNG implementation.

---

## Dependencies

The following libraries are required for this project:

- **NumPy**: For efficient numerical operations, such as squaring large numbers and performing modular arithmetic.
- **Matplotlib**: For visualizing the correlations and patterns in the generated number sequences.
- **Warnings**: To suppress unnecessary runtime warnings during the execution of the script.
