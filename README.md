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
* `pip install azure-storage-blob`
* Create a new (your choice).py file

* **Before we start we need our Account Access Key**
* ![InkedBlobstorageConnectString_LI](https://user-images.githubusercontent.com/81914415/113557499-c55b5780-9606-11eb-817b-f3f2a8a629e7.jpg)

* **We are going to use the library to connect our blobstorage that's why we need to import;**
* `from azure.storage.blob import BlobClient, BlobServiceClient, ContainerClient`
* `import os`

* **We need to create the BlobServiceClient object which will be used to create a container client.**
* `connect_str = 'YOUR_CONNECTION_STRING'`
* `PROJECT = BlobServiceClient.from_connection_string(connect_str)`

* **Create a name for the container**
* `container_name = 'NAME_YOUR_CONTAINER'`

* **Create the container**
* `container_client = PROJECT.create_container(container_name)`

* **Create a local directory to hold blob data**
* `local_path = "./data"`
* `os.mkdir(local_path)`

* **Create a file in the local data directory to upload and download**
* `local_file_name = container_name + ".txt"`
* `upload_file_path = os.path.join(local_path, local_file_name)`

* **Write text to the file**
* `file = open(upload_file_path, 'w')`
* `file.write("Hello, World! We can create a new text here and we can upload this file.")`
* `file.close()

* **Create a blob client using the local file name as the name for the blob**
* `project_client = PROJECT.get_blob_client(container=container_name, blob=local_file_name)`

* **Upload the created file**
* `with open(upload_file_path, "rb") as data:`
    *  `      project_client.upload_blob(data)`

* **IMPORTANT NOTE**
* `ErrorCode:ContainerBeingDeleted` If you get this error, you need to change the container name.
* This caused if you delete the container and recreate.
