# Archive and compressed files
## 1. Archive
1. tar -------------   create archive
2. (-c)  -------------   create a new archive
3. (-v)  -------------   verbose (visualization)
4. (-x)  -------------   it extract the file
5. (-f)  -------------   file 
6. (tar --help) 
7. (-C)  -------------   change location
8. (-t)  -------------   list

**Syntax** ------->
```sh
tar<flag> <destination & mention extention.tar> <source>
```
**Ex.** ----------->
1. tar -cvf <dest.>/.tar (extension) <source> -------- this is format

 `tar -cvf /root/opt. /opt`

 2. tar -xf <source> -C <dest.> --------- format

 `tar -xf opt.tar -C /etc` ------------- opt directory will extract in /etc

 3. tar -xf <source> -------------- format

 `tar -xf opt.tar` ------------- to extract where you tar file present

---
## 2. Compression
| Compression | Compression Size | Size  | Speed  | Extension | Decompression | Archive + Compression |
|-------------|------------------|-------|--------|-----------|---------------|------------------------|
| gzip        | Low              | 80 MB | High   | .gz       | gunzip        | -z                     |
| bzip2       | Medium           | 50 MB | Medium | .bzip2    | bunzip2       | -j                     |
| xz          | High             | 30 MB | Low    | .xz       | unxz          | -J                     |

1. tools ---- (gzip,bzip2,xz)
2. low ---- (low ,medium ,high)
3. mb
4. speed ---- (high ,medium, low)
5. extensions ----  (.gz, .bzip2, .xz)
6. extaction commands ---- (gunzip, bunzip2, unxz)

---
🔹Normal file / Archive file ----- compress (gz, bzip2, xz) --- extract	

 - ex ---
   - 1. opt.tar.gz
   - 2. opt.tar.bzip2
   - 3. opt.tar.xz

🔹 Archieve + Compression -------
		
		. gzip -z (small)
		. bzip2 -j (small)
		. xz -J (big)
	  
	ex ------ 1. tar -czf /root/(media).tar.gz /opt/      
		  2. tar -xzf opt.tar.gz -C/home/  ------   To extract & decompress file at different location

   
    To decompree file in another location move the file to that location decompree it
