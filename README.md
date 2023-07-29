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
```

## Features

- Automated MongoDB backup for multiple databases.
- Uploads the backups to Azure Blob Storage for secure storage.
- Supports configuration via a `config.ini` file for easy customization.
- Provides logging to track the backup process and any potential errors.

## Script Explanation

The script performs the following steps:

- It defines the necessary variables like storage_account_name, container_name, etc.
- The source_directory is set to the current date in the format "MM-DD-YY".
- The destination_directory is set to "mongobackups/YYYY-MM-DD" where "YYYY-MM-DD" is the current date.
- The azure_connection_string is the connection string obtained from your Azure account.
- It uses the Azure CLI command az storage blob upload-batch to upload the backup files to Azure Blob Storage.

## Usage

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/your-repo.git

2. Configure the script:
   - Create a config.ini file in the same directory as the script (backup_script.sh).
   - Add your MongoDB and Azure configuration to the config.ini

3. Run the script:
   - Ensure you've set the appropriate permissions to execute the script: chmod +x backup_script.sh.

   - To run the script, simply execute it in the terminal:

   ```bash
   ./backup_script.sh
   ```

   - The script will perform a backup of the specified MongoDB databases and upload them to Azure Blob Storage.

4. Check the log:
   - The script will create a backup.log file in the same directory, which logs the backup process and any errors that occur

## Note

- Make sure to schedule the script to run at regular intervals using a cron job or any other scheduling method to maintain up-to-date backups.

## Contributing

Pull requests are welcome. For major changes or enhancements, please open an issue first to discuss what you want to change.
