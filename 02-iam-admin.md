# Setup IAM & Admin for InstaHelp

Follow these steps to configure IAM for collaboration and security in the InstaHelp project on Google Cloud. This guide provides steps to grant user access and create service accounts.

--- 

## IAM Setup Steps

### 1. Granting Access to Users
1. Navigate to **IAM & Admin > IAM** in the Google Cloud Console.  
2. Click **Grant Access** under the **VIEW BY PRINCIPALS** section.  
3. Add the following accounts:  
   - **Account 1**:  
     - Enter **Principal**: `<partner_email>` (e.g., `c130b4kx1159@bangkit.academy`).  
     - Assign Role:  
       - **Basic > Owner**.  
   - **Account 2**:  
     - Enter **Principal**: `<partner_email>` (e.g., `c130b4ky3551@bangkit.academy`).  
     - Assign Roles:  
       - **Storage > Storage Admin**.  
       - **Storage > Storage Object Creator**.  
       - **Storage > Storage Object Viewer**.  
   - **Account 3**:  
     - Enter **Principal**: `<service_account_email>` (e.g., `instahelp-image-upload@capstone-443613.iam.gserviceaccount.com`).  
     - Assign Roles:  
       - **Storage > Storage Admin**.  
       - **Storage > Storage Object Creator**.  
       - **Storage > Storage Object Viewer**.  

4. Click **Save** to apply the changes.

---

### 2. Creating a Service Account
1. Navigate to **IAM & Admin > Service Accounts** in the Google Cloud Console.  
2. Click **Create Service Account**.  
3. Fill in the following details:  
   - **Name**: `instahelp-bucket-access` (example).  
   - **Service Account ID**: `instahelp-project-id` (e.g., `capstone-443613`).  
4. Click **Create and Continue**.  

5. **Grant Access to the Service Account**:  
   - Assign the Role:  
     - **Storage > Storage Admin**.  
6. Click **Done** to complete the setup.

---

## Additional Notes
- **Regular Audits**: Conduct regular audits of IAM settings to ensure security and remove unnecessary accounts or roles.  
- **Principle of Least Privilege**: Only grant the minimum necessary access for each user or service account.  
- **Custom Roles**: Create custom roles if specific permissions are required for the project.  

For more details, visit the [Google Cloud IAM Documentation](https://cloud.google.com/iam/docs).
