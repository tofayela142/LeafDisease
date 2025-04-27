
# Deployment Guide for Leaf Disease Detection System

This document provides step-by-step instructions to deploy the **Leaf Disease Detection System** on Google Cloud Platform (GCP).

---

## Prerequisites

- A Google Cloud Platform (GCP) account
- Google Cloud SDK installed locally
- Docker installed
- Billing enabled on GCP project
- Basic understanding of Docker, GCP (Cloud Run / App Engine)

---

## 1. Model Preparation

Ensure your trained TensorFlow model is saved properly.

Example:

```python
model.save('models/leaf_disease_model')
```

If using TensorFlow Lite for mobile, export it as `.tflite` format.

---

## 2. Dockerizing the Backend

Create a `Dockerfile` for TensorFlow Serving:

```dockerfile
FROM tensorflow/serving

# Copy the exported model into the container
COPY models/leaf_disease_model /models/leaf_disease_model

ENV MODEL_NAME=leaf_disease_model
```

If you want to serve a **FastAPI** app (custom logic), you'll need a separate `Dockerfile` for FastAPI.

---

## 3. Build and Push Docker Image

Authenticate Docker to Google Container Registry:

```bash
gcloud auth configure-docker
```

Build the Docker image:

```bash
docker build -t gcr.io/YOUR_PROJECT_ID/leaf-disease-backend .
```

Push it to GCP:

```bash
docker push gcr.io/YOUR_PROJECT_ID/leaf-disease-backend
```

---

## 4. Deploy to Google Cloud Run

Deploy the backend container:

```bash
gcloud run deploy leaf-disease-backend \
  --image gcr.io/YOUR_PROJECT_ID/leaf-disease-backend \
  --platform managed \
  --region YOUR_REGION \
  --allow-unauthenticated
```

GCP will generate a public URL for your API.

---

## 5. Deploy Frontend (ReactJS)

### Build the ReactJS app

```bash
cd frontend
npm install
npm run build
```

### Host Frontend

Options:
- **Firebase Hosting** (Recommended for React)
- **GCP App Engine**
- **GCP Storage Bucket (Static Hosting)**

Example using Firebase:

```bash
npm install -g firebase-tools
firebase login
firebase init
firebase deploy
```

---

## 6. Update API URL in Frontend

After backend deployment, update your ReactJS frontend to point to the live backend URL.

Example (`frontend/src/config.js`):

```javascript
export const API_BASE_URL = "https://your-cloud-run-url.a.run.app";
```

Rebuild your frontend after changing the API URL.

---

## Project Deployment Flow

```plaintext
User → ReactJS Frontend → FastAPI Backend (Cloud Run) → TensorFlow Serving Model
```

---

## Important Notes

- Use environment variables to manage different stages (development, production).
- Monitor GCP resource usage to avoid unexpected charges.
- Consider adding authentication for production deployments.

---


