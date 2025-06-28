readme: |
  # 🧩 Board Game Data Processing Scripts

  This project provides a set of shell scripts to clean and analyze the [Board Game Geek dataset](https://www.kaggle.com/datasets/andrewmvd/board-games), which contains information on 20,000+ board games. Each game entry includes metadata such as name, year published, mechanics, domains, complexity, ratings, and more.

  The goal is to answer several data analysis questions using only standard Unix tools and shell scripting.

  ---

  ## 📌 Research Objectives

  Using cleaned data, the following research questions are addressed:

  1. **What is the most popular game domain and game mechanic?**  
     (Appearance in a game's list counts as one occurrence.)

  2. **Is there a correlation between publication year and average rating?**  
     (E.g., are newer games generally rated higher?)

  3. **Is there a correlation between game complexity and average rating?**

  ---

  ## 🛠️ Shell Scripts

  ### 1. `empty_cells`

  This script identifies and counts empty cells in each column of a semicolon-separated dataset.

  **Input**:
  - A text file with semicolon (`;`) delimiters.
  - First line contains column headers.

  **Output**:
  - A count of empty cells per column, for example:
    ```
    /ID: 16
    Name: 0
    Year Published: 1
    ```


  ### 2. `preprocess`

  Cleans and standardizes the dataset to prepare it for analysis.

  **Input**:
  - A raw `.txt` file with:
    - Semicolon delimiters.
    - Windows-style line endings (CRLF).
    - European-style decimal commas (e.g., `3,14`).
    - Non-ASCII characters.
    - Possibly empty `/ID` fields.

  **Output**:
  - A **tab-separated** cleaned version of the dataset sent to standard output, with:
    - `;` replaced by tab characters.
    - Windows line endings converted to Unix (LF).
    - Decimal commas replaced with `.`.
    - Non-ASCII characters removed.
    - Empty `/ID` values filled with new unique integers, continuing from the largest existing ID.

  ### 3. `analysis`

  Processes the cleaned tab-separated data and answers the research questions.

  **Input**:
  - A cleaned `.tsv` file from the `preprocess` script.

  **Output**:
  - Most popular **game mechanic** and **game domain**.
  - **Pearson correlation coefficient** between:
    - Year published and average rating.
    - Complexity and average rating.

  **Example Output**:
The most popular game mechanics is Hand Management found in 48 games
The most game domain is Strategy Games found in 77 games
The correlation between the year of publication and the average rating is 0.226
The correlation between the complexity of a game and its average rating is 0.426

## 📚 Notes

- All scripts assume the column order in the dataset remains constant.
- The analysis assumes input data has already been cleaned.
- Scripts were tested using the provided class Docker image.


## 🧾 References

- Dataset: [Board Games Dataset on Kaggle](https://www.kaggle.com/datasets/andrewmvd/board-games)
- Pearson correlation: [How to Calculate Correlation Coefficient](https://www.cuemath.com/data/how-to-calculate-correlation-coefficient/)
