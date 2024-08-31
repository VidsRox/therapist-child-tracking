# Therapist and Child Detection and Tracking

This project aims to build a video analysis system that detects and tracks therapists and children, particularly those with Autism Spectrum Disorder, in videos. The system assigns unique IDs to each individual, tracks them through various scenarios including re-entries and occlusions, and provides valuable insights into their behaviors and interactions. This README provides a detailed description of the project, guiding you through the setup, usage, and the logic behind analyzing the model predictions.

## Table of Contents
1. [Project Overview](#project-overview)
2. [Technologies and Algorithms Used](#technologies-and-algorithms-used)
3. [Installation](#installation)
4. [Usage](#usage)
5. [Logic Behind Model Predictions](#logic-behind-model-predictions)
6. [Reproducing Results](#reproducing-results)
7. [Results](#results)
8. [Contributing](#contributing)
9. [License](#license)

## Project Overview

This project develops an optimized inference pipeline to process long-duration videos, identifying and tracking children and therapists with unique IDs. The system handles various tracking challenges, such as managing re-entries and post-occlusion tracking, making it robust for real-world applications in understanding behaviors and engagement levels.

## Technologies and Algorithms Used

- **Python**: The primary programming language used for implementing the solution.
- **YOLOv5**: A state-of-the-art object detection model used to identify and locate individuals in each video frame.
- **OpenCV**: Used for video processing tasks, such as reading frames from videos, drawing bounding boxes, and saving the output video.
- **PyTorch**: Deep learning framework utilized for loading and running the YOLOv5 model.
- **NumPy**: For numerical operations, including handling arrays and calculating distances between detected objects for tracking.
- **Google Colab**: Provides a cloud-based platform with GPU support for running the notebook.
- **Google Drive**: Used for storing input and output videos, enabling easy access and saving.

## Installation

1. Clone the repository and navigate to the project directory:
    ```bash
    git clone https://github.com/yourusername/therapist-child-tracking.git
    cd therapist-child-tracking
    ```

2. Install the required dependencies:
    ```bash
    pip install -r requirements.txt
    ```

3. (Optional) Use Google Colab for running the project with GPU support.

## Usage

1. **Prepare Your Data**: Upload your input video files to Google Drive. Ensure that the paths in the code correctly point to these files.

2. **Run the Notebook**: Use Google Colab to run the provided notebook. Follow the step-by-step instructions in the notebook to set up the environment, load the model, and process the videos.

3. **View Results**: The output video with predictions overlaid (bounding boxes and unique IDs) will be saved to Google Drive.

## Logic Behind Model Predictions

The process of analyzing model predictions is detailed as follows:

1. **Object Detection**: 
    - YOLOv5 is used to detect individuals in each frame of the video. The model identifies bounding boxes around persons (children and therapists) and outputs class probabilities.

2. **Tracking Individuals**:
    - A centroid-based tracking algorithm assigns unique IDs to each detected person. The algorithm calculates the centroid of each bounding box and maintains a history of these centroids to track movements across frames.
    - If a person leaves the frame and later re-enters, the algorithm reassigns the original ID if the person’s centroid matches historical data, ensuring continuity in tracking.

3. **Post-Occlusion Tracking**:
    - When individuals are partially or fully occluded, the tracker attempts to maintain their IDs by predicting movements based on previous positions. This minimizes ID reassignment errors and maintains tracking accuracy.

4. **Handling New Entries**:
    - New IDs are assigned to individuals detected for the first time, ensuring that each person is uniquely identified throughout the video duration.

## Reproducing Results

To reproduce the results:

1. Ensure that your video data is correctly uploaded to Google Drive and paths are updated in the notebook.
2. Follow the instructions in the notebook to run the detection and tracking pipeline.
3. The annotated output video will be saved in your specified Google Drive folder.

## Results

The project outputs videos with bounding boxes and unique IDs for each detected individual, accurately tracking their movements, re-entries, and handling occlusions. This provides a visual and quantitative analysis of behaviors and interactions in therapy sessions.

## Contributing

Contributions are welcome! Please follow these steps:
1. Fork the repository.
2. Create a new branch: `git checkout -b feature-branch`
3. Commit your changes: `git commit -m 'Add new feature'`
4. Push to the branch: `git push origin feature-branch`
5. Open a pull request.

## License

This project is licensed under the MIT License. See the `LICENSE` file for more details.

---

This README is designed to guide you through setting up and using the Therapist and Child Detection and Tracking project, providing insights into the underlying logic and helping you easily reproduce the results. If you have any questions or need further assistance, please refer to the project's documentation or open an issue on GitHub.
