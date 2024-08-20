# High School Extractor from LinkedIn Profile Files

## Overview

This script processes a list of LinkedIn profile files (in HTML or plain text format) and extracts the name of the high school listed under the "Education" section. The extracted information is saved in a CSV file with two columns: the file path of the LinkedIn profile and the corresponding high school name.

## Requirements

- Python 3.x
- Libraries:
  - `BeautifulSoup4` (from `bs4`)
  - `opencv-python`

## Installation

To run this script, you need to have Python installed on your system. Additionally, you need to install the `BeautifulSoup4` library. You can install it using pip:

```bash
pip install beautifulsoup4
```

## Input Files

- **input_linkedin_files.csv**: A CSV file containing the file paths of LinkedIn profile HTML or text files. Each file should represent a LinkedIn profile and be listed in the first column of the CSV.

### Example `input_linkedin_files.csv`

```csv
LinkedIn File Path
/path/to/example_profile1.html
/path/to/example_profile1.txt
/path/to/example_profile2.txt
/path/to/example_profile2.html
```

- **LinkedIn Profile Files**: These files should be in HTML or plain text format and must contain an "Education" section where high schools are listed.

## Output File

- **output_high_schools.csv**: The script will generate this CSV file, which will contain the file path of the LinkedIn profile and the extracted high school name.

### Example `output_high_schools.csv`

```csv
LinkedIn URL,High School
/path/to/example_profile.html,Springfield High School
/path/to/example_profile.txt,Springfield High School
```

## How to Run the Script

1. Ensure that you have the required CSV file (`input_linkedin_files.csv`) and the corresponding LinkedIn profile files (HTML or text) in place.

2. Place the script (`linkedin_high_school_scraper.py`) in the same directory as your `input_linkedin_files.csv`.

3. Run the script using Python:

python linkedin_high_school_scraper.py


4. The output will be saved in `output_high_schools.csv` in the same directory.

## Code Explanation

- **extract_high_school(file_path)**: 
  - This function reads the content of the file (HTML or text) provided by `file_path`.
  - If the content contains HTML tags (`<html>` or `<body>`), it processes it as an HTML file using `BeautifulSoup`.
  - It looks for the "Education" section and tries to find the high school name. 
  - If it's not an HTML file, it searches the plain text lines for "High School".
  - The function returns the high school name if found, otherwise, it returns "High School not found."

- **process_linkedin_profiles(input_csv, output_csv)**:
  - This function processes the input CSV (`input_linkedin_files.csv`) and uses the `extract_high_school` function to extract high school names.
  - It writes the results to an output CSV (`output_high_schools.csv`).

## Error Handling

- The script includes basic error handling to manage cases where files cannot be processed. If an error occurs, the output will indicate "Error processing file".
