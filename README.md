# MongoDB Backup to Azure Blob Storage

This bash script automates the process of backing up a MongoDB database and uploading the backup files to Azure Blob Storage.

## Prerequisites

- Linux VM.
- MongoDB is installed and running on the VM.
- The Azure CLI is installed and configured with the necessary permissions to access the storage account.

## Setup

- **Create an Azure Blob Storage container:**
Before running the script, create a new Azure Blob Storage container where you want to store the MongoDB backups.

- **Replace the variables in the script with your actual values:**
Open the script (`backup_script.sh`) and replace the following variables with your actual Azure Blob Storage and MongoDB configuration:

```bash
storage_account_name="your_storage_account_name"
container_name="your_container_name"
source_directory="/var/backups/mongobackups/$(date +'%m-%d-%y')"
destination_directory="mongobackups/$(date +'%Y-%m-%d')"
azure_connection_string="your_azure_connection_string"
