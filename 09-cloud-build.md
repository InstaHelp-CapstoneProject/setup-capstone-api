# Setup Cloud Build for Capstone Project

Follow these steps to configure your Cloud Build for the InstaHelp application.

---

## Steps to Set Up Cloud Build

steps:

# Step 1: Build the Docker image

-   name: "gcr.io/cloud-builders/docker"
    args:
    [
    "build",
    "-t",
    "asia-southeast2-docker.pkg.dev/capstone-443613/instahelp/instahelp-api",
    ".",
    ]

# Step 2: Push the Docker image to Artifact Registry

-   name: "gcr.io/cloud-builders/docker"
    args:
    [
    "push",
    "asia-southeast2-docker.pkg.dev/capstone-443613/instahelp/instahelp-api",
    ]

# Step 3: Deploy the image to Cloud Run

-   name: "gcr.io/google.com/cloudsdktool/cloud-sdk"
    args: - "gcloud" - "run" - "deploy" - "instahelp-api" - "--image" - "asia-southeast2-docker.pkg.dev/capstone-443613/instahelp/instahelp-api" - "--platform" - "managed" - "--region" - "asia-southeast2" - "--allow-unauthenticated"
    options:
    logging: CLOUD_LOGGING_ONLY
    images:
-   "asia-southeast2-docker.pkg.dev/capstone-443613/instahelp/instahelp-api"