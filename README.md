# Project: People Counting with YOLO and ByteTrack

## 1. Objective

The objective of this project is to develop an automated system for detecting, tracking, and counting people in a video using computer vision techniques.

The system uses the following technologies:

- **YOLOv8:** Detects people in each video frame.
- **ByteTrack:** Tracks detected people across consecutive frames and assigns a unique ID to each tracked person.
- **OpenCV:** Handles video processing, displays detection results, and draws the virtual counting line.

People are counted when they cross a virtual diagonal line. Whenever a tracked person crosses this line, the counter is incremented.

Each tracked person is counted only once, even if they cross the line multiple times.

## 2. Video Dataset and Attribution

The video used for people detection, tracking, and line-crossing counting (`town_center_clip.avi`) was obtained from the following public repository:

**Source:** [Nathan Rooy – Raspberry Pi Urban Mobility Tracker](https://github.com/nathanrooy/rpi-urban-mobility-tracker/tree/master/data/videos)

The video is used as input data to demonstrate the people-counting system.

To run the project, download the corresponding video from the source repository and place it in the project directory.

The original video is not included in this repository to keep its size manageable.

## 3. Installation

### Prerequisites

- Python 3.10 or later.
- Jupyter Notebook or JupyterLab.
- An Internet connection for downloading the YOLOv8 model weights during the first run.

### Install Dependencies

Open a terminal in the project directory and execute:

```bash
pip install ultralytics opencv-python matplotlib
```

The libraries are used for the following purposes:

- `ultralytics`: Provides the YOLOv8 model and ByteTrack tracking functionality.
- `opencv-python`: Handles video processing and display.
- `matplotlib`: Allows image visualization inside the notebook.

## 4. Usage

### Project Structure

Make sure the project files are organized as follows:

```text
Person_Counter/
│
├── person_counter.ipynb
├── town_center_clip.avi
└── README.md
```

**Note:** The video must be downloaded separately from the source repository mentioned in Section 2.

### Execution Steps

1. Open a terminal in the project directory.
2. Start Jupyter Notebook:

```bash
jupyter notebook
```

3. Open `person_counter.ipynb`.
4. Execute the notebook cells in order.
5. YOLOv8 detects people in the video.
6. ByteTrack tracks detected people and maintains their IDs across frames.
7. The system checks whether a tracked person crosses the virtual line and updates the counter.
8. The annotated video is displayed in an OpenCV window.

### Customizing the Counting Line

The position of the diagonal counting line can be adjusted directly in the code:

```python
LINE_START = (990, 205)
LINE_END = (1920, 350)
```

- `LINE_START`: Coordinates of the first endpoint.
- `LINE_END`: Coordinates of the second endpoint.

Modify these coordinates to position the counting line according to the video scene.

### Stopping the Execution

Press the `q` key while the video window is active to stop processing.

The final number of counted people is then displayed in the terminal.

## 5. Notes

- The project uses **YOLOv8n**, a lightweight version of YOLOv8, to reduce inference time.
- Using a CUDA-compatible GPU is recommended for better performance. However, the project can also run on a CPU.