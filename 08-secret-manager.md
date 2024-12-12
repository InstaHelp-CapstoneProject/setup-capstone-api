# Storing Service Account Credentials in Google Cloud Secret Manager for Capstone Project

Follow these steps to configure your `credentials.json` for the InstaHelp application and securely store your credentials.json file in Google Cloud's Secret Manager.

---

### Step 1: Enable Secret Manager API

Before you can store secrets, you need to enable the Secret Manager API for your project.

1. Go to the [Google Cloud Console](https://console.cloud.google.com/).
2. Navigate to **APIs & Services > Library**.
3. Search for **Secret Manager API**.
4. Click **Enable**.

### Step 2: Create a Secret to Store the Credentials

1. Go to the [Secret Manager page](https://console.cloud.google.com/security/secret-manager).
2. Click **Create Secret**.
3. In the **Secret Name** field, enter `SERVICE_ACCOUNT`.
4. In the **Secret Value** field, upload or paste the contents of your `credentials.json` file.
5. Click **Create**.

### Step 3: Set IAM Permissions for Secret Manager

To access the stored credentials, you need to set the correct permissions for the Secret Manager.

1. Go to the **IAM & Admin** section in the Google Cloud Console.
2. Click **Add** to add a new member.
3. In the **New members** field, enter the service account or user that needs access to the secret.
4. Assign the **Secret Manager Secret Accessor** role to this member.
5. Click **Save**.

### Step 4: Access the Secret Programmatically

You can access the secret using the `gcloud` CLI or the Google Cloud SDK in your application code.

#### Using `gcloud` CLI:

```bash
gcloud secrets versions access latest --secret="SECRETS/SERVICE_ACCOUNT"
```
