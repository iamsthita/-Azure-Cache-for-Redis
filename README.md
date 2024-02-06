# Redis Cache Commands:

An Overview of Common Redis Cache Commands and Their Usages:
<br>

**SELECT:** Allows you to switch between different databases (“floors" in the context of SCALE) within a Redis instance.

**SCAN:** This is a cursor-based iterator, which means that with each command call, the server provides an updated cursor that must be used as the cursor argument in the subsequent call. The return value of SCAN is an array containing two elements. The first element represents the new cursor to be used in the next call, while the second element is an array of elements.

**KEYS:** Retrieve all keys or matching a specified pattern.
(Not Recommended in PROD)

**DBSIZE:** To get the total number of keys in the selected Redis database(“floors" in the context of SCALE).

**DEL:** Delete a specific existing key in Redis.

**FLUSHDB:** Delete all the Cache keys from the currently selected database (“floor" in the context of SCALE)

**FLUSHALL:** Remove all the Cache keys from all the existing databases, not just the currently selected one. Use sparingly.

**INFO:** Retrieves various information about the Redis server, including memory usage, clients, and more.


Navigate to Azure Cache for Redis, select the required Redis application, go to the Overview pane, and click on 'Console.

<img width="427" alt="image" src="https://github.com/iamsthita/Azure-Cache-for-Redis/assets/132139960/c9ae667a-e70b-4698-a8cf-42377f6a9539">
<br><br>
<img width="357" alt="image" src="https://github.com/iamsthita/Azure-Cache-for-Redis/assets/132139960/3ad340d6-1d6c-4d24-92da-4f119147752f">
<br><br>
Here we are taking an example of Multi tenancy setup. <br><br>
Once you go inside Console, you can type the below commands as per the requirements: <br>

1. Fetch all Cache values for a particular floor:
SELECT [DATABASE ID]
SCAN cursor [COUNT count]

2. Fetch specific Cache value with keyword:
SELECT [DATABASE ID]
SCAN cursor COUNT count *MATCH pattern*

3. Delete specific Cache key:
DEL {cache full key name with double quotes}

4. Delete all Cache values from a Single floor:
SELECT [DATABASE ID]
FLUSHDB

5. Delete all Cache values from all associated floors:
FLUSHALL
(Please be careful while executing this as this will clear cache from all associated floors.)
<br><br>

**Detailed Explanation Below:**
<br><br>

FETCH ALL CACHE VALUES FOR A PARTICULAR FLOOR: <br> <br>
SELECT 1 <br>
SCAN 0 COUNT 1000 <br> 
Here server returns an updated cursor 366 that the user needs to use as the cursor argument in the next call. If the required key is not found keep the command running with next cursor value until the value reaches 0. <br> <br>
SCAN 366 COUNT 1000 <br> <br>
The above will fetch the next set of keys and so on.

NOTE: The cursor value "366" in the SCAN response does not indicate the total number of cache key entries. The cursor value is specific to the
SCAN operation and represents the current position in the iteration of keys, but it does not reflect the total count of keys. <br><br>

<img width="410" alt="image" src="https://github.com/iamsthita/Azure-Cache-for-Redis/assets/132139960/816db1da-b027-4ef8-b424-6ea771e4e15f">




