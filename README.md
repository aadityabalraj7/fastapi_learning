# Insurance Premium Prediction API

## Description

This is a FastAPI-based web API for predicting insurance premiums. It takes user inputs such as BMI, age group, lifestyle risk, city tier, income (in LPA), and occupation to provide premium predictions using a trained machine learning model.

## Features

- **Health Check Endpoint**: Monitor the API and model status.
- **Prediction Endpoint**: Accepts user data and returns premium predictions.
- **Input Validation**: Uses Pydantic schemas for robust data validation.
- **CORS Enabled**: Supports cross-origin requests.
- **Docker Support**: Easily deployable using Docker.

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/aadityabalraj7/fastapi_learning.git
   cd fastapi_learning
   ```

2. Create a virtual environment (optional but recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

### Running Locally

Start the FastAPI server:
```bash
uvicorn app:app --reload
```

The API will be available at `http://127.0.0.1:8000`.

### Using Docker

Build and run the Docker container:
```bash
docker build -t insurance-premium-api .
docker run -p 8000:8000 insurance-premium-api
```

## API Endpoints

### GET /
Returns a welcome message.

**Response:**
```json
{
  "message": "Insurance Premium Prediction API"
}
```

### GET /health
Provides health status and model information.

**Response:**
```json
{
  "status": "OK",
  "version": "1.0.0",
  "model_loaded": true
}
```

### POST /predict
Predicts the insurance premium based on user input.

**Request Body:**
```json
{
  "bmi": 25.0,
  "age_group": "30-40",
  "lifestyle_risk": "medium",
  "city_tier": "tier1",
  "income_lpa": 10.0,
  "occupation": "salaried"
}
```

**Response:**
```json
{
  "prediction": 15000.0,
  "model_version": "1.0.0"
}
```

## Project Structure

```
insurance-premium-prediction-fastapi/
├── app.py                 # Main FastAPI application
├── Dockerfile             # Docker configuration
├── requirements.txt       # Python dependencies
├── config/
│   └── city_tier.py       # City tier configurations
├── model/
│   └── predict.py         # Prediction logic and model loading
└── schema/
    ├── prediction_response.py  # Response schema
    └── user_input.py           # Input schema
```

## Requirements

- Python 3.11+
- FastAPI
- Uvicorn
- Pydantic
- Other dependencies listed in `requirements.txt`

## Contributing

1. Fork the repository.
2. Create a feature branch.
3. Make your changes.
4. Submit a pull request.

## License

This project is licensed under the MIT License.