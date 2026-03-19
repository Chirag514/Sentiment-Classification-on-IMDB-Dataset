# IMDB Sentiment Classification using RNN, LSTM & GRU

## Overview
This project focuses on **binary sentiment classification** of movie reviews from the IMDB dataset using deep learning models.

The goal was not just to build models, but to **analyze training behavior**, identify issues like **underfitting and overfitting**, and apply techniques to improve performance and generalization.

---

## Dataset
- **IMDB Movie Reviews Dataset**
- 50,000 labeled reviews:
  - Positive
  - Negative

---

## Models Implemented
- Recurrent Neural Network (**RNN**)
- Long Short-Term Memory (**LSTM**)
- Gated Recurrent Unit (**GRU**)

---

## Training Setup
- Loss Function: Binary Cross-Entropy
- Optimizer: Adam
- Evaluation Metrics: Accuracy & Validation Loss

---

## Key Challenges

### Underfitting (RNN)
- Model failed to capture meaningful patterns
- Low performance on training and validation data

### Overfitting (LSTM & GRU)
- High training accuracy
- Increasing validation loss after few epochs

---

## Techniques Applied

### 1. Fixing Underfitting in RNN
- Reduced dropout to allow better learning
- Reduced sequence length (200 → 100)
- Reduced hidden size

Result: Improved learning and better feature extraction  

---

### 2. Fixing Overfitting in LSTM & GRU

#### Dropout Regularization
- Added dropout after embedding layer
- Increased dropout values
- Prevented reliance on specific neurons

#### Reducing Model Capacity
- Reduced hidden size and number of layers
- Prevented memorization of training data

#### Gradient Clipping
- Used `clip_grad_norm_()`
- Stabilized training by controlling exploding gradients

#### Learning Rate Scheduler
- Used `ReduceLROnPlateau`
- Reduced learning rate when validation loss plateaued

#### Early Stopping
- Stopped training when validation stopped improving
- Prevented unnecessary overfitting

Result: More stable validation curves and improved generalization  

---

## Ensemble Learning

After improving individual models, ensemble methods were applied:

- Hard Voting  
- Soft Voting  
- **Weighted Voting (Best Performance)**  

### Why Weighted Voting Worked Best?
- Assigns higher importance to better-performing models  
- Produces more reliable and robust predictions  

Final model achieved improved accuracy and stability  

---

## Model Performance 

### Before Improvements
| Model | Accuracy |
|------|----------|
| RNN  | 49.40% |
| LSTM | 72.10% |
| GRU  | 79.05% |

---

### After Improvements
| Model | Accuracy |
|------|----------|
| RNN  | 56.45% |
| LSTM | 69.60% |
| GRU  | **83.70%** |
| Ensemble (Weighted) | **83.45%** |
| Ensemble (Soft Voting) | 82.60% | 
| Ensemble (Hard Voting) | 76.85% |


---

## Key Learnings
- RNN struggles with long-term dependencies  
- LSTM & GRU are prone to overfitting  
- Regularization is critical in deep learning  
- Validation metrics are more important than training accuracy  
- Ensemble methods significantly improve performance  
