# CloudTier S3 Storage Tiering demo
The CloudTier SDK integrates S3 Intelligent-Tiering cloud storage with on-premise storage systems seamlessly, creating a hybrid storage environment.  So it allows on-premise applications to access S3 file objects transparently, just as they would access on-premise regular files. There is no interruption to move or restore your on-premise files to/from the cloud storage, so you don’t need to change your existing applications and infrastructure to be compatible with the cloud environment.

The CloudTier S3 demo is a C# demo project, it demonstrates how to connect the S3 storage from your on-premise storage, and how to generate the test files in on-premise storage and S3 storage. It demonstrates how to browse and read the S3 files as a local regular files.
![CloudTier S3 Storage Tiering Demo](https://www.easefilter.com/images/CloudTierS3Demo.PNG)
When you launch the CloudTier S3 demo, it will generate a few test stub files in your application folder’s sub folder “TestStubFolder”, the file’s content was stored in the sub folder “TestSourceFolder”, when you read the stub file, the file content will be retrieved from the source file, if your file content was stored in the S3 storage, then it will be retrieved from the S3, it can demonstrate how the storing tiering is working with this simple project.

A stub file looks and acts like a regular file. It has the same file attributes with the original physical file (file size, creation time, last write time, last access time). It also keeps the original file’s security. The difference between the stub file and the normal physical file is the stub file doesn’t take any physical space, looks like a 0 kb file.
![Stub file](https://www.easefilter.com/images/stub.png)

## How to run the CloudTierS3 demo?

1.	Excluded the process Id from the filter driver: the excluded processes can’t access the stub file. It can prevent the unwanted processes from downloading the data from the cloud storage.        
2.	Filter connection threads: the number of the threads to handle the read requests of the stub files.
3.	Connection timeout: the maximum time of the filter driver waiting for the data return from your application.
4.	Cache folder path: the folder to store the cache files which download from the cloud storage.
5.	The return data type: a. return block data on read: return the block of the requested read data if you have the block of the data. b. return cache file on read: return the cache file name if the whole file was downloaded. c. rehydrate file on first read: the file was downloaded to the cache folder, and the stub file will be rehydrated to the regular file.
6.	Amazon S3 site settings: before you can test the S3 connection, you need to have an S3 account with the access key, then you can create a test bucket with the intelligent tiering enabled in Amazon S3 console. 
7.	To browse the files in s3 or upload/download the files to/from S3, you can go to the S3 explorer. After the files were uploaded to the S3, then you can create the stub file from the S3 explorer.
![S3 File Explorer](https://www.easefilter.com/images/s3explorer.png)
8.	Read the S3 files: after the files were uploaded to the S3 cloud storage, you can replace your original file with the stub file based on your retention policies. You can create S3 stub file in S3 explorer. For example, to read the stub file by copying the stub file to another folder, you will see the S3 file will be downloaded to the cache folder from the S3 storage, after that the cache file will be returned to your local file system through the CloudTier filter driver, then the read request to the S3 file will be completed successfully. 

## EaseFilter File System Filter Driver SDK Reference
| Product Name | Description |
| --- | --- |
| [Storage Tiering SDK](https://www.easefilter.com/cloud/storage-tiering-sdk.htm) | EaseFilter Storage Tiering Filter Driver SDK Introduction. |
| [File Monitor SDK](https://www.easefilter.com/kb/file-monitor-filter-driver-sdk.htm) | EaseFilter File Monitor Filter Driver SDK Introduction. |
| [File Control SDK](https://www.easefilter.com/kb/file-control-file-security-sdk.htm) | EaseFilter File Control Filter Driver SDK Introduction. |
| [File Encryption SDK](https://www.easefilter.com/kb/transparent-file-encryption-filter-driver-sdk.htm) | EaseFilter Transparent File Encryption Filter Driver SDK Introduction. |
| [Registry Filter SDK](https://www.easefilter.com/kb/registry-filter-drive-sdk.htm) | EaseFilter Registry Filter Driver SDK Introduction. |
| [Process Filter SDK](https://www.easefilter.com/kb/process-filter-driver-sdk.htm) | EaseFilter Process Filter Driver SDK Introduction. |
| [EaseFilter SDK Programming](https://www.easefilter.com/kb/programming.htm) | EaseFilter Filter Driver SDK Programming. |

## EaseFilter SDK Sample Projects
| Sample Project | Description |
| --- | --- |
| [CloudTier Storage Tiering Demo](https://www.easefilter.com/cloud/cloudtier-storage-tiering-demo.htm) | A HSM File System Filter Driver Demo. |
| [CloudTier S3 Intelligent Tiering Demo](https://www.easefilter.com/cloud/cloudtier-s3-intelligent-tiering-demo.htm) | CloudTier S3 Intelligent Tiering Demo. |
| [Amazon S3 File Explorer Demo](https://www.easefilter.com/cloud/s3-browser-demo.htm) | Amazon S3 File Explorer Demo. |
| [Auto File DRM Encryption](https://www.easefilter.com/kb/auto-file-drm-encryption-tool.htm) | Auto file encryption with DRM data embedded. |
| [Transparent File Encrypt](https://www.easefilter.com/kb/AutoFileEncryption.htm) | Transparent on access file encryption. |
| [Secure File Sharing with DRM](https://www.easefilter.com/kb/DRM_Secure_File_Sharing.htm) | Secure encrypted file sharing with digital rights management. |
| [File Monitor Example](https://www.easefilter.com/kb/file-monitor-demo.htm) | Monitor file system I/O in real time, tracking file changes. |
| [File Protector Example](https://www.easefilter.com/kb/file-protector-demo.htm) | Prevent sensitive files from being accessed by unauthorized users or processes. |
| [FolderLocker Example](https://www.easefilter.com/kb/FolderLocker.htm) | Lock file automatically in a FolderLocker. |
| [Process Monitor](https://www.easefilter.com/kb/Process-Monitor.htm) | Monitor the process creation and termination, block unauthorized process running. |
| [Registry Monitor](https://www.easefilter.com/kb/RegMon.htm) | Monitor the Registry activities, block the modification of the Registry keys. |
| [Secure Sandbox Example](https://www.easefilter.com/kb/Secure-Sandbox.htm) |A secure sandbox example, block the processes accessing the files out of the box. |
| [FileSystemWatcher Example](https://www.easefilter.com/kb/FileSystemWatcher.htm) | File system watcher, logging the file I/O events. |

## Filter Driver Reference

* [Understand MiniFilter Driver](https://www.easefilter.com/kb/understand-minifilter.htm)
* [Understand File I/O](https://www.easefilter.com/kb/File_IO.htm)
* [Understand I/O Request Packets(IRPs)](https://www.easefilter.com/kb/understand-irps.htm)
* [Filter Driver Developer Guide](https://www.easefilter.com/kb/DeveloperGuide.htm)
* [MiniFilter Filter Driver Framework](https://www.easefilter.com/kb/minifilter-framework.htm)
* [Isolation Filter Driver](https://www.easefilter.com/kb/Isolation_Filter_Driver.htm)

## Support
If you have questions or need help, please contact support@easefilter.com 

[Home](https://www.easefilter.com/) | [Solution](https://www.easefilter.com/solutions.htm) | [Download](https://www.easefilter.com/download.htm) | [Demos](https://www.easefilter.com/online-fileio-test.aspx) | [Blog](https://blog.easefilter.com/) | [Programming](https://www.easefilter.com/kb/programming.htm)


