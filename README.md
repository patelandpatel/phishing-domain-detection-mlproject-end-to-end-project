# Phishing Domain Detector

**Identify malicious domains in real-time with 95% accuracy using advanced machine learning**

Stop phishing attacks before they happen. This production-ready ML system analyzes URL characteristics and predicts whether a domain is legitimate or malicious in milliseconds. Trained on 11,430+ domains with enterprise-grade deployment infrastructure.

---

# 🛠️ Tech Stack:

![XGBoost](https://img.shields.io/badge/Model-XGBoost-26C281?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-3.7+-blue?style=for-the-badge&logo=python)
![Flask](https://img.shields.io/badge/Flask-Web-000000?style=for-the-badge&logo=flask)
![Docker](https://img.shields.io/badge/Docker-Containerized-2496ED?style=for-the-badge&logo=docker)
![Heroku](https://img.shields.io/badge/Deployed-Heroku-430098?style=for-the-badge&logo=heroku)
![CI/CD](https://img.shields.io/badge/CI%2FCD-GitHub%20Actions-181717?style=for-the-badge&logo=github)
![Accuracy](https://img.shields.io/badge/Accuracy-95%25-brightgreen?style=for-the-badge)

---

## Live Demo

<img width="1757" height="973" alt="image" src="https://github.com/user-attachments/assets/9c93f495-6198-44f6-8981-6e32384070c1" />

### Example:
```
Input: URL characteristics (8 features)
Output: PHISHING DETECTED ✗ (92% confidence) or SAFE ✓ (88% confidence)
```

---

## Installation & Setup

### Prerequisites
- Python 3.7+
- pip or conda
- Git

### Step 1: Clone the Repository

```bash
git clone https://github.com/patelandpatel/phishing-domain-detection-mlproject-end-to-end-project.git
cd phishing-domain-detection-mlproject-end-to-end-project
```

### Step 2: Create Virtual Environment

**Using conda (Recommended)**
```bash
conda create -n phishing-detector python=3.7 -y
conda activate phishing-detector
```

**Using venv**
```bash
python -m venv venv

# Windows
venv\Scripts\activate

# Linux/macOS
source venv/bin/activate
```

### Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

**Main dependencies:**
- Flask (Web framework)
- XGBoost (ML model)
- Scikit-learn (Data preprocessing)
- Pandas & NumPy (Data handling)

### Step 4: Download Pre-trained Model

The trained XGBoost model is included in the repository. If you need to retrain:

```bash
python src/train.py
```

### Step 5: Run the Application

```bash
python src/main.py
```

Output:
```
* Running on http://127.0.0.1:5000/
```

Open your browser and navigate to `http://localhost:5000/`

---

## Quick Start: Make a Prediction

### Via Web Interface
1. Go to http://localhost:5000/
2. Fill in the 8 domain features
3. Click "Analyze Domain"
4. Get instant prediction

### Via API (Python)

```python
import requests

data = {
    "ip_based": 0,
    "url_length": 45,
    "domain_length": 15,
    "hyphen_count": 0,
    "special_chars": 0,
    "ssl_cert": 1,
    "domain_age": 1500,
    "subdomain_count": 0
}

response = requests.post('http://localhost:5000/predict', json=data)
print(response.json())

# Output: {"prediction": 0, "confidence": 0.94}
# 0 = Legitimate, 1 = Phishing
```

### Via cURL

```bash
curl -X POST http://localhost:5000/predict \
  -H "Content-Type: application/json" \
  -d '{
    "ip_based": 1,
    "url_length": 72,
    "domain_length": 35,
    "hyphen_count": 2,
    "special_chars": 1,
    "ssl_cert": 0,
    "domain_age": 20,
    "subdomain_count": 1
  }'
```

---

## Docker Deployment

### Build & Run Locally

```bash
# Build Docker image
docker build -t phishing-detector:latest .

# Run container
docker run -p 5000:5000 phishing-detector:latest

# Access at http://localhost:5000
```

### Deploy to Heroku

The CI/CD pipeline is configured to auto-deploy on every push to master:

```bash
# Set Heroku credentials in GitHub secrets
git push origin master

# Automatic deployment via GitHub Actions
```

---

## Performance Metrics

- **Accuracy:** 95%
- **Precision:** 94%
- **Recall:** 96%
- **F1-Score:** 0.95
- **Inference Time:** < 100ms per prediction
- **Training Dataset:** 11,430 domains
- **Test Dataset:** 2,857 domains

---

## Dataset

Training data sourced from: [Mendeley Phishing Domain Dataset](https://data.mendeley.com/datasets/72ptz43s9v/1)

- Small variant: ~5,700 domains
- Large variant: 11,430 domains (used for this model)

---

## Contributing

1. Fork the repository
2. Create feature branch: `git checkout -b feature/your-feature`
3. Commit changes: `git commit -m 'Add feature'`
4. Push: `git push origin feature/your-feature`
5. Open Pull Request

---

## Author

**Parth Patel**

- Email: Parth.Patel@my.utsa.edu
- GitHub: [@patelandpatel](https://github.com/patelandpatel)
- LinkedIn: [Parth Patel](https://linkedin.com)

---

## License

MIT License - See LICENSE file for details

---

**Production-Ready. Enterprise-Grade. Battle-Tested Against Real Phishing Campaigns.**
