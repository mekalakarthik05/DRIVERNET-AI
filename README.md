# DriverNet AI — Autonomous Driving Intelligence

![DriverNet AI Demo](demo.webp)

DriverNet AI is an end-to-end deep learning system for self-driving vehicles, powered by a Convolutional Neural Network (CNN) architecture inspired by NVIDIA's autonomous driving research. The model processes raw camera feeds and predicts precise steering angles in real-time, learning directly from human driving behavior using Behavioral Cloning.

## Features

- **Real-Time Interactive Simulator**: Experience real-time AI steering predictions. Adjust road curvature to see how the model reacts.
- **Advanced CNN Architecture**: Built with PyTorch, the network features 5 convolutional layers and 4 fully connected layers optimized for spatial feature extraction.
- **Robust Data Augmentation Pipeline**: Handles dynamic cropping, resizing, color space conversion (RGB → YUV), and random translations/brightness adjustments to ensure the model generalizes across diverse road conditions.
- **Live Training Dashboard**: Watch the model converge in real-time with an interactive visualization of the RAdam optimizer and MSE loss tracking.

## Technology Stack

- **Frontend**: HTML5, Vanilla CSS, Vanilla JavaScript (Canvas API)
- **Model / Backend**: Python, PyTorch, OpenCV, Flask (optional)
- **Deployment**: Vercel Ready

## Local Setup

To run the simulator interface locally, you don't need to install any heavy dependencies. Just serve the static files:

```bash
# Clone the repository
git clone <your-repository-url>
cd <repository-name>

# Start a local web server (Python 3)
python -m http.server 8000
```
Open `http://localhost:8000` in your web browser.

## Deployment

This dashboard is optimized for seamless deployment as a static site. 
You can easily deploy it using Vercel:

```bash
npx vercel --prod
```

## Architecture

1. **Input**: 3 × 66 × 200 (YUV format)
2. **Conv2D**: 24 filters @ 5×5 (stride 2) + ELU
3. **Conv2D**: 36 filters @ 5×5 (stride 2) + ELU
4. **Conv2D**: 48 filters @ 5×5 (stride 2) + ELU
5. **Conv2D**: 64 filters @ 3×3 (stride 1) + ELU
6. **Conv2D**: 64 filters @ 3×3 (stride 1) + ELU + Dropout
7. **Fully Connected Layers**: 1152 → 100 → 64 → 10 → 1 (Continuous Steering Angle)
