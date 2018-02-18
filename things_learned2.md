
## EHCACHE

Its an open source library for implementing caching that is completely developed in java.


+ Cache usually stores the hottest data i.e the data that is most frequently needed and we need to retrive it faster.


+ Its basic structure is using LinkedHashMap.


+ It stores the data in <key,value> pair of datatype Element
+ It have various tier storage structures which are as follows -


On-Heap :- On-Heap has limited storage as it is stored on JVM's heap memory


Off-Heap :- Off-Heap is stored in RAM and the size of Off-Heap is limited by the availability of RAM it needs to be Serialized


Disk :- The object in Disk Storage needs to be Serialized else they stored as Null.

 ADVANTAGES OF EHCACHE OVER COLLECTION OBJECT :- 
 
 
 > In Ehcache we can limit the maximum element a cache can have as well as how much memory a cache can consume.
  
 > If it reaches the limit then Ehcache has the algorithms such as LRU,LFU etc to clean itself. (Which is not possible in Map or HashMap interfaces, We have to add those functionality explicitly)
 
 
 > Ehcache provides the functionality of when the memory cache exceeds a certain limit then overflowing to the disk is possible.
  
 > In Ehcache suppose the system crashes or goes into unplanned shutdowm then the data will stay persistant.
 
 > Persistence :- Persistence means the cache will survive a JVM restart. Everything that was in the cache will still be there after restarting the JVM and creating a CacheManager disk persistence at the same location.
 
 
 To get more info about how to implement persistence click here.[persistence](http://www.ehcache.org/generated/2.10.4/html/ehc-all/#page/Ehcache_Documentation_Set%2Fto-persist_configuring_persistance_and_restart.html%23)
 
 
 EHCACHE configuration :- 
 you can refer to EHCACHE official documentation for configuration of latest version of [EHCACHE Configuration](http://www.ehcache.org/documentation/2.8/configuration/configuration.html#ehcache-failsafe.xml) for version 3.10.
 
 
 
 Configuration of 2.10.4 -
 
 + Download the jar file of ehcache2.10.4
 + extract that jar into your workspace.
 
 + after extraction open your IDE. include 3 jar files into your project which are present in 
 ```ehcache2.10.4/lib/``` folder.
 
 
 > ehcache-2.10.4.jar
 
 
 > slf4j-api-1.7.7.jar
 
 
 > slf4j-jdk14-1.7.7.jar
 
  
 + after extracting create ehcache.xml file and place in your workspace.
 
 + to know more about ehcache file elements open ehcache.xml file which is present in that extracted folder.

This was my ehcache.xml file.

```

<?xml version="1.0" encoding="UTF-8"?>

<ehcache xsi:noNamespaceSchemaLocation="ehcache.xsd" updateCheck="true" monitoring="autodetect" dynamicConfig="true">
<diskStore path="java.io.tmpdir"/>

	 <defaultCache
            maxElementsInMemory="10000"
            eternal="false"
            timeToIdleSeconds="120"
            timeToLiveSeconds="120"
            maxElementsOnDisk="10000000"
            diskExpiryThreadIntervalSeconds="120"
            memoryStoreEvictionPolicy="LRU">
        <persistence strategy="localTempSwap"/>
    </defaultCache>

	<cache name="mycache1"
		maxEntriesLocalHeap="10000"
		maxEntriesLocalDisk="100000"
		overflowToDisk="false"
		eternal="true"
		diskSpoolBufferSizeMB="20">
	</cache>

</ehcache>

```
