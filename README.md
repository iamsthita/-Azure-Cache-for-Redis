# Azure-Cache-for-Redis

# Redis Cache Commands
An Overview of Common Redis Cache Commands and Their Usages:

SELECT: Allows you to switch between different databases (“floors" in the context of SCALE) within a Redis instance.

SCAN: This is a cursor-based iterator, which means that with each command call, the server provides an updated cursor that must be used as the cursor argument in the subsequent call. The return value of SCAN is an array containing two elements. The first element represents the new cursor to be used in the next call, while the second element is an array of elements.

KEYS: Retrieve all keys or matching a specified pattern.
(Not Recommended in PROD)

DBSIZE: To get the total number of keys in the selected Redis database(“floors" in the context of SCALE).

DEL:Delete a specific existing key in Redis.

FLUSHDB: Delete all the Cache keys from the currently selected database (“floor" in the context of SCALE)

FLUSHALL: Remove all the Cache keys from all the existing databases, not just the currently selected one. Use sparingly.

INFO: Retrieves various information about the Redis server, including memory usage, clients, and more.

Navigate to Azure Cache for Redis, select the required Redis application, go to the Overview pane, and click on 'Console
