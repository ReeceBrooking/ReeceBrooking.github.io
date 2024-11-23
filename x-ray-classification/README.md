### Multi-Class Image Classification for X-Rays

This project was aimed at developing a machine learning model to assist doctors in diagnosing illnesses affecting patients' lungs. Using a dataset of labelled X-ray scans—categorised into pneumonia, COVID-19, or no illness—I constructed a multi-class classification model using a Convolutional Neural Network. The model outputs a diagnosis based on an input X-ray scan by leveraging tools like TensorFlow/Keras and various preprocessing, training, and evaluation techniques.

---

### Data Preparation and Preprocessing

The dataset comprised greyscale X-ray lung scans, an important consideration when preprocessing the data for neural network training. Grayscale images reduce the computational overhead compared to RGB images, but the large integer pixel values (0–255) posed a challenge for efficient learning. To address this, pixel values were normalised to a 0–1 range, ensuring faster convergence and improved numerical stability during training.

Additionally, image augmentation techniques such as flipping, rotation, and zooming were applied to enhance the dataset's variability and improve the model's generalisation to unseen data.

The dataset was split into training, validation, and testing sets, and the batch size parameter was varied during experiments. The batch size balances computational efficiency with gradient estimation quality: smaller batches speed up training but add variance to the learning curve, while larger batches provide smoother learning at the cost of higher computational demands.

---

### Model Design and Architecture

The model was designed as a sequential CNN architecture using Keras. Convolutional layers served as the backbone of the network, leveraging their ability to detect local patterns in image data, such as edges and objects. This approach was particularly effective because convolution operations reduce the size of input images while preserving critical features, enabling the model to focus on meaningful spatial patterns.

Max-pooling layers were incorporated to further reduce dimensionality, ensuring computational efficiency while retaining essential information. Dense layers processed the extracted features to classify the input image into one of the three categories. The final output layer used a softmax activation function, converting the model’s predictions into probabilities for each class.

To prevent overfitting, dropout layers were added, randomly setting a percentage of layer outputs to zero during training. This technique, which smooths out the learning curve, was critical for improving the model’s generalisation to validation and test data.

Key parameters included the choice of loss function, optimiser, and training settings:

- **Loss Function**: Categorical cross-entropy measured the divergence between the predicted and actual distributions, suitable for multi-class classification tasks.
- **Optimiser**: The Adam optimiser, with its adaptive learning rate, was employed to balance computational efficiency and gradient descent performance.
- **Batch Size**: Experimentation with different batch sizes allowed the balancing of computational cost and gradient estimation quality.
- **Early Stopping**: To avoid overfitting, the training process used early stopping, halting once the validation performance plateaued or degraded.

A flattening layer was used to transition from the convolutional layers to the fully connected layers.

---

### Training and Evaluation

The training process involved running the model over multiple epochs, where each epoch represented one complete pass through the dataset. To prevent overfitting, the number of epochs was determined dynamically using early stopping, ensuring training stopped when validation performance no longer improved. This technique also reduced unnecessary computation and improved training efficiency.

Evaluation metrics, including accuracy and AUC, were tracked across training and validation datasets to monitor performance over time. Accuracy provided a straightforward measure of correct predictions, while AUC assessed the model’s ability to distinguish between classes. These metrics were plotted using Matplotlib, allowing for visualisation of model performance.

The model achieved approximately 76% accuracy on the test set, demonstrating a solid baseline for multi-class classification. Analysis of precision, recall, and F1 scores through classification reports highlighted areas for improvement and a confusion matrix visualised patterns of misclassification.

Though it was shown by the F1 scores that “Normal” X-rays were less accurately diagnosed compared to others, contextually this is less important than a healthy diagnosis for a patient who is actually sick. Being able to reliably flag patients for disease allows for more efficient work by busy radiologists.

---

### Challenges and Solutions

The project encountered typical challenges in machine learning, particularly related to data and model optimisation.

- **Overfitting**: The model initially performed well on training data but struggled with validation data. Regularisation techniques, namely dropout layers, mitigated overfitting. Early stopping further ensured training ceased when performance plateaued.
- **Efficiency:** The initial model with three layers trained on too many parameters, leading to higher risk overfitting and longer model training. To combat this, convolutional and max pooling layers were implemented to reduce parameters and increase computational efficiency.

---

### Insights and Takeaways

This project offered insights into the practical application of machine learning for medical imaging. The process emphasised the importance of careful data preparation, from normalisation to augmentation, to ensure model readiness. The design and training of the CNN provided valuable experience in leveraging convolutional layers for image feature extraction. Experimenting with parameters such as batch size and regularisation techniques solidified my understanding of how these factors influence model performance.

Visualisation tools like loss and accuracy plots and confusion matrices proved invaluable for evaluating the model's performance and diagnosing issues like overfitting and misclassification. This iterative approach to refinement ensured that the model could generalise effectively to unseen data.

---

### Future Directions

Future improvements to the model could be implemented by expanding the dataset to include more diverse and balanced samples which would further enhance generalisation and robustness. Additionally, hyperparameter optimisation techniques, such as grid search or Bayesian optimisation, could refine model performance and efficiency.
