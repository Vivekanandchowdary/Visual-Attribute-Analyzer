# Visual Attribute Analyzer

## Overview
The **Visual Attribute Analyzer** is an AI-powered system designed to extract objective, structured visual data from product images. Rather than relying on manual tagging or traditional computer vision training pipelines, this project utilizes a **Multimodal Large Language Model (Google Gemini)** to interpret complex visual features.

The system accepts product images (local files or URLs) and outputs continuous floating-point scores for specific visual dimensions, along with a list of observable attributes. Results are automatically aggregated into an Excel report for easy analysis.

## Key Features
* **Zero-Shot Analysis:** No model training required; leverages the generalized knowledge of Foundation Models.
* **Structured Output:** Converts unstructured image data into strict JSON and tabular formats.
* **Dimensional Scoring:** Evaluates products on 5 specific visual scales (-5.0 to +5.0), including *Visual Weight*, *Formality*, and *Unconventionality*.
* **Automated Reporting:** Automatically saves and appends results to `product_measurements.xlsx`, preventing duplicate entries.

## Architecture

1.  **Input Layer:** Handles image ingestion from local directories or web URLs, including "User-Agent" spoofing to bypass basic web scraping blocks.
2.  **Intelligence Layer:** Uses **Google Gemini 1.5/2.0** with a prompt-engineered "System Instruction" to enforce strict JSON schemas and numerical scaling.
3.  **Persistence Layer:** A lightweight storage mechanism using `pandas` to manage an append-only Excel database of analyzed products.

## Setup & Usage

### Prerequisites
* Python 3.x
* A Google Gemini API Key

### Installation
1.  Clone the repository:
    ```bash
    git clone [https://github.com/YOUR_USERNAME/Visual-Attribute-Analyzer.git](https://github.com/YOUR_USERNAME/Visual-Attribute-Analyzer.git)
    cd Visual-Attribute-Analyzer
    ```

2.  Install dependencies:
    ```bash
    pip install -q -U google-generativeai pandas openpyxl requests pillow
    ```

3.  Configure API Key:
    * Open the script and paste your API key in the `API_KEY` variable.

### Running the Analysis
Run the main script (or Jupyter Notebook cells):
```python
# Analyze a single image
result = analyze_product_image("path/to/image.jpg")
save_to_excel(result, "path/to/image.jpg")
