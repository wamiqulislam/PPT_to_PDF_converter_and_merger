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
- Supports downloading all PDFs (and merged PDF) as a single ZIP in Colab

## Setup (Colab)

1. Install LibreOffice and PyPDF2:

```python
!apt-get update -qq
!apt-get install -y -qq libreoffice
!pip install PyPDF2 --quiet
```

2. Upload PPT/PPTX Files:

Click the |choose files| button and select all the files you would like to convert

3. Choose the mode (optional).

Change the mode here, depending on if you only want to convert to pdf, make a merged pdf, or both

```python
# Change mode based on what you want: "convert", "merge", "convert_and_merge"
MODE = "convert_and_merge"
```

- Converted PDFs and merged PDF (if mode includes merge) will appear in `/content/pdf_output` adn will be automatically zipped and downloaded

## Notes

- Animations and slide transitions are not preserved (PDF limitation)
- Filenames are sorted alphabetically for merging
- Works best with LibreOffice installed

## License

MIT License
