
# Face Recognition based Time Attendance System Model

This project implements a face-recognition-based time attendance system using the **nn4.small2.v1.t7** model for face embedding. It includes image preprocessing, face extraction, and model training with data augmentation techniques.

## Project Structure

- **Model/**: Contains the face recognition model and related files.
- **cascades/**: Stores Haar cascades for face detection.
- **FaceRecog_faceNet_VGG16_MLP.ipynb**: Jupyter notebook for training and testing the face recognition model.
- **cam_test.py**: Python script to test the webcam for face detection.
- **yolov5.rar**: Contains pre-trained YOLOv5 model for object detection.

## Model Details

We use the **nn4.small2.v1.t7** model for face embedding generation. The model converts face images to 128-dimension embedding vectors, which are then used for recognition.

## Image Preprocessing

- **Convert blob images**: Reduces noise in images due to illumination.
  - Input: RGB image matrix and output size.
  - Output: Blob image.
  
- **_extract_face**: Extracts face from an image based on the bounding box and size threshold.
  - Input: RGB image matrix and bounding box coordinates.
  - Output: Extracted face matrix.

We loop through the images, extract faces, and save them to a pickle file. The images are resized using OpenCV to 96x96, which is the required input size for the model.

## Train/Test Split

We divide the dataset into an 80:20 ratio for training and testing to compare the accuracy between pre-trained and self-trained models. The accuracy is calculated based only on the test set.

## Data Augmentation

We apply various data augmentation techniques to improve the model’s performance:
- Normalize pixel values to have a mean of 0 and variance of 1.
- Rotate images by 20 degrees.
- Shift images horizontally and vertically.
- Flip images horizontally.

The augmented images are used to train the model.

## TensorFlow Dataset

We use a TensorFlow dataset with the following configuration:
- Batch size: 32
- Shuffle after every 256 steps.

## How to Run

1. Clone this repository:
   ```bash
   git clone https://github.com/Hung-341/Face-Recognition-based-Time-Attendance-System-Model-Only
   ```
2. Install the required libraries:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the notebook or scripts for training and testing:
   ```bash
   jupyter notebook FaceRecog_faceNet_VGG16_MLP.ipynb
   ```

## License

This project is licensed under the MIT License.
