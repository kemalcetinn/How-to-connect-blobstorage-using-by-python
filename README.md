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

* **We need to import the library to create, upload and download the blobstorage;**
* `from azure.storage.blob import BlobClient, ContainerClient`

* **We can specify connection string and container name to make easier.**
* `connection_string = "YOUR_CONNECTION_STRING"`
* `container_name = "YOUR_CONTAINER_NAME"`

* **Create the container**
* `container_client = ContainerClient.from_connection_string(conn_str=connection_string, container_name=container_name)`
* `container_client.create_container()`

* **Uploading a blob**
* `blob = BlobClient.from_connection_string(conn_str=connection_string, container_name=container_name, blob_name="BLOB_NAME_YOUR_CHOICE")`
* `with open("./<YOUR_FILE_NAME>.txt", "rb") as data:`
*    `blob.upload_blob(data)`
        
*![uploadblobfile](https://user-images.githubusercontent.com/81914415/113784504-3baea580-973e-11eb-82d5-1fc62f3b60dd.jpg)

             
* **Downloading a blob**
* `blob = BlobClient.from_connection_string(conn_str=connection_string, container_name=container_name, blob_name="BLOB_NAME")`
* `with open("./<YOUR_FILE_NAME>..txt", "wb") as x:`
*       `blob_data = blob.download_blob()`
*       `blob_data.readinto(x)`
     
*![downloadblobfile](https://user-images.githubusercontent.com/81914415/113784532-4832fe00-973e-11eb-8dea-01f34722b34c.jpg)

* **List the blobs in your container**
*`container = ContainerClient.from_connection_string(conn_str="my_connection_string", container_name=container_name)`

*`blob_list = container.list_blobs()`
* `for blob in blob_list:`
*    `print(blob.name + '\n')`

* ![listing](https://user-images.githubusercontent.com/81914415/113784937-ddce8d80-973e-11eb-92bb-cdc41b215919.jpg)


* **IMPORTANT NOTE**
* `ErrorCode:ContainerBeingDeleted` If you get this error, you need to change the container name.
* This error is caused when you delete the container and recreate it.
