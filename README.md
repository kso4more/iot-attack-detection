# IoT Cyberattack Detection using Machine Learning

This project investigates the use of supervised machine learning techniques to classify different types of IoT cyberattacks using network traffic data.

## Dataset

The project uses the **Real-Time IoT Cyber Attack Dataset** from [Kaggle](https://www.kaggle.com/datasets/joebeachcapital/real-time-internet-of-things-rt-iot2022/data). 

- 123,117 samples
- 85 features
- 12 traffic classes

Attack examples include:

- ARP Poisoning
- DDoS Slowloris
- SYN Flood
- Nmap scanning attacks
- Metasploit SSH brute force

Normal traffic:

- MQTT Publish
- ThingSpeak
- Wipro IoT bulb traffic

## Methodology

The project follows a standard machine learning pipeline:

1. Data preprocessing
2. Feature engineering
3. Imbalance handling
4. Model training and tuning
5. Model evaluation

### Feature Engineering

Important features were derived from TCP flag behaviour:

- SYN/ACK ratio
- RST ratio

Highly correlated and low-information features were removed using:

- correlation filtering
- mutual information

Dimensionality was reduced using **PCA**.

## Models Evaluated

Three classifiers were evaluated:

- Logistic Regression
- Random Forest
- K-Nearest Neighbours (KNN)

Hyperparameter tuning was performed using **nested cross-validation with grid search**.

## Results

KNN achieved the best overall performance:

| Model | Accuracy | Precision | Recall | F1 |
|------|------|------|------|------|
| Logistic Regression | ~0.92 | ~0.93 | ~0.92 | ~0.92 |
| Random Forest | ~0.92 | ~0.92 | ~0.92 | ~0.92 |
| KNN | ~0.97 | ~0.98 | ~0.97 | ~0.97 |

Key findings:

- Oversampling improved performance, especially for KNN
- PCA significantly reduced training time with minimal accuracy loss
- TCP flag ratios were highly informative features

## Security Insights

The results demonstrate that machine learning can effectively classify IoT network attacks and may support automated intrusion detection systems in resource-constrained IoT environments.

However, rare attack types such as **ARP poisoning** remain difficult to detect due to limited protocol-level features and class imbalance.

## Technologies

- Python
- Scikit-learn
- Pandas
- NumPy
- Jupyter Notebook

## Author

Gin Lee  
