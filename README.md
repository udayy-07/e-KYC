# e-KYC System

## Overview

This e-KYC (Electronic Know Your Customer) system is designed to facilitate the verification process by leveraging OCR and face recognition technologies. The system is built using Streamlit for the front end and various Python libraries for backend processing.

## File Descriptions

### 1. `app.py`
This is the main application file for the e-KYC system. It includes:
- **Imports**: Necessary libraries and custom modules.
- **Logging Setup**: Configures logging.
- **Streamlit Customization**: Functions to set a wider page layout and custom theme.
- **Sidebar and Header**: Functions to create a sidebar for ID card type selection and display headers based on the selected ID card type.

### 2. `face_verification.py`
This module handles face detection and verification:
- **Imports**: Libraries for face recognition and processing.
- **Logging Setup**: Configures logging.
- **Configuration**: Reads configuration parameters from a YAML file.
- **Functions**: 
  - `detect_and_extract_face(img)`: Detects and extracts the largest face from an image, enlarging it by 15%.

### 3. `ocr_engine.py`
This module extracts text from images using OCR:
- **Imports**: Necessary libraries for OCR and logging.
- **Logging Setup**: Configures logging.
- **Function**:
  - `extract_text(image_path, confidence_threshold=0.3, languages=['en'])`: Extracts text from an image file using EasyOCR, filtering the text based on a confidence threshold and specified languages.

### 4. `preprocess.py`
This module provides image preprocessing functionality.
- **Functions**:
  - `preprocess(image_path)`: Reads an image from the specified path and resizes it to a standard size (300x300).
- **Dependencies**: Requires OpenCV (`cv2`).

### 5. `postprocess.py`
This module provides image post-processing functionality.
- **Functions**:
  - `postprocess(image)`: Takes an image, converts it to grayscale, applies Gaussian blur, thresholds the image, and finds contours.
- **Dependencies**: Requires OpenCV (`cv2`) and NumPy (`np`).

### 6. `mysqldb_operations.py`
This module provides functionality to interact with a MySQL database.
- **Class**:
  - `Database`: Handles connection and query execution for a MySQL database.
- **Methods**:
  - `create_connection(host_name, user_name, user_password, db_name)`: Establishes a connection to the specified MySQL database.
  - `execute_query(query)`: Executes a given SQL query that modifies the database (INSERT, UPDATE, DELETE).
  - `execute_read_query(query)`: Executes a given SQL query that retrieves data from the database (SELECT).
- **Error Handling**: Basic error handling with try-except blocks, errors are printed to the console.

## Setup and Installation

1. **Clone the repository**:
    ```sh
    git clone https://github.com/your-repository/e-kyc-system.git
    cd e-kyc-system
    ```

2. **Install the required packages**:
    ```sh
    pip install -r requirements.txt
    ```

3. **Run the application**:
    ```sh
    streamlit run app.py
    ```

## Configuration

- **Logging**: Logs are stored in the `logs` directory.
- **Configuration File**: `config.yaml` contains paths and other configurations used by various modules.

## Usage

1. Start the application.
2. Select the ID card type from the sidebar.
3. Follow the instructions to upload the required documents.
4. The system will process the uploaded documents and display the extracted information.

