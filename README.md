#Board Game Data Processing Scripts

This project aims to process and analyse Board Games Geek dataset and answer certain research questions. The data is sourced from Kaggle and contains 20,000+ board games. Each row represents a game, and columns hold details like ID, name, year published, mechanics, domains, complexity, play time, min age, users rated, BGG rank, owned users, min players, max players and average rating.

Objective: Create 3 shell scripts named empty_cells, preprocess and analysis that answer the following research questions:
•	What is the most popular domain and most popular mechanics across the set of games. (Appearance in a given game's list counts as 1.)
•	What is the correlation between publication year and average rating, e.g. newer games being preferred over older ones.
•	What is the correlation between game complexity and average rating.

Scripts

1. empty_cells

This script reads a semicolon-separated text file and counts how many empty cells are in each column.

Input: A text file where:

The first line has column names (headers).
Each line is split by semicolons (;).
An empty cell is when there's nothing between two semicolons or at the end of a line.

Output: Empty cells are counted carefully and displayed as output.

Example: 
/ID: 16
Name: 0
Year Published: 1
Notes:

Note: The script assumes the first line contains the headers.

2. preprocess
This script takes a raw semicolon-separated file, cleans it up and outputs the cleaned file as a tab-separated file with standardized formatting.

Input: A text file with:

Semicolon (;) separators.
Windows-style line endings (CRLF).
Decimal commas (e.g., 3,14 instead of 3.14).
Possible non-ASCII characters (like special symbols).
Some missing or empty IDs in the /ID column.
Output: A cleaned file (sent to stdout) where:

Semicolons are replaced with tabs (\t).
Windows CRLF line endings are changed to Unix LF endings.
Decimal commas are replaced with decimal points (e.g., 3,14 becomes 3.14).
Non-ASCII characters are removed.
Missing or empty IDs are replaced with new, unique integer IDs that continue from the largest ID found in the file.
Notes:

Other empty cells (not IDs) are left as they are.
The output is a tab-separated file ready for the analysis script.


3. analysis
This script analyses the cleaned tab-separated file from preprocess to answer questions about the board game data such as calculating the Pearson correlations for the numerical columns (year published, complexity, and average rating).


Input: The tab-separated file from preprocess is used. 

Example Questions:

Most popular game mechanics: The mechanics that appear in the most games.
Most popular game domain: The domain that appears in the most games.
Correlation between year published and average rating: A number (Pearson correlation) showing how these two are related.
Correlation between complexity and average rating: A number (Pearson correlation) showing how these two are related.

Example output:

The most popular game mechanics is Hand Management found in 48 games
The most game domain is Strategy Games found in 77 games
The correlation between the year of publication and the average rating is 0.226
The correlation between the complexity of a game and its average rating is 0.426
