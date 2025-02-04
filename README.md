# Invoice Data Extraction System

## Overview
This repository contains an Invoice Data Extraction System that extracts text and relevant invoice details from PDF invoices using a hybrid approach. It supports both regular PDFs and scanned invoices using OCR. Extracted data is then processed using regex patterns to identify key invoice fields and saved in CSV format.

## Features
- Extract text from regular PDFs using `PyPDF2`
- Extract text from scanned PDFs using `Tesseract OCR`
- Identify key invoice fields using regex-based extraction
- Save extracted data into a structured CSV file
- Download the extracted CSV file automatically

## Installation
To set up and use the system, install the required dependencies:
```bash
!pip install PyPDF2 pdfminer.six pytesseract opencv-python-headless numpy pandas pdf2image
!apt-get install -y poppler-utils tesseract-ocr
```

## Usage
### Extracting Text from PDFs
For non-scanned PDFs:
```python
text = extract_text_from_pdf('/path/to/invoice.pdf')
```
For scanned PDFs:
```python
text = extract_text_from_scanned_pdf('/path/to/invoice.pdf')
```

### Extracting Invoice Data
Once text is extracted, invoice details can be obtained using:
```python
data = extract_invoice_data(text)
print(data)
```

### Saving Data to CSV
Extracted invoice details are stored in a CSV file for further processing:
```python
import pandas as pd
from google.colab import files

df = pd.DataFrame([data])
df.to_csv('extracted_invoices.csv', index=False)
files.download('extracted_invoices.csv')
```

## Invoice Fields Extracted
- **Invoice Number**
- **Invoice Date**
- **Place of Supply**
- **Place of Origin**
- **GSTIN of Supplier**
- **GSTIN of Recipient**
- **Taxable Value**
- **SGST Rate & Amount**
- **CGST Rate & Amount**
- **IGST Rate & Amount**
- **Total Tax Amount**
- **Final Invoice Amount**

## Technologies Used
- `PyPDF2` for extracting text from regular PDFs
- `pdf2image` and `pytesseract` for OCR on scanned PDFs
- `re` (Regex) for invoice data extraction
- `pandas` for data processing and CSV handling

## Notes
- Ensure Tesseract OCR is installed and configured correctly.
- The regex patterns are tailored for a specific invoice format; modifications may be required for different invoice layouts.
- The system currently runs on Google Colab; adaptations may be needed for local execution.



**Author:** YASH VERMA
