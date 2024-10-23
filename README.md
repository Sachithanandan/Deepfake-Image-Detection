# **Deepfake Detection Project**

This repository contains Python scripts to build a pipeline for detecting deepfakes using Convolutional Neural Networks (CNNs).

## **Setup**

1. **Clone the repository:**

   ```bash
   git clone <repository-url>
   cd <repository-folder>
   ```

2. **Create virtual environment & install dependencies:**

   ```bash
   python -m venv venv
   source venv/bin/activate   # Linux/Mac
   .\venv\Scripts\activate    # Windows
   pip install -r requirements.txt
   ```

## **Usage**

1. **Convert Video to Images:**

   ```bash
   python 00-convert_video_to_image.py --input_video <path> --output_folder <path>
   ```

2. **Crop Faces:**
   - **MTCNN:** 

     ```bash
     python 01a-crop_faces_with_mtcnn.py --input_folder <path> --output_folder <path>
     ```
   - **Azure Vision API:** 

     ```bash
     python 01b-crop_faces_with_azure-vision-api.py --input_folder <path> --output_folder <path>
     ```

3. **Prepare Dataset:**

   ```bash
   python 02-prepare_fake_real_dataset.py --input_folder <path> --output_folder <path>
   ```

4. **Train CNN:**

   ```bash
   python 03-train_cnn.py --dataset_folder <path> --model_output <path>
   ```

5. **Run Flask App:**

   ```bash
   python app.py
   ```



**workflow**:

1. **Convert Video to Frames**: Extract images from video using `00-convert_video_to_image.py`.
2. **Detect & Crop Faces**: 
   - Use either **MTCNN** (`01a-crop_faces_with_mtcnn.py`) or **Azure Vision API** (`01b-crop_faces_with_azure-vision-api.py`) to crop faces from images.
3. **Prepare Dataset**: Organize images into "deepfake" and "real" folders using `02-prepare_fake_real_dataset.py`.
4. **Train CNN Model**: Train a deepfake classifier using `03-train_cnn.py` on the prepared dataset.
5. **Deploy Web App**: Run `app.py` to launch a Flask-based app for image classification.


