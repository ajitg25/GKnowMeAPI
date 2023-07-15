# G-KnowMe API

## Description

The GKnowMe API is designed to extract text details from lab reports, excluding personal information, and store them in the same format as visible in the lab report. The extracted information is then linked to a unique user ID, such as Aadhar card, and stored in a Blockchain network for secure access and tamper-proof storage.

## API Working:
**Upload Lab Report:** The user uploads a lab report file to the API portal.

**File Validation:** The API checks if the uploaded file is in one of the supported image formats, such as PNG, JPG, or JPEG. If the file is valid, the API proceeds to the next step.

**Image Processing:** The uploaded image file is processed using the img_process() function. This function enhances the image to improve text extraction accuracy.

**Text Contour Detection:** The API utilizes the OpenCV library to detect text contours within the lab report. The get_coord() function identifies the coordinates of these contours and returns them in a dictionary format, using the y,x values as keys.

**Sorting Coordinates:** The sort_coord() function ensures that the contours are properly sorted in row-wise order. Due to variations in pixel positioning, the function allows a threshold of 1-10 pixels to consider contours in the same row. This step helps maintain the correct structure of the extracted information.

**Text Extraction:** The sorted coordinates are passed to the get_csv_json() function, which utilizes the PyTesseract library for text extraction. The function extracts text from each contour and organizes it into columns, including test name, reference value, units, and results.

**JSON Output:** The extracted information is stored in a JSON format as key-value pairs. Each pair represents a specific piece of information from the lab report. The final JSON output is returned from the API as the desired result.



## Installation

To install this project, follow these steps:

1. Install the Tesseract-OCR.
2. `pip install -r requirements.txt`.
4. Run the api file using,
    `uvicorn api:app --reload`

