# Description
[Azure Queue Storage](https://learn.microsoft.com/en-us/azure/storage/queues/storage-queues-introduction) is a service for  storing a large number of messages, up to millions of items. Queues are commonly used to create a backlog of work to process in an asynchronous manner. The workflow to process these message implements the [[Web-Queue-Worker -architecture style]].
# Queue
A queue contains a set of messages.
## Naming
The queue name must be lowercase, and it must follow the naming rules:
- A queue name must be unique within the storage account
- The name cannot be changed after creation
- A queue name must start with a letter or number, and can only contain letters, numbers, and the dash (-) character.    
- The first and last letters in the queue name must be alphanumeric. The dash (-) character cannot be the first or last character. Consecutive dash characters are not permitted in the queue name.    
- All letters in a queue name must be lowercase.
- A queue name must be from 3 through 63 characters long.
## Access
The URL of a storage account queue follows the format:
`https://<storage account>.queue.core.windows.net/<queue>`

# Message
A message stored within a queue can be in any format, with a maximum size of 64 KB. The default time-to-live of each message is 7 days. This value can be changed with configuration.
