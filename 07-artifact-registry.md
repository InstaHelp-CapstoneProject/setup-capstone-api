# Setup Cloud Artifact Registry for Capstone Project

Follow these steps to configure your Artifact Regitry for the InstaHelp application.

---

## Steps to Set Up Cloud Artifact Registry

### 1. Create a Repository

1. Go to the [Google Cloud Console](https://console.cloud.google.com).
2. Navigate to **Artifact Registry**.
3. Click **Create Repository**.
4. Fill in the following details:
    - **Name**: `capstone`
    - **Format**: Choose **Docker**.
    - **Region**: Select **asia-southeast2 (Jakarta)**.
5. Click **Create** to create the repository.

---

## Usage

Once the repository is created, you can push Docker images to it by tagging your images appropriately and using `gcloud` or Docker commands to upload them.
