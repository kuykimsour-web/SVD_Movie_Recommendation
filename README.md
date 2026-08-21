# SVD for Movie Recommendation Systems

## Project  --- Singular Value Decomposition (SVD) and Its Applications

### Project Topic

**Application of Singular Value Decomposition (SVD) in Movie
Recommendation Systems**

---

## 1. Project Overview

This project investigates how **Singular Value Decomposition (SVD)** can
be applied to a movie recommendation system.

The main idea is to represent movie ratings as a **User--Movie Rating
Matrix** and decompose that matrix using:

\[ A = U`\Sigma `{=tex}V\^T \]

SVD helps identify important hidden patterns in users' movie
preferences. By keeping the most important singular values, we can
construct a lower-rank approximation of the rating matrix and use it to
estimate users' preferences for movies they have not rated.

This project follows the requirements of Project II: choose an SVD
application other than image compression, perform analysis, plot
singular values and cumulative sum versus the rank (r), present the work
in class, and submit the presentation, Python code, and short PDF
report.

---

## 2. Research Question

> **How can SVD be applied to a movie-rating dataset to identify user
> preferences and generate personalized movie recommendations?**

### Supporting Research Questions

1. How does SVD decompose the user--movie rating matrix into meaningful
   components?
2. How does the choice of rank (r) affect the amount of information
   retained?
3. How effectively can an SVD-based model predict users' movie
   preferences?

---

## 3. Objectives

- Understand the mathematical concept of Singular Value Decomposition.
- Apply SVD to a real movie-rating dataset.
- Construct a User--Movie Rating Matrix.
- Analyze the singular values of the rating matrix.
- Study how different values of (r) affect information retention.
- Plot Singular Values versus (r).
- Plot Cumulative Sum versus (r).
- Use the SVD approximation to estimate movie preferences.
- Generate movie recommendations for users.
- Discuss the results, advantages, and limitations of the approach.

---

## 4. Mathematical Foundation

### 4.1 Singular Value Decomposition

For a matrix (A), SVD decomposes the matrix as:

\[ A = U`\Sigma `{=tex}V\^T \]

where:

- \(A\) = original User--Movie Rating Matrix
- \(U\) = left singular vectors
- (`\Sigma`{=tex}) = diagonal matrix containing singular values
- (V\^T) = transpose of the right singular-vector matrix

The singular values satisfy:

\[ `\sigma`{=tex}\_1 `\geq `{=tex}`\sigma`{=tex}\_2
`\geq `{=tex}`\cdots `{=tex}`\geq `{=tex}`\sigma`{=tex}\_p
`\geq 0`{=tex} \]

where (p = `\min`{=tex}(m,n)).

### 4.2 Low-Rank Approximation

Instead of using every singular value, we can keep only the first (r)
components:

\[ A_r = U_r`\Sigma`{=tex}\_rV_r\^T \]

This produces a lower-rank approximation of the original rating matrix.

The first singular values are generally the most important because they
represent the strongest patterns in the data.

### 4.3 Cumulative Information

The cumulative amount of information represented by the first (r)
singular values can be calculated as:

\[ E(r)= `\frac{\sum_{i=1}^{r}\sigma_i^2}`{=tex}
{`\sum`{=tex}\_{i=1}\^{p}`\sigma`{=tex}\_i\^2} \]

This helps determine an appropriate value of (r).

### 4.4 Recommendation

After reconstructing the rating matrix:

\[ `\hat{A}`{=tex}=U_r`\Sigma`{=tex}\_rV_r\^T \]

the estimated value (`\hat{A}`{=tex}\_{u,i}) represents the predicted
preference of user (u) for movie (i).

Movies that the user has not rated and have the highest predicted
ratings can be selected as recommendations.

---

## 5. Dataset

### MovieLens 100K

This project uses the **MovieLens 100K dataset**.

The main files used are:

- `u.data` --- movie ratings
- `u.item` --- movie information and movie titles

### Main Rating Data

The `u.data` file contains:

  Column        Description

---

  `user_id`     ID of the user
  `movie_id`    ID of the movie
  `rating`      User's rating
  `timestamp`   Time when the rating was given

The rating information is used to construct the User--Movie Rating
Matrix.

### Movie Information

The `u.item` file is used to connect movie IDs with movie titles and
other movie information.

---

## 6. Project Methodology

The project follows this workflow:

```text
MovieLens Dataset
       ↓
Data Preparation
       ↓
User–Movie Rating Matrix
       ↓
Singular Value Decomposition
       ↓
U, Σ, Vᵀ
       ↓
Analyze Singular Values
       ↓
Cumulative Information Analysis
       ↓
Choose Rank r
       ↓
Low-Rank Approximation
       ↓
Predict Missing Preferences
       ↓
Generate Movie Recommendations
       ↓
Evaluate and Discuss Results
```

---

## 7. Required Analysis

### 7.1 Singular Values vs. Rank (r)

A graph will be created to show how the singular values change as (r)
increases.

**Required graph:**

> Singular Values vs. (r)

The graph will help identify which components contain the most important
information.

### 7.2 Cumulative Sum vs. Rank (r)

A second graph will show how much information is retained as more
singular values are included.

**Required graph:**

> Cumulative Sum vs. (r)

This analysis will help determine a suitable value of (r).

---

## 8. Python Implementation

The main programming language for this project is **Python**.

Main libraries:

- NumPy
- Pandas
- Matplotlib

Basic SVD calculation:

```python
import numpy as np

U, S, VT = np.linalg.svd(A, full_matrices=False)
```

The actual analysis code will be developed in the project notebook.

---

## 9. Expected Results

The project will investigate:

- The distribution of singular values.
- How quickly cumulative information increases.
- A suitable value of (r).
- The quality of the low-rank approximation.
- Predicted ratings for movies a user has not rated.
- Personalized movie recommendations.

The final results will be based on the actual MovieLens data and will
not use manually invented values.

---

## 10. Evaluation

The project may compare predicted ratings with known ratings from a test
set.

Possible evaluation measures include:

### Mean Absolute Error (MAE)

\[ MAE = `\frac{1}{N}`{=tex} `\sum`{=tex}\_{i=1}\^{N}
\|r_i-`\hat{r}`{=tex}\_i\| \]

### Root Mean Squared Error (RMSE)

\[ RMSE = `\sqrt{ \frac{1}{N} \sum_{i=1}^{N} (r_i-\hat{r}_i)^2 }`{=tex} \]

Lower values indicate smaller prediction errors.

---

## 11. Project Deliverables

According to the project requirements, the final submission will
contain:

### 1. Presentation Slides

`SVD_Movie_Recommendation.pptx`

### 2. Python Code / Jupyter Notebook

`SVD_Movie_Recommendation.ipynb`

### 3. Short Report

`SVD_Movie_Recommendation_Report.pdf`

---

## 12. Project Structure

```text
SVD_Movie_Recommendation/
│
├── data/
│   ├── u.data
│   └── u.item
│
├── notebooks/
│   └── SVD_Movie_Recommendation.ipynb
│
├── figures/
│   ├── singular_values_vs_r.png
│   └── cumulative_sum_vs_r.png
│
│
└── README.md
```

---

## 13. Limitations

The project should discuss limitations such as:

- The rating matrix contains many missing ratings.
- Replacing missing ratings with zero can affect the SVD model.
- User preferences can change over time.
- Recommendations depend on the available rating data.
- A low-rank approximation may lose some information.
- SVD alone does not explain every factor influencing a user's movie
  choice.

---

## 14. Conclusion

This project applies Singular Value Decomposition to a real movie-rating
dataset to investigate hidden patterns in user preferences.

The analysis focuses on the mathematical relationship:

\[ A = U`\Sigma `{=tex}V\^T \]

and the low-rank approximation:

\[ A_r = U_r`\Sigma`{=tex}\_rV_r\^T \]

By analyzing singular values and cumulative information, an appropriate
rank (r) can be selected. The resulting approximation can then be used
to estimate user preferences and generate personalized movie
recommendations.

---

## 15. References

- Project II: Singular Value Decomposition (SVD) and Its Applications
  --- course project material.
- MovieLens 100K Dataset --- GroupLens Research.
- NumPy documentation --- Singular Value Decomposition
  (`numpy.linalg.svd`).

---

## Project Status

**Status:** In Progress

**Topic:** SVD for Movie Recommendation Systems

**Application:** Recommendation Systems

**Programming Language:** Python

**Main Dataset:** MovieLens 100K
----------------------------

## License

This project is licensed under the **MIT License**.

See the [`LICENSE`](LICENSE) file for the full license text.

Copyright (c) 2026 Kimsour Kuy
