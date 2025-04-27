
#  Potato Leaf Disease Detection

This project focuses on building an **end-to-end deep learning model** to detect diseases in potato leaves.  
The purpose is educational — to practice model development, deployment preparation, and project structuring.

##  Project Overview
- **Problem**: Early detection of potato leaf diseases to help farmers and reduce crop loss.
- **Approach**: Build a CNN (Convolutional Neural Network) based model to classify healthy and diseased leaves.
- **Dataset**: A curated dataset containing images of **potato leaves** (extracted from a broader dataset including pepper, tomato, and potato leaves).

##  Project Structure
```
LeafDisease/
│
├── datasets/           # Dataset folder (images of potato leaves)
├── models/             # Saved trained models
├── notebooks/          # Colab Notebooks
├── src/                # Source code (training, preprocessing, etc.)
├── README.md           # Project description
└── requirements.txt    # Python libraries required
```

## 🛠️ Technologies Used
- Python
- TensorFlow / Keras
- OpenCV
- NumPy
- Google Colab
- Matplotlib
- Scikit-learn

## Model Workflow
1. **Data Collection** — Gather images of potato leaves (healthy and infected).
2. **Data Preprocessing** — Resize, normalize, and augment images.
3. **Model Building** — Design a Convolutional Neural Network (CNN).
4. **Training & Evaluation** — Train the model and evaluate its performance.
5. **Saving the Model** — Save the trained model for deployment or further use.

## Results
- **Accuracy Achieved**: (to be updated after training)
- **Loss**: (to be updated after training)

##  Useful Links
- **Google Colab Notebook**: [Open Colab](https://colab.research.google.com/drive/1YeEb6vqCUOw0Fn37sV_jCWi4zMNfDonj?usp=sharing)
- **GitHub Repository**: [Visit GitHub](https://github.com/tofayela142/LeafDisease)

##  Future Work
- Expand to detect diseases in pepper and tomato leaves.
- Deploy the model as a web or mobile application.
- Use Transfer Learning with models like MobileNet or EfficientNet for better accuracy.

##  Acknowledgements
Special thanks to our respected teachers and the open-source community for dataset and inspiration.
