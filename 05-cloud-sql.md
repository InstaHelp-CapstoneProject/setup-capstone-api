### Setup Cloud SQL for Capstone Project

Follow these steps to configure your VPC Network for the InstaHelp application.

---

1. **Create Instance**:
   - Navigate to the **Cloud SQL** section in Google Cloud Console.
   - Click **Create Instance**.

2. **Choose Database Type**:
   - Select **MySQL**.

3. **Fill in Instance Details**:
   - **Instance ID**: `capstone`
   - **Database Version**: `MySQL 8.0`
   - **Configuration**: Choose **Development**.
   - **Region**: `asia-southeast2 (Jakarta)` → Select **Single Zone**.

4. **Customize Your Instance**:
   - Click **Customize your instance** and configure the following:
     - **Machine Type**:
       - Select **Shared Core**.
       - **vCPU**: `1`
       - **Memory**: `0.614 GB`
     - **Storage**:
       - **Storage type**: `HDD`
       - **Storage capacity**: `10GB`
     - **Connections**:
       - **Instance IP assignment**: Select **Private IP**.
       - Uncheck **Public IP**.
     - **Data Protection**:
       - Uncheck **Enable deletion protection**.

5. **Create Instance**:
   - Review the settings and click **Create Instance**.

#### Instance Name:
- `instahelp-sql`
