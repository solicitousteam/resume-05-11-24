# Document Processing API

This project provides a FastAPI application for processing documents, specifically converting PDF files to DOCX format, removing sensitive information, and inserting logos into documents.

## Features

- Upload PDF or DOCX files.
- Convert PDF files to DOCX format.
- Remove sensitive information such as emails, GitHub links, LinkedIn links, and mobile numbers from documents.
- Insert a logo into the header of the DOCX document.
- Return the modified DOCX file for download.

## Requirements

To run this application, you need to have the following packages installed:

- FastAPI
- Uvicorn
- SpaCy
- Aspose.PDF
- python-docx
- python-multipart

You can install the required packages using:

pip install -r requirements.txt

## Usage

1. Start the FastAPI server: uvicorn main:app --reload

2.Use a tool like Postman or cURL to send a POST request to the `/upload/` endpoint with the following parameters:
   - `file`: The PDF or DOCX file you want to process.
   - `logo`: The logo image file (PNG, JPG, or JPEG) to be inserted into the document.

### Example Request
bash
curl -X POST "http://127.0.0.1:8000/upload/" \
-F "file=@path_to_your_file.pdf" \
-F "logo=@path_to_your_logo.png"



### Response

The API will return the modified DOCX file as a downloadable response.

## Functions

### `pdf_to_docx_aspose(pdf_path, docx_output_path)`

Converts a PDF file to DOCX format using Aspose.PDF.

### `remove_sensitive_info(document)`

Removes sensitive information from the document, including:
- Email addresses
- GitHub links
- LinkedIn links
- Mobile numbers

### `insert_logo(document, logo_file)`

Inserts a logo image into the header of the document.

### `modify_docx(file_content: bytes, logo_content: bytes)`

Processes the DOCX file by removing sensitive information and adding a logo.

### `upload_and_process_file(file: UploadFile, logo: UploadFile)`

Handles the file upload, processes the file, and returns the modified DOCX file.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
