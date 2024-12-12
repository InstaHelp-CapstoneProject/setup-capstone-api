# Setup Cloud Storage for InstaHelp

Follow these steps to configure your Google Cloud Storage bucket for the InstaHelp application.

---

## 1. Create a Bucket
1. Go to the **Google Cloud Console**.
2. Navigate to **Cloud Storage > Buckets**.
3. Click **Create Bucket**.
4. Fill in the details:
   - **Name**: `instahelp`
   - **Location**: `asia-southeast2 (Jakarta)` (or your closest region)
   - **Storage class**: `Standard`
   - **Access control**: Select **Uniform**
5. Click **Create**.

---

## 2. Create Folders in the Bucket
1. Go to your `instahelp` bucket in **Cloud Storage**.
2. Use the **Create Folder** option to add the following folders:
   - `avatars/`
   - `incidents/`
   - `models/`
   - `vehicles/`

---

## 3. Configure Permissions
1. Go to the **Permissions** tab of the `instahelp` bucket.
2. Click **Grant Access** and configure the roles:
   - Add the **Principal** (e.g., your partner's account or other accounts).
     - Role: **Basic > Owner**
   - Add another account for repository access:
     - Role: **Source > Source Repository Reader**
   - Add another account for storage management:
     - Role: **Storage > Storage Admin**
3. Save the changes.

---

## 4. Create a Service Account
1. Navigate to **IAM & Admin > Service Accounts** in the Google Cloud Console.
2. Click **Create Service Account**.
3. Fill in the details:
   - **Name**: `bucketaccess`
   - **Service Account ID**: `capstone-project-arahku`
4. Click **Create and Continue**.
5. Grant the service account access:
   - Role: **Storage > Storage Admin**
6. Finish the process by clicking **Done**.

---

## 5. Verify Public Access (Optional)
1. Check the **Public Access** status of the bucket.
2. Remove unwanted permissions to avoid exposing sensitive data.

---

You now have a configured Cloud Storage bucket for InstaHelp!
