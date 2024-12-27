# FusionPDF

<p align="center">
  <a href="https://github.com/m4j0rt0m/fusionpdf">FusionPDF</a> - A command-line tool for blending and overlaying two PDF files into one.<br>
  <a href="https://github.com/m4j0rt0m/fusionpdf/actions"><img src="https://github.com/m4j0rt0m/fusionpdf/actions/workflows/release.yaml/badge.svg" alt="Build Status"></a>
  <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="license">
  <a href="https://github.com/m4j0rt0m/fusionpdf/releases"><img src="https://img.shields.io/github/v/release/m4j0rt0m/fusionpdf" alt="Version info"></a>
</p>

<p align="center">
  <a href="#features">Features</a> •
  <a href="#installation">Installation</a> •
  <a href="#usage">Usage</a> •
  <a href="#troubleshooting">Troubleshooting</a> •
  <a href="#contributions">Contributions</a><br>
</p>

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
```
```bash
sudo apt install imagemagick poppler-utils
```

### Install FusionPDF

#### From GitHub Releases

1. Download the latest `.deb` package from the [Releases](https://github.com/m4j0rt0m/fusionpdf/releases) page.
2. Install the package using `dpkg`:
```bash
sudo dpkg -i fusionpdf_<version>_all.deb
```
Or, use `apt` for a simpler installation:
```bash
sudo apt install ./fusionpdf_<version>_all.deb
```
3. Resolve any missing dependencies:
```bash
sudo apt-get install -f
```

#### From Source

1. Clone the repository and use the script directly:
```bash
git clone https://github.com/m4j0rt0m/fusionpdf.git
```
```bash
cd fusionpdf
```
2. Move the script to a directory in your PATH, such as /usr/local/bin:
```bash
sudo cp fusionpdf /usr/local/bin/
```

---

## Usage

### Basic Syntax

```bash
fusionpdf <input1.pdf> <input2.pdf> <output.pdf>
```

### Examples

1. Combine two PDFs:
```bash
fusionpdf front.pdf back.pdf result.pdf
```
2. Overlay and save to a specific path:
```bash
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

---

## Troubleshooting

### i) `convert: attempt to perform an operation not allowed by the security policy 'PDF'`

**Cause**: This error occurs because ImageMagick's default security policy restricts PDF operations.

**Solution**:
1. Locate the `policy.xml` file:
```bash
locate policy.xml | grep ImageMagick
```
>Common locations:
>* /etc/ImageMagick-6/policy.xml
>* /usr/lib/ImageMagick-6.9.10/config-Q16/policy.xml

2. Edit the file with a text editor:
```bash
sudo nano /etc/ImageMagick-6/policy.xml
```

3. Find the line restricting PDF operations:
```xml
<policy domain="coder" rights="none" pattern="PDF" />
```

4. Change `rights="none"` to `rights="read|write"`:
```xml
<policy domain="coder" rights="read|write" pattern="PDF" />
```

5. Save the policy file, restart your terminal and try again, it should be solved.
