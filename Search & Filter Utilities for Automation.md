# Search & Filter Utilities in Linux (for Automation)
**(cat ,grep, sort, uniq, find)**

1.  cat  --------   to merge the file

2.  grep  ---------   grep "<word>" filename 	  ( ex. grep "ubuntu"  os-release )
    . grep -i "<word>" filename
    . grep -c "<word>" filename  ---- no of count word total 
    . grep -ci "<word>" filename  ---- no of count words both capital and small word total 
    . ls /etc | grep m (for finding m words in file)
    . ls /etc | grep c (for finding m words in file)
    . ls /etc | grep cron (for finding m words in file)
 
 3.  sort  ---------  
    . sort os-release  ------  ascending order in alphabetical order, mentioned file or dir. name
    . sort -r os-release  -----  descending order in alphabetical order

4.  uniq <name>  ---------  double words represent only single time
    . uniq -c <filename>  -------  show words with no of count 
    . sort <filename> | uniq | wc-l  ------  total word count
    . uniq <filename / dir.> | wc-l  ------  total words count complete
    . sort <filename / dir.> | uniq  ------  total count
    . sort <filename / dir.>  ----- 

5.  find  ----------
    - find /  ---------  (/ finds in all 19 dir.)
    - find / -name <filename / dir.>  -------  
    - find /root -name <filename / dir.>  ------
    - find /root -cmin 2(min)  ------  
    - find -ctime  ------  for day
    - find -cmin  -------  for min 
    - find /root -name 777  -------  to search file by permission 
    - find -mtime  -------  modified 1 day
    - find -mmin  -------  
    - find / -user name | less 
    - find /home -user <filename>
    - find /home/<filename> -user <filename>
