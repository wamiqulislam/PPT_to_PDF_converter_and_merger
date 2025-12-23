# PPT to PDF Converter & Merger

A simple Python script to convert PowerPoint files (`.ppt` / `.pptx`) to PDF and optionally merge them into a single PDF. Works perfectly in **Google Colab** or any environment with LibreOffice installed.

## Features

- Convert single or multiple PPT/PPTX files to PDF
- Merge all PDFs into one single file
- Clean workspace before every run
- Hardcoded paths for easy usage in Colab
- Optional modes:
  - `convert` → convert PPTs to separate PDFs
  - `merge` → merge existing PDFs
  - `convert_and_merge` → convert and merge into one PDF
- Download all PDFs (and merged PDF) as a single ZIP in Colab

## Setup (Colab)

1. Install LibreOffice and PyPDF2:

```python
!apt-get update -qq
!apt-get install -y -qq libreoffice
!pip install PyPDF2 --quiet
```

2. Reset folders:

```python
!rm -rf /content/ppt_input /content/pdf_output
!mkdir /content/ppt_input /content/pdf_output
```

3. Upload your PPT/PPTX files to `/content/ppt_input`.

## Usage

```python
# Change mode based on what you want: "convert", "merge", "convert_and_merge"
MODE = "convert_and_merge"
convert_ppt_to_pdf(MODE)

# After conversion/merge, create a ZIP of all PDFs for download
import os
import zipfile
from google.colab import files

PDF_DIR = "/content/pdf_output"
ZIP_PATH = "/content/all_pdfs.zip"

with zipfile.ZipFile(ZIP_PATH, 'w', zipfile.ZIP_DEFLATED) as zipf:
    for file in os.listdir(PDF_DIR):
        if file.endswith(".pdf"):
            zipf.write(
                os.path.join(PDF_DIR, file),
                arcname=file
            )

print("✅ PDFs zipped successfully")
files.download(ZIP_PATH)
```

- Converted PDFs and merged PDF (if mode includes merge) will appear in `/content/pdf_output`.
- The ZIP file `all_pdfs.zip` will contain **all PDFs** for easy download.

## Notes

- Animations and slide transitions are not preserved (PDF limitation)
- Filenames are sorted alphabetically for merging
- Works best with LibreOffice installed

## License

MIT License
