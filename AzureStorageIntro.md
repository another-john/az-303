## Introduction To Azure Storage

1. Azure Storage Key Benefits:
  - Durablity
  - Hight availability
  - Encryption
  - Security
  - Scalability
  - Accessiblity

2. Azure Blob Storage
  - Overview
    - Provide Object storage for the cloud
    - Optimized to support massive amounts of unstructured data
    - Unstructured data is data that does not fit a specific data model
  - Usage:
    - host images and documents that you wish to serve up to a web browser
    - stream video or audio
    - store log fies
    - store backup data, archive data and data that needs to be analyzed by some on-prem process or Azure-hosted process
  - Structure 
    - Account->Container->Blob
    - Countainers are used to organize the blobs within the account, like directires in a file system
  - Types
    - Block Blobs
      - Can contain up to 4.7TB of text and binary data
      - Consist of blocks of data that can be managed individually
    - Append Blobs
      - Optimized for append operations
      - Good choice for logging data from virtual machines
    - Page Blobs
      - Used to store random access files up to 8TB in size
      - Typically used to store VHD files, which would serve as disks for Azure virtual machines

3. Azure Files
  - Server Message Block protocol : SMB
  - Overview
    - Fully managed file share system available in the cloud
    - Access through the typical SMB protocal
    - Mount file shares fomr Windwos, Linux, and MacOS machines that reside both on-prem and in the cloud
    - Cache file shares on Windows servers, using the Azure file sync service
    - Helps make data more accessible for remote offices
  - 

4. Azure Queue Storage
  - Designed for storing large numbers of messages used in communications between the different components of a distributed application
  - Messages can be acessed from anywhere in the world through authenticated calls via HTTP/HTTPS
  - Each queue message can be up to 64 KB in size
  - A typical queue can contain millions of messages

5. Azure Table Storage
  - Intended for the storage of structured NoSQL data
  - Offers a key/attribute store and a schema-less design
  - Schema-less design allows you to more easily adapt data to the needs of your business or application

6. Disk Storage
  - Managed block level storage volumes
  - Used to provide storage capabilities for virtual machines
  - Much like a physical disk that you would see in an on-prem server but virtualized
  - Available disk types include ultra disks, premium SSD disks standard SSD disks and standard HDD disks

7. Storage Account
  - General Purpose V2: Recommended for most scenarios that require Azure sotrage
  - General Purpose V1
  - Block Blob Storage: 
    - Premium performance for block blobs and append blobs
    - Used for situations where high transaction rates are in play
    - For scenarios that require low storage latency
  - File Storage: 
    - Files-only storage accounts
    - Feature high performance characteristics
    - Recommended for enterprise applications or high-performing applications
  - Blob Storage
    - A legact account used for blob-only storage
    - recommended to use General Purpose V2

8. Replication:
  - Locally-redundant storage : LRS
  - Zone-redundant storage : ZRS
  - Geo-redundant storage : GRS
  - Read-access geo-redundant storage : RA-GRS
  - Geo-zone-redundant storage : GZRS
  - Read-access geo-zone-redundant storage RA-GZRS