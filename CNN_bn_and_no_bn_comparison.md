## Experiment: Effects of Batch Normalization in Convolutional Neural Networks

This experiment investigates the impact of Batch Normalization (BN) on:
1. **Convergence Speed** of the network during training.
2. **Permissible Learning Rates** for stable and effective training.
3. **Overall Model Performance** in terms of accuracy and loss.

## Experiment Setup

### Datasets
- **MNIST**: A dataset of 28x28 pixel grayscale images of handwritten digits, containing 60,000 training samples and 10,000 test samples.

### Models
1. **CNN without Batch Normalization**: Standard convolutional layers followed by activation and pooling layers.
2. **CNN with Batch Normalization**: Same architecture but with Batch Normalization layers after each convolutional layer.

### Training Parameters
- **Epochs**: 10
- **Optimizer**: Adam
- **Learning Rates Tested**: 0.001, 0.005, 0.01

## Results

### Learning Rate = 0.001

| Model                    | Epoch 1 Loss | Epoch 10 Loss | Epoch 1 Accuracy | Epoch 10 Accuracy | Test Accuracy |
|--------------------------|--------------|---------------|------------------|--------------------|---------------|
| **Without BN**           | 0.1943       | 0.0078       | 94.09%          | 99.74%            | 99.05%        |
| **With BN**              | 0.1121       | 0.0059       | 97.45%          | 99.81%            | 99.15%        |

**Observations**:
- **Convergence Speed**: The model with BN converged faster, showing significant accuracy and loss improvement within the first few epochs.
- **Performance**: With BN, the model achieved slightly higher test accuracy and lower final loss, indicating improved generalization.

### Learning Rate = 0.005

| Model                    | Epoch 1 Loss | Epoch 10 Loss | Epoch 1 Accuracy | Epoch 10 Accuracy | Test Accuracy |
|--------------------------|--------------|---------------|------------------|--------------------|---------------|
| **Without BN**           | 0.0190       | 0.0113       | 99.59%          | 99.79%            | 98.79%        |
| **With BN**              | 0.0046       | 0.0020       | 99.84%          | 99.94%            | 99.17%        |

**Observations**:
- **Learning Rate Stability**: BN allowed the model to handle the larger learning rate without significant instability, unlike the model without BN, which had noticeable fluctuations.
- **Performance**: The model with BN continued to perform better in test accuracy and maintained lower final training loss.

### Learning Rate = 0.01

| Model                    | Epoch 1 Loss | Epoch 10 Loss | Epoch 1 Accuracy | Epoch 10 Accuracy | Test Accuracy |
|--------------------------|--------------|---------------|------------------|--------------------|---------------|
| **Without BN**           | 0.0727       | 0.0383       | 97.86%          | 99.14%            | 98.48%        |
| **With BN**              | 0.0550       | 0.0100       | 98.28%          | 99.69%            | 98.97%        |

**Observations**:
- **Convergence and Stability**: Without BN, the model showed slower convergence and higher loss at the larger learning rate, indicating training instability. With BN, the model trained more smoothly and with a higher final accuracy.
- **Performance**: The BN model achieved better performance, although the difference was less pronounced than with lower learning rates.

## Interpretation

1. **Accelerated Convergence**:
   - Batch Normalization accelerates convergence across all learning rates, showing faster loss reduction and reaching higher accuracy within fewer epochs.

2. **Larger Learning Rates**:
   - The presence of BN permitted the use of larger learning rates (e.g., 0.005 and 0.01) without significant instability. This is likely due to BN's effect of reducing internal covariate shifts, making gradient updates more stable.

3. **Improved Model Performance**:
   - Models trained with BN achieved slightly better final accuracy and generalization across all learning rates, suggesting that BN may add a regularization effect that enhances performance.

## Conclusion
Batch Normalization is an effective technique for:
- **Accelerating convergence** during training by normalizing activations.
- **Enabling the use of larger learning rates** without destabilizing training.
- **Improving model performance** with slight accuracy and loss improvements on test data.

In summary, Batch Normalization is a valuable addition to neural networks, especially when training with higher learning rates or when convergence speed is critical.
