# FusionPDF

FusionPDF is a lightweight command-line tool designed to blend and overlay two PDF files into a single polished output. Whether you’re creating composite documents, overlays, or simply combining pages with precision, FusionPDF makes it simple and efficient.

---

## Features

- **Blend PDF Pages**: Combines the first pages of two PDF files into a visually appealing overlay.
- **Normalization**: Automatically adjusts output for optimal results.
- **Lightweight**: Minimal dependencies and fast execution.
- **Command-Line Simplicity**: Run directly from the terminal with clear and concise options.

---

## Installation

### Prerequisites

FusionPDF requires the following tools:
- **ImageMagick**: For image processing.
- **Poppler-utils**: For extracting images from PDFs.

Install them with:
```bash
sudo apt update
sudo apt install imagemagick poppler-utils
```

### Install FusionPDF

Clone the repository and use the script directly:

```
git clone https://github.com/m4j0rt0m/fusionpdf.git
cd fusionpdf
chmod +x fusionpdf
sudo cp fusionpdf /usr/local/bin/
```

---

## Usage

### Basic Syntax

```
fusionpdf <input1.pdf> <input2.pdf> <output.pdf>
```

### Examples

1. Combine two PDFs:
```
fusionpdf front.pdf back.pdf result.pdf
```
2. Overlay and save to a specific path:
```
fusionpdf cover.pdf watermark.pdf ~/Documents/combined.pdf
```

> If you omit any required argument, the tool will display usage instructions.

---

## How It Works

1. Extracts Images: Takes the first pages of both PDFs and converts them to images.
2. Blends Images: Combines the images using transparency and normalization for optimal results.
3. Creates PDF: Converts the blended image back into a PDF.

---

## Contributions

Contributions are welcomed! Please open an issue or submit a pull request if you have ideas for improvements or find any bugs.

---

## License

This project is licensed under the MIT License. See the LICENSE file for details.

---

## Acknowledgments

FusionPDF leverages the power of ImageMagick and Poppler-utils to deliver its functionality.
