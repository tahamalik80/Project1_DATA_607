# Project1_DATA_607
# Chess Tournament Data Analysis

## Project Overview

This project parses and analyzes chess tournament results from a semi-structured text file (`tournamentinfo.txt`). It extracts key statistical information for each player and outputs the results into a clean CSV file for further analysis or database import.

**Author:** Taha Malik  
**Date:** September 21, 2025

---

## Objectives

- **Parse a raw chess tournament text file**
- **Extract structured data for each player**, including:
  - Player’s Name
  - Player’s State
  - Total Number of Points
  - Player’s Pre-Rating
  - Average Pre Chess Rating of Opponents (only games actually played)
- **Export the results to a CSV file** (`chess_tournament_results2.csv`)

---

## File Structure

- `tournamentinfo.txt` — The raw tournament data file.
- `Chess_Tournament_Data_Analysis2.Rmd` — The main R Markdown analysis file.
- `chess_tournament_results2.csv` — The output CSV file containing cleaned player data.
- `README.md` — This documentation file.

---

## How the Analysis Works

### 1. **Loading Libraries**
- Uses the `tidyverse` suite for data manipulation and I/O.
- Uses `stringr` for powerful regular expression parsing.

### 2. **Reading Raw Data**
- Reads the entire text file into R and previews lines to confirm structure.

### 3. **Extracting Player Blocks**
- Identifies lines where player records start using a regex pattern.
- Each player's info is captured from two lines: their results and their profile.

### 4. **Parsing Player Information**
- Extracts player's name, state, point total, pre-tournament rating, and opponent pair numbers.
- Only real games (wins, losses, draws) are included for opponent rating calculation; byes and forfeits are ignored.
- Defensive code warns if any critical field is missing.

### 5. **Building Opponent Rating Lookup**
- Creates a fast lookup table for pre-ratings based on player pair number.

### 6. **Calculating Average Opponent Rating**
- For each player, looks up all opponent pre-ratings and computes the mean, excluding any missing values or non-played rounds.

### 7. **Assembling and Exporting Results**
- Wraps all extracted and calculated data into a tidy data frame.
- Outputs the final results to `chess_tournament_results2.csv` for further analysis or import.

---

## Example Output

| Name      | State | Total_Points | Pre_Rating | Avg_Opp_Rating |
|-----------|-------|--------------|------------|----------------|
| Gary Hua  | ON    | 6.0          | 1794       | 1605           |
| ...       | ...   | ...          | ...        | ...            |

- **Avg_Opp_Rating** is calculated ONLY from the opponent’s pre-tournament ratings for *actual games played*.

---

## How To Run The Analysis

1. **Ensure you have R (preferably RStudio) and the required packages (`tidyverse`, `stringr`) installed.**
2. **Place `tournamentinfo.txt` in your working directory.**
3. **Open `Chess_Tournament_Data_Analysis2.Rmd` in RStudio and knit the file to HTML.**
4. **After knitting, check your directory for `chess_tournament_results2.csv`.**
5. **Use the CSV for further analysis, import to SQL, or as project deliverable.**

---

## Advanced Features & Edge Case Handling

- **Robust regex parsing** for names, points, and opponent numbers.
- **Warnings issued for missing or malformed data.**
- **Excludes byes, forfeits, and unplayed rounds from average calculations.**
- **Summary statistics are printed to help verify data integrity.**
- **Ready for RPubs publication; HTML output contains both code and results.**

---

## Publishing & Sharing

- Knit the `.Rmd` to HTML and upload to [RPubs](https://rpubs.com/) for easy sharing. -
https://rpubs.com/tmalik03/Project1_DATA_607 
---

## References

- [Elo Rating System](https://en.wikipedia.org/wiki/Elo_rating_system)
- Tournament data provided in assignment

---
