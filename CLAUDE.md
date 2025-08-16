# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Python-based computer vision project that uses DeepFace library for real-time facial analysis including age prediction, gender detection, and emotion recognition. The project supports both live camera feed and video file analysis with advanced features like MediaPipe face landmarks detection.

## Dependencies and Environment

### Core Dependencies
- **opencv-python==4.11.0.86** - Computer vision and video processing
- **deepface==0.0.93** - AI-powered facial analysis (age, gender, emotion)
- **mediapipe==0.10.21** - Google's framework for face landmarks detection
- **numpy>=1.26** - Numerical computations
- **tensorflow[and-cuda]==2.16.1** - Machine learning backend (with CUDA support)

### Installation
```bash
pip install -r requirements.txt
```

Note: The project is configured for GPU acceleration with TensorFlow CUDA, but will fall back to CPU if GPU is unavailable.

## Architecture and Components

### Main Implementation (DeepFace.ipynb)
The project is implemented as a Jupyter notebook with three distinct analysis approaches:

1. **Real-time Camera Analysis** (Cell 1)
   - Live webcam feed processing
   - Basic age, gender, emotion detection overlay
   - Uses OpenCV for camera capture and display

2. **Video File Analysis with Data Table** (Cell 2)
   - Processes video files frame by frame
   - Creates real-time data visualization table
   - Analysis history tracking (last 10 entries)
   - Progress monitoring and frame-by-frame analysis

3. **Advanced Analysis with Face Landmarks** (Cell 3)
   - Combines DeepFace analysis with MediaPipe face mesh
   - GPU/CPU device detection and optimization
   - Interactive controls (pause/resume functionality)
   - Detailed face landmarks visualization (eyes, nose, mouth, face contours)
   - Enhanced data table with GPU status indicators

### Key Features
- **Multi-backend Support**: OpenCV and MediaPipe detector backends
- **GPU Acceleration**: Automatic GPU detection with CPU fallback
- **Error Handling**: Robust error handling with `enforce_detection=False`
- **Performance Optimization**: Frame skipping (every 5th frame) for real-time processing
- **Interactive Controls**: Keyboard shortcuts for user interaction

## Development Environment

### Jupyter Notebook Environment
The project uses Jupyter notebooks as the primary development environment. The notebook contains executable cells with different analysis modes.

### GPU Configuration
The project includes automatic GPU detection and configuration:
```python
physical_devices = tf.config.experimental.list_physical_devices('GPU')
if len(physical_devices) > 0:
    tf.config.experimental.set_memory_growth(physical_devices[0], True)
```

## Usage Patterns

### Running Analysis
1. **Camera Analysis**: Execute cell 1 for live camera feed
2. **Video Analysis**: Place video file in project root and execute cell 2 or 3
3. **Controls**: 
   - 'q' or ESC: Exit
   - Space: Pause/Resume (advanced mode)
   - 'c': Continue after pause

### Video Input
- Place video files (e.g., `girl.mp4`) in the project root directory
- Supported formats: Standard video formats supported by OpenCV

### Output Features
- Real-time overlay text with analysis results
- Separate data table window showing historical analysis
- Progress indicators and performance metrics
- Face landmarks visualization (advanced mode)

## Technical Notes

### DeepFace Configuration
- Uses stable `opencv` detector backend by default
- Analyzes age, gender, and emotion simultaneously
- Configured with `enforce_detection=False` to prevent crashes on unclear faces

### MediaPipe Integration
- Face mesh detection with refined landmarks
- Custom landmark drawing for key facial features
- Optimized for single face detection (`max_num_faces=1`)

### Performance Considerations
- Frame skipping (every 5th frame) for real-time performance
- GPU memory growth configuration to prevent allocation issues
- Efficient data structure management for analysis history

## File Structure
- `DeepFace.ipynb` - Main implementation notebook
- `requirements.txt` - Python dependencies
- `girl.mp4` - Sample video file for testing
- Video files should be placed in project root for analysis