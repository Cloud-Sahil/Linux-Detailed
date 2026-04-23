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
| Day (Date) | 1–31    | Day of month    | 1–31               | 15 → 15th day          |
| Month      | 1–12    | Month           | 1–12 / Jan–Dec     | 4 or Apr               |
| Day (Week) | 0–6 (7) | Day of week     | 0–6 / Sun–Sat      | 0 or Sun → Sunday      |
