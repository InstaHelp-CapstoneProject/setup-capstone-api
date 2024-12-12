# VPC Network Setup for InstaHelp

Follow these steps to configure your VPC Network for the InstaHelp application.

---

## 1. Create a VPC Network

### Option 1: Using Google Cloud Console

1. Navigate to **VPC Network > VPC Networks** in the Google Cloud Console.
2. Click **Create VPC Network** and fill in the following details:
    - **Name**: `instahelp-vpc`
    - **Subnet creation mode**: Select **Custom**.
3. Add a custom subnet:
    - **Subnet name**: `subnet-instahelp`
    - **Region**: `asia-southeast2`
    - **IP address range (CIDR)**: `10.184.0.0/20`
4. Click **Create**.

### Option 2: Using Google Cloud Shell

Run the following commands in the **Cloud Shell**:

```bash
gcloud compute networks create instahelp-vpc --project=capstone-project-arahku --subnet-mode=custom --mtu=1460 --bgp-routing-mode=regional

gcloud compute networks subnets create subnet-jakarta-staging --project=capstone-project-arahku --range=10.184.0.0/20 --stack-type=IPV4_ONLY --network=instahelp-vpc --region=asia-southeast2
```

## 2. Setup Firewalls

### 2.1 Allow Service Traffic (TCP:5000)

#### Using Console:

1. Navigate to **Firewall Rules** and click **Create Firewall Rule**.
2. Fill in the following details:
    - **Name**: `allow-service-instahelp`
    - **Network**: `instahelp-vpc`
    - **Target**: `Specified target tags`
    - **Target tags**: `service`
    - **Source IP ranges**: `0.0.0.0/0`
    - **Protocols and ports**: Check **TCP** and enter `5000`.
3. Click **Create**.

#### Using Cloud Shell:

```bash
gcloud compute firewall-rules create allow-service-instahelp \
    --direction=INGRESS \
    --priority=1000 \
    --network=instahelp-vpc \
    --action=ALLOW \
    --rules=tcp:5000 \
    --source-ranges=0.0.0.0/0 \
    --target-tags=service
```

### 2.2 Allow SSH Traffic (TCP:22)

#### Using Console:

1. Navigate to **Firewall Rules** and click **Create Firewall Rule**.
2. Fill in the following details:
    - **Name**: `allow-ssh`
    - **Network**: `instahelp-vpc`
    - **Target**: `Specified target tags`
    - **Target tags**: `ssh`
    - **Source IP ranges**: `0.0.0.0/0`
    - **Protocols and ports**: Check **TCP** and enter `22`.
3. Click **Create**.

#### Using Cloud Shell:

```bash
gcloud compute firewall-rules create allow-ssh \
    --direction=INGRESS \
    --priority=1000 \
    --network=instahelp-vpc \
    --action=ALLOW \
    --rules=tcp:22 \
    --source-ranges=0.0.0.0/0 \
    --target-tags=ssh
```

### 2.3 Allow Internal Traffic

#### Using Console:

1. Navigate to **Firewall Rules** and click **Create Firewall Rule**.
2. Fill in the following details:
    - **Name**: `allow-internal`
    - **Network**: `instahelp-vpc`
    - **Target**: `Specified target tags`
    - **Target tags**: `allow-internal`
    - **Source IP ranges**: `10.184.0.0/20`
    - **Protocols and ports**:
        - Check **TCP** and enter `0-65535`.
        - Check **UDP** and enter `0-65535`.
        - Check **Other protocols** and enter `icmp`.
3. Click **Create**.

#### Using Cloud Shell:

```bash
gcloud compute firewall-rules create allow-internal \
    --direction=INGRESS \
    --priority=1000 \
    --network=instahelp-vpc \
    --action=ALLOW \
    --rules=tcp:0-65535,udp:0-65535,icmp \
    --source-ranges=10.184.0.0/20 \
    --target-tags=allow-internal
```
