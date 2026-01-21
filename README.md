# PDF Splitter Utility

A comprehensive Python GUI application for splitting PDF files with multiple splitting modes.

## Features

- **Three Splitting Modes:**
  - **Split into Two Equal Parts**: Automatically divides PDF into two halves
  - **Split Each Page Individually**: Creates separate PDF files for each page
  - **Split at Specific Page**: Custom split point to divide PDF at any page number

- **User-Friendly GUI**: Built with PyQt5 for a professional interface
- **Progress Tracking**: Real-time progress bar and status updates
- **Multi-threaded Processing**: Non-blocking UI during PDF processing
- **Automatic Naming**: Output files are intelligently named based on input file
- **Error Handling**: Comprehensive error handling with user-friendly messages

## Requirements

- Python 3.7 or higher
- PyQt5 5.15.0+
- PyPDF2 3.0.0+

## Installation

1. **Clone or download this repository**

2. **Install dependencies:**

```bash
pip install -r requirements.txt
```

Or install manually:

```bash
pip install PyQt5 PyPDF2
```

## Usage

### Running the Application

```bash
python pdf_splitter.py
```

### Step-by-Step Guide

1. **Select Input PDF**
   - Click "Browse" next to "Input PDF File"
   - Select the PDF file you want to split
   - The application will display the total number of pages

2. **Choose Split Mode**
   - **Two Equal Parts**: Splits PDF into two files of equal size
   - **Each Page Individually**: Creates one PDF file per page
   - **Specific Page**: Enter the page number where you want to split

3. **Select Output Directory**
   - Click "Browse" next to "Output Directory"
   - Choose where to save the split PDF files
   - By default, it uses the same directory as the input file

4. **Split PDF**
   - Click the "Split PDF" button
   - Monitor progress in the status window
   - A success message will appear when complete

### Output File Naming

**Two Parts Mode:**
- `original_name_part1.pdf`
- `original_name_part2.pdf`

**Individual Pages Mode:**
- `original_name_page_0001.pdf`
- `original_name_page_0002.pdf`
- ...

**Custom Split Mode:**
- `original_name_pages_1-10.pdf`
- `original_name_pages_11-50.pdf`

## Examples

### Example 1: Split 100-page PDF into two parts

Input: `document.pdf` (100 pages)

Output:
- `document_part1.pdf` (pages 1-50)
- `document_part2.pdf` (pages 51-100)

### Example 2: Extract each page individually

Input: `report.pdf` (25 pages)

Output:
- `report_page_0001.pdf`
- `report_page_0002.pdf`
- ...
- `report_page_0025.pdf`

### Example 3: Split at page 30

Input: `manual.pdf` (150 pages)

Output:
- `manual_pages_1-30.pdf` (pages 1-30)
- `manual_pages_31-150.pdf` (pages 31-150)

## Technical Details

### Architecture

- **Main GUI (`PDFSplitterGUI`)**: Handles user interface and user interactions
- **Worker Thread (`PDFSplitterThread`)**: Processes PDF splitting in background
- **Signal-Slot Communication**: Updates UI without blocking

### Threading

The application uses Qt's threading system to prevent UI freezing:
- PDF processing runs in a separate thread
- Progress updates sent via signals
- Main thread remains responsive

### Error Handling

- Invalid file format detection
- Page range validation
- File I/O error handling
- User-friendly error messages

## Troubleshooting

### Issue: "No module named PyQt5"
**Solution:** Install PyQt5:
```bash
pip install PyQt5
```

### Issue: "No module named PyPDF2"
**Solution:** Install PyPDF2:
```bash
pip install PyPDF2
```

### Issue: PDF won't load
**Solution:** 
- Ensure the file is a valid PDF
- Check file permissions
- Try a different PDF file

### Issue: Application won't start on Linux
**Solution:** Install additional Qt dependencies:
```bash
# Ubuntu/Debian
sudo apt-get install python3-pyqt5

# Fedora
sudo dnf install python3-qt5
```

## Platform Support

- **Windows**: Full support
- **macOS**: Full support
- **Linux**: Full support (may require Qt dependencies)

## Performance

- Small PDFs (<10 MB): Near-instant processing
- Medium PDFs (10-50 MB): 1-5 seconds
- Large PDFs (50-200 MB): 5-30 seconds
- Very large PDFs (>200 MB): May take longer, progress tracked

## Security Considerations

- No data sent to external servers
- All processing done locally
- Original PDF files are never modified
- Output files created with standard permissions

## Limitations

- Encrypted PDFs may not be supported (depends on encryption type)
- Very large PDFs (>500 pages) may take significant time for individual page splitting
- Cannot split PDFs with digital signatures while maintaining signature validity

## Future Enhancements

Potential features for future versions:
- Range-based splitting (e.g., pages 10-20, 30-40)
- Merge functionality
- Batch processing multiple PDFs
- PDF rotation during split
- Page preview before splitting
- Custom page selection
- Password-protected PDF support

## License

This project is provided as-is for educational and utility purposes.

## Contributing

Suggestions and improvements are welcome!

## Author

Created for efficient PDF document management.

## Changelog

### Version 1.0.0
- Initial release
- Three splitting modes
- GUI interface
- Progress tracking
- Multi-threaded processing
