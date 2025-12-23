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
# Import the function (if in a separate module)
# from ppt_converter import convert_ppt_to_pdf

# Modes:
convert_ppt_to_pdf("convert")             # Convert only
convert_ppt_to_pdf("merge")               # Merge existing PDFs only
convert_ppt_to_pdf("convert_and_merge")   # Convert then merge into one PDF
```

- Converted PDFs and merged PDF (if mode includes merge) will appear in `/content/pdf_output`.

## Notes

- Animations and slide transitions are not preserved (PDF limitation)
- Filenames are sorted alphabetically for merging
- Works best with LibreOffice installed

## License

MIT License
