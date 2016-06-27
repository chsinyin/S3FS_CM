S3FS_CM
==
We modified S3FS by adding another cache.
User can apply compression to the files in cache.

Setting
==
Download and install s3fs-fuse first at https://github.com/s3fs-fuse/s3fs-fuse  
Download both patch files(fdcache_cpp.patch and fdcache_h.patch)  
Move files to s3fs directory :  
```
mv fdcache_cpp.patch ~/s3fs-fuse/src/  
mv fdcache_h.patch ~/s3fs-fuse/src/
```
Patch files :  
```
patch -po < fdcache_cpp.patch  
patch -po < fdcache_h.patch
```
You can modify the ptah of cache, maximum cache size, and change the compress-decision in fdcache.cpp
And make file :  
```
sudo make  
cd ..  
sudo make install  
```
