# Cronjob (automata) automation
 - apt update
 - apt install cron
 - service cron start ---- to start cron service
 - service cron status ---- to check status of cron 
 - crontab -l ----- check crontab
 - cat /etc/crontab ---- read crontab 

| *     | *   | *    | *             | *               |
|------------|---------|-----------------|--------------------|------------------------|
| Minutes    | Hours    | Day (Date)    | Month               | Day (Week)   |
| (0-59)      | 0–23    | (1-31)     | (1-12) or jan,feb...               | (0-6)(Sunday=0 or 7) or sun,mon,tue..|

Ex. 
1. 35 19 30 *  * /bin/tar -czf /root/opt.tar.gz /opt
2. 00 00 * * sat /bin/touch xyz
