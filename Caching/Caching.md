# Caching

A cache is a high-speed data storage layer, which stores a subset of data so that future requests for the data becomes faster than accesssing the data from primary storage location.

Caching is a process of storing a copies of files in cache, so that they can be accessed with less delay. Caching is one of the easiest way to increase system performance.

A cache's primary purpose is to increase data retrieval performance by reducing the time to acsess the data from slower storage layer. It also helps in save costs, scale heavy loads, and reduce latency.

# Why do we need caching

- When the costs of getting some information is very high or we need that information from time to time then we get the information once and the store it in a cached version.
- When we need to retrieve data at higher speed then we can store the data in cache and then when request is made that data can be returned to user instead of going to slower back-end storage.

# Cache Invalidation

Caching Invalidation is a process in which data in the cache marked as invalid so that in future request made for that particular data should have cache-miss. In simple words, when we modify a data in a database then the same data present in the cache should be marked as invalid and when the application checks the data in cache it should be invalid data so the application can access data from database. 

# Caching Approaches

## 1. Cache-Aside

In the approach, the application directly talks to both cache and database. There will be no direct connection between cache and database. The process involved in accessing the data by this approach is as follows.

- First, the application checks the cache.
- If the data is available in cache then we have a cache-hit. The application reads the data and returns to the client.
- If the data is not available in the cache. Then we will have a cache-miss. Now the data is read from the database and then the data returns to the client. Here application has to update the data in the cache so that it can retrieve the data when future requests made.
  
## 2. Read-Through Cache

Read-Through cache is linked to database. There will be no connection between database and application. Both Cache-Aside and Read-Through Cache loads the data slowly(Lazy loading) when it is loaded for the first time.

- Here the application request the data to cache.
- If the data is not found in cache then cache will load the data from database, updates the data in cache and then it will return to the application.
  
## 3. Write-Through Cache

In this write-through cache, the written data first served to the cache then to the database. Here the cache will be in line with database and all the data that is to be written in will have to pass through cache. The steps involved in writing or updating data are given below.

- The application writes the data directly to the cache.
- Then cache updates the data in the main database. When the updates are complete, both the cache and database will have the same data. This helps cache in maintaining the data consistency with the database. It minimizes the risk of data loss.
- However, every update operation should be updated in cache as well as in database which will result in a delay in updating the data.

## 4. Write-Around

Here the application writes the data directly to the database. Then the data which is to be read is will be updated in the cache.

- This reduces the update operations in the cache.
- However, when we make a requests for the data it will face a cache-miss if the data is not available in cache. Then in this case the application has to read the data from slower back-end storage.

## 5. Write-Back or Write-Behind

In this approach, the application writes the data to the cache and the data gets updated in main database in specified intervals. This helps in reducing the delay in data transfer. In this case there is a high risk of data loss if there is a crash since the copy of data was in cache.

# Cache Eviction

Cache provides high speed data access but it is limited, which is why it is important to carefully maintain and manage the information stored in it. Cache eviction is a process in which old, unused, excess data being dropped from cache to create space for new and frequently used data. The policies followed by cache eviction are given below.

- Least Recently Used (LRU) : It removes the items which are used very recently. It is one of the most popular caching strategies used.
- Least Frequently Used (LFU) : It removes the items which are used less number of times.

# References

- An article from Amazom web services on Caching - [AWS](https://aws.amazon.com/caching/#:~:text=In%20computing%2C%20a%20cache%20is,the%20data's%20primary%20storage%20location.)
- An article by Umer Mansoor on Brief overview of caching and cache invalidation - [https://codeahoy.com/2022/04/03/cache-invalidation/](https://codeahoy.com/2022/04/03/cache-invalidation/)
- An article by Umer Mansoor on Caching strategies and how to choose the right one - [https://codeahoy.com/2017/08/11/caching-strategies-and-how-to-choose-the-right-one/](https://codeahoy.com/2017/08/11/caching-strategies-and-how-to-choose-the-right-one/)
- An article on how to write markdown file by Saumya Ranjan Sahu - [https://medium.com/@saumya.ranjan/how-to-write-a-readme-md-file-markdown-file-20cb7cbcd6f](https://medium.com/@saumya.ranjan/how-to-write-a-readme-md-file-markdown-file-20cb7cbcd6f)