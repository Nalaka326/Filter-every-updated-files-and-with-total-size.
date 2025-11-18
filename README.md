# Filter every updated files and with total size.

This Markdown file contains a simple **daily report script** to list all files updated in `/var/www/html` for a specific date and calculate their total size.

```bash
echo "---- FILE LIST WITH SIZES ----"
find /var/www/html -type f -newermt "2025-11-18" ! -newermt "2025-11-19" -exec ls -lh {} \;


echo "---- TOTAL SIZE ----"
find /var/www/html -type f -newermt "2025-11-18" ! -newermt "2025-11-19" -print0 \
| du -ch --files0-from=- | grep total
```

## Notes
- Replace `2025-11-18` and `2025-11-19` with any date to generate the report for a different day.
- The first part lists all files modified on the specified day with human-readable sizes.
- The second part calculates the total size of all files updated that day.
- You can save the output to a file by redirecting it, e.g., `> daily_report_2025-11-18.txt`.
- This script can be scheduled with **cron** to generate daily reports automatically.
