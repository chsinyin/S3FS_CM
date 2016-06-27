S3FS_CM
==
We modified S3FS by adding another cache.
User can decide to compress or not to compress the files in this cache.
We use zlib to compress file by now, which can be replaced by user.

Setting
==
First, you should download and install libfuse at https://github.com/libfuse/libfuse  
Next, download and install s3fs-fuse at https://github.com/s3fs-fuse/s3fs-fuse  
Then download both patch files(fdcache_cpp.patch and fdcache_h.patch)  
Move files under s3fs directory :  
```
mv fdcache_cpp.patch ~/s3fs-fuse/src/  
mv fdcache_h.patch ~/s3fs-fuse/src/
```
Patch files :  
```
patch -po < fdcache_cpp.patch  
patch -po < fdcache_h.patch
```
You can modify the path of cache, maximum cache size, log files' path and change the compress-decision in `fdcache.cpp ` 
And make file :  
```
sudo make  
cd ..  
sudo make  
sudo make install  
```
Run :  
```
s3fs [Bucket] [mount point] options ...
Ex. s3fs testBucket tmp/s3  
```
In this version, the mount point(tmp/s3) is used to identify s3fs_CM.
If the mount point is not tmp/s3, it behaves as original s3fs.
This(mount point for s3fs_CM) can also be modified in fdcache.cpp  
Other usage is as s3fs.
