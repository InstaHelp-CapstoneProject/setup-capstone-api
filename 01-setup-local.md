# InstaHelp Setup Guide

This guide provides step-by-step instructions for setting up the InstaHelp project locally.

---

## Prerequisites

Ensure you have the following installed:

-   **Python 3.x**: Recommended version is Python 3.12.8 or later.
-   **Git**: For cloning the repository.
-   **Flask**: For running the project.
-   **MySQL**: For database setup.

---

## Setup Instructions

### 1. Clone the Repository

Clone the InstaHelp repository to your local machine:

```bash
git clone https://github.com/InstaHelp-CapstoneProject/capstone-api.git
cd instahelp
```

### 2. Create a Virtual Environment

Set up a Python virtual environment:

```bash
python -m venv venv
```

### 3. Activate the Virtual Environment

Activate the virtual environment (for PowerShell):

```bash
venv\Scripts\activate
```

### 4. Install Dependencies

Install the required Python packages:

```bash
pip install -r requirements.txt
```

### 5. Database Setup

#### Create the Database

Open your MySQL client or GUI tool and create a new database named `instahelp`:

```sql
CREATE DATABASE instahelp;
```

Ensure the database user is `root` with no password.

#### Initialize the Database

Run the following commands within the active virtual environment:

```bash
flask db init
flask db migrate -m "migrate all"
flask db upgrade
```

#### Seed the Database

Populate the database with initial data:

```bash
flask seed run
```

---

### 6. Development Mode

Enable Flask development mode by setting the following environment variables:

```bash
$env:FLASK_DEBUG="1"
$env:FLASK_ENV="development"
$env:PYTHONDONTWRITEBYTECODE=1
```

---

### 7. Run the Application

Start the Flask application:

```bash
flask run
```

The application should now be running at http://localhost:5000.

---

## Troubleshooting

-   If `flask` commands are not recognized, ensure the virtual environment is activated.
-   Verify that MySQL is running, and the `instahelp` database exists.
