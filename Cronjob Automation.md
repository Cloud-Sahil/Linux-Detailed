# Cronjob (automata) automation
 - apt update
 - apt install cron
 - service cron start ---- to start cron service
 - service cron status ---- to check status of cron 
 - crontab -l ----- check crontab
 - cat /etc/crontab ---- read crontab 

| *     | Range   | Description     | Values             | Example                |
|------------|---------|-----------------|--------------------|------------------------|
| Minutes    | 0–59    | Minute field    | 0–59               | 30 → at 30th minute    |
| Hours      | 0–23    | Hour field      | 0–23               | 14 → 2 PM              |
| Day (Date) | 1–31    | Day of month    | 1–31               | 15 → 15th day          |
| Month      | 1–12    | Month           | 1–12 / Jan–Dec     | 4 or Apr               |
| Day (Week) | 0–6 (7) | Day of week     | 0–6 / Sun–Sat      | 0 or Sun → Sunday      |
