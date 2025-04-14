# Deep Visual Programming Interface using QR/ArUco Markers

This project allows users to build logic-based programs using **QR codes** and **ArUco markers** in the real world, interpreted by a webcam. The system identifies various logic blocks (e.g., `if`, `while`, `print`) represented by these markers and executes the corresponding commands dynamically. This project demonstrates an **augmented reality-inspired visual programming environment** for physical spaces.

## Project Structure

deep-visual-programming/ ├── README.md ├── requirements.txt ├── .gitignore ├── setup.py ├── run.py # Entry point ├── config/ │ └── markers.yaml # Marker ID to logic block mapping ├── data/ │ └── test_images/ # Static images for testing ├── docs/ │ └── architecture.md ├── scripts/ │ └── generate_markers.py # Auto-generate ArUco markers ├── core/ │ ├── init.py │ ├── marker_tracker.cpp # Real-time ArUco/QR detection (OpenCV C++) │ ├── marker_tracker.so # Compiled C++ shared lib │ └── marker_interpreter.py# Logic graph builder and interpreter ├── models/ │ └── gesture_model.pt # Optional: gesture recognition model ├── utils/ │ ├── aruco_helper.py │ ├── qr_reader.py │ └── visualizer.py └── tests/ └── test_interpreter.py # Unit tests


## Features

- **Marker-based Programming**: Use QR codes/ArUco markers as building blocks for your programs.
- **Real-time Interpretation**: The webcam detects and processes markers to interpret commands.
- **Modular Components**: Easy to extend with more logic blocks and enhanced recognition capabilities.
- **Gesture Recognition** (Optional): Interact with the program using hand gestures (via PyTorch model).
- **Cross-platform**: Can be run locally on Windows, macOS, and Linux.
- **Testing**: Automated tests for key program logic.

## Requirements

### Software Requirements
- **Python 3.10+**
- **C++ Compiler** (for building the ArUco marker tracker)
- **OpenCV** (for marker detection and real-time video processing)
- **PyTorch** (optional: for gesture recognition model)
- **NumPy**, **PyYAML**, **pyzbar** (QR reader), **matplotlib** (for visualization)

### Install Dependencies

1. Clone this repository:

   ```bash
   git clone https://github.com/yourusername/deep-visual-programming.git
   cd deep-visual-programming

Set up a virtual environment (recommended):

bash
Copy
Edit
python -m venv venv
source venv/bin/activate  # On Windows use venv\Scripts\activate
Install the required Python dependencies:

bash
Copy
Edit
pip install -r requirements.txt
(Optional) If you want to run the gesture recognition functionality, you'll need to download the gesture_model.pt file (if provided) and place it in the models/ folder.

Setup Instructions
1. C++ ArUco Tracker
The project includes a C++ shared library (marker_tracker.so or marker_tracker.pyd) for efficient real-time marker detection. You need to compile the C++ source code to generate the shared library:

On Linux/macOS:

bash
Copy
Edit
g++ -std=c++17 -shared -fPIC -o core/marker_tracker.so core/marker_tracker.cpp `pkg-config --cflags --libs opencv4`
On Windows, use a compatible compiler (MSVC, MinGW) to build marker_tracker.pyd or marker_tracker.dll.

If you need help with building on Windows, refer to OpenCV documentation.

2. Generate ArUco Markers (Optional)
If you want to generate new markers, you can use the scripts/generate_markers.py script to create QR/ArUco markers.

Run:

bash
Copy
Edit
python scripts/generate_markers.py
This will generate a set of markers that correspond to the logic blocks defined in config/markers.yaml.

How to Run the Program
Local Testing
Start the webcam:

bash
Copy
Edit
python run.py
As the program runs, hold or display ArUco markers in front of the webcam. The system will recognize the markers and execute the logic corresponding to their IDs.

Use the following marker IDs as defined in config/markers.yaml:

0: start

1: if

2: else

3: while

4: print('Hello')

5: end

Test the Code Locally
To test the basic interpreter:

bash
Copy
Edit
pytest tests/
This will run all unit tests in the tests/ directory.

How to Contribute
We welcome contributions to this project! Here’s how you can get involved:

1. Fork the Repository
Click on the Fork button at the top right of this repository to create your own copy.

2. Clone Your Fork
Clone your forked repository to your local machine:

bash
Copy
Edit
git clone https://github.com/yourusername/deep-visual-programming.git
cd deep-visual-programming
3. Create a New Branch
Always create a new branch for your feature or bug fix:

bash
Copy
Edit
git checkout -b feature/your-feature-name
4. Make Your Changes
Add or modify code in the core/, utils/, or scripts/ directories.

Add or modify tests in the tests/ directory.

5. Commit Your Changes
After making your changes, commit them:

bash
Copy
Edit
git add .
git commit -m "Added new feature or fixed a bug"
6. Push Changes
Push your changes to your forked repository:

bash
Copy
Edit
git push origin feature/your-feature-name
7. Create a Pull Request
Go to the original repository and create a Pull Request with your changes.

License
This project is licensed under the MIT License - see the LICENSE file for details.

Acknowledgments
OpenCV for marker detection and real-time computer vision.

PyTorch and TensorFlow for deep learning models (optional).

Contributors and open-source libraries that made this project possible.

Example Contributions
Improved Marker Detection: Enhance marker detection for better performance in low-light conditions.

Added New Logic Blocks: Implement additional logic blocks like for, while, etc.

Gesture Recognition: Train and integrate new gesture recognition models.

GUI Interface: Build a GUI to visualize the logic and block connections.

Issues
If you find any issues, please report them in the Issues section.