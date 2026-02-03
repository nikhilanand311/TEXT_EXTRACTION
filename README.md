# Text Extraction & Summarization Tool

A powerful and user-friendly web application built with Streamlit for extracting bibliography information and summarizing text from various document formats.

---

## 📋 Table of Contents

- [About](#-about)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Architecture](#-architecture)
- [Pages](#-pages)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Usage](#-usage)
- [Contributing](#-contributing)
- [License](#-license)

---

## 📖 About

The **Text Extraction & Summarization Tool** is designed to streamline the process of gathering insights from documents. Whether you have a research paper, a book scan, or an article, this tool allows you to:
- Extract key bibliographic details (Title, Author, Year).
- Generate concise summaries of long texts.
- Convert and download the results in multiple accessible formats.

Built with **Python** and **Streamlit**, it offers a responsive interface with both Light and Dark modes to suit your preference.

---

## ✨ Features

### Core Functionality
- **Bibliography Extraction**: Automatically identifies and extracts Title, Author, and Year from text.
- **Text Summarization**: Uses advanced NLP models (Hugging Face Transformers) to generate summaries.
- **Multi-Format Support**: Upload files in **PDF**, **PNG**, **JPG**, or **JPEG** formats.
- **OCR Capability**: Extracts text from images using Tesseract OCR.

### Advanced Features
- **Multi-Format Export**: Download your results as:
  - Microsoft Word (`.docx`)
  - PDF (`.pdf`)
  - PowerPoint (`.pptx`)
  - Excel (`.xlsx`)
  - Images (`.png`, `.jpg`)
- **Theme Customization**: Toggle between **Light** and **Dark** themes for a comfortable viewing experience.
- **State Management**: Persists your theme and input data during the session.

---

## 🛠 Tech Stack

### Framework & Interface
| Technology | Description |
|------------|-------------|
| **Streamlit** | Web application framework for the UI |
| **Python 3.x** | Core programming language |

### NLP & Processing
| Library | Description |
|---------|-------------|
| **Transformers** | Hugging Face library for text summarization |
| **spaCy** | Advanced Natural Language Processing |
| **PyTesseract** | Python wrapper for Google Tesseract OCR |
| **PyMuPDF (fitz)** | PDF processing and text extraction |
| **Pillow (PIL)** | Image processing library |

### File Generation
| Library | Description |
|---------|-------------|
| **python-docx** | Generating Word documents |
| **ReportLab** | Generating PDF files |
| **python-pptx** | Generating PowerPoint presentations |
| **pandas** | Generating Excel files |

---

## 🏗 Architecture

The application follows a straightforward Streamlit architecture:

```mermaid
graph TD
    A[User] -->|Uploads PDF/Image| B(Streamlit Frontend)
    B -->|PDF| C[PyMuPDF Processor]
    B -->|Image| D[Tesseract OCR]
    C --> E{Action Selected}
    D --> E
    E -->|Extract Bibliography| F[Regex & Logic Layer]
    E -->|Summarize| G[Hugging Face Transformer]
    F --> H[Result View]
    G --> H
    H -->|Download| I[File Generators (Docx, PDF, PPT, etc.)]
```

### Project Structure
```
TEXT_EXTRACTION-main/
├── app.py                 # Main Application Logic
├── requirements.txt       # Python Dependencies
├── .env                   # Environment Variables
└── README.md              # Project Documentation
```

---

## 📄 Pages

### 1. Main Page
The central hub of the application where users can:
- **Upload Files**: Drag and drop support for PDFs and Images.
- **Select Action**: Choose between "Extract Bibliography" or "Summarize Text".
- **View Results**: See the extracted text and processed output (Bibliography or Summary).
- **Download**: Save the results in your preferred format.

### 2. About Page
Provides an overview of the application, features, and the technologies used to build it.

---

## 🚀 Installation

### Prerequisites
1. **Python 3.8+** installed.
2. **Tesseract OCR** installed on your system.
   - **Windows**: [Download Installer](https://github.com/UB-Mannheim/tesseract/wiki) and add it to your PATH.
   - **Linux**: `sudo apt-get install tesseract-ocr`
   - **macOS**: `brew install tesseract`

### Setup Steps

1. **Clone the repository** (if applicable) or navigate to the project folder:
   ```bash
   cd TEXT_EXTRACTION-main
   ```

2. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Download Language Models** (for spaCy):
   ```bash
   python -m spacy download en_core_web_sm
   ```

---

## ⚙️ Configuration

1. Create a `.env` file in the root directory.
2. Add your OpenAI API Key (Required for application initialization):
   ```env
   OPENAI_API_KEY=your_openai_api_key_here
   ```
   *Note: Ensure you have a valid key set, otherwise the app will exit.*

---

## 📖 Usage

1. **Run the Application**:
   ```bash
   streamlit run app.py
   ```

2. **Access the App**:
   Open your browser and navigate to `http://localhost:8501`.

3. **Workflow**:
   - Select **"Extract Bibliography"** from the sidebar to get citation details.
   - Select **"Summarize Text"** to get a quick summary.
   - Upload your document.
   - Click **Save** to set a filename.
   - Click **Download** with your chosen format.

---

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository.
2. Create a feature branch (`git checkout -b feature/AmazingFeature`).
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`).
4. Push to the branch (`git push origin feature/AmazingFeature`).
5. Open a Pull Request.

---

## 📄 License

This project is licensed under the MIT License.
