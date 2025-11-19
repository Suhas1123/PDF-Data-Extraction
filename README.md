# PDF Data Extraction & Database Storage Tool

This tool is a Python-based backend service designed to automate the ingestion and structuring of data from PDF documents (like policy schedules or invoices).

It follows a full data pipeline:
1. Receives a PDF file via an API endpoint.
2. Extracts all raw text and structured entities (key fields).
3. Stores the data in a persistent database for search and reporting.

## 🛠️ Technology Stack

| Component | Technology | Role |
| :--- | :--- | :--- |
| **Backend/API** | **Python (Flask)** | Handles the HTTP requests (file upload) and application logic. |
| **Extraction** | **PDFPlumber** | Library used to open, parse, and extract text and layout information from the PDF file. |
| **Database/ORM** | **SQLAlchemy** | Used as the Object-Relational Mapper (ORM) to manage the database structure and connections. |
| **Database File** | **SQLite** | Used for local, file-based data persistence (`pdf_data.db`). |

---

## 🚀 Getting Started

### Prerequisites

* **Python 3.x**
* **pip** (Python package installer)

### Installation

1.  **Clone the Project (or place files in a folder):**
    ```bash
    mkdir PDF_Robot
    cd PDF_Robot
    ```

2.  **Install Required Libraries:**
    ```bash
    pip install Flask SQLAlchemy pdfplumber
    ```

3.  **Start the Service:**
    Run the main application file:
    ```bash
    python app.py
    ```
    The service will start running and listening on `http://127.0.0.1:5000/`. Keep this terminal window open.

---

## 🚪 API Endpoint Usage

The service exposes one primary endpoint for handling file uploads.

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| **`POST`** | `/upload-pdf` | Uploads a PDF file, triggers extraction, and stores data in the database. |

### Sending a File (using `curl`)

To send a file, you must use a tool that supports `POST` requests and `form-data` file uploads (like `curl`, Postman, or a custom script).

In your terminal (open a new one so the robot stays running), run:

```bash
# IMPORTANT: Replace /path/to/your/document.pdf with the actual local path of your PDF file.
curl -X POST -F 'file=@/path/to/your/document.pdf' [http://127.0.0.1:5000/upload-pdf](http://127.0.0.1:5000/upload-pdf)
