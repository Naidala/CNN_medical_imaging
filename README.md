# Mammography and Neural Networks  
Mammography is essential for early cancer detection but prone to errors. Neural networks reduce human error, achieving up to 85% accuracy. Studies focus on anomalies like masses and calcifications. Preprocessing (e.g., contrast enhancement, background removal) and diverse datasets (e.g., MIAS, DDSM) are critical. CNNs excel at detecting lesions but face challenges in distinguishing benign from malignant. Fine-tuning and data augmentation significantly improve results.

---

## Data Description  
Images are 150x150 pixels, 16-bit grayscale, with labels:  
- 0: Baseline  
- 1: Benign masses  
- 2: Malignant masses  
- 3: Benign calcifications  
- 4: Malignant calcifications  

Data is balanced for unbiased training.

---

## DataAugmentationFromScratch  
A CNN structure with increasing filters (32 to 128) and MaxPooling reduces resolution. Fully connected layers with sigmoid activation optimize binary tasks.  
- **Binary classification**: 82.7% accuracy (35 epochs), 87.5% with augmentation (100 epochs, dropout=0.5).  
- **Four-class classification**: Using one-hot encoding, reached 52.68% accuracy with augmentation.

---

## PreTraining  
VGG16 was fine-tuned, converting grayscale images to RGB. Layers were frozen to leverage pre-trained features.  
- **Binary classification**: 90.18% accuracy (30 epochs).  
- **Four-class classification**: 66.37% accuracy with fine-tuning.  
- **Multilabel classification**: Attributes trained independently (75% individual accuracy, 56% combined accuracy).

---

## Confusion Matrix and Ensemble  
Ensemble methods combine predictions from models to improve accuracy. Fine-tuned models performed best on benign cases, while multilabel models reduced off-diagonal errors. Averaging boosted overall accuracy from 66% to 67%.
