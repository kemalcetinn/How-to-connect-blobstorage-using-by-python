# How-to-connect-blobstorage-using-by-python

## Requirements ##
* [Azure account with active subscription.](https://azure.microsoft.com/en-us/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=docs&utm_campaign=visualstudio)
* Storage Account

# Create a Storage Account by using Azure Portal
* Storage Account
* ![InkedAzureStorageAccountOpening_LI](https://user-images.githubusercontent.com/81914415/113512383-1454ae80-956d-11eb-8d2c-d56d842a0ec4.jpg)

* You need to follow the arrows and fill it.

# Create a BLOBSTORAGE by using Python #
* Open your editor terminal and install the Azure Storage Blob library for Python
* Create a new .py file, you can name it whatever you want.

* `pip install azure-storage-blob`
* Before we start we need our Account Access Key
* ![InkedBlobstorageConnectString_LI](https://user-images.githubusercontent.com/81914415/113557499-c55b5780-9606-11eb-817b-f3f2a8a629e7.jpg)

* We are going to use the library to connect our blobstorage that's why we need to import.
* `from azure.storage.blob import BlobClient, BlobServiceClient, ContainerClient`
* `import os`

* We need to create the BlobServiceClient object which will be used to create a container client.
* `connect_str = 'YOUR_CONNECTION_STRING'`
* `blob = BlobServiceClient.from_connection_string(connect_str)`

* Create a name for the container
* `container_name = 'projectblob'`
* Create the container
* `container_client = blob.create_container(container_name)`
* Create a local directory to hold blob data
* `local_path = "./data"`
* `os.mkdir(local_path)`

*  Create a file in the local data directory to upload and download
 `local_file_name = 'denemetutorial2' + ".txt"`
 `upload_file_path = os.path.join(local_path, local_file_name)`
