# Class 0

## Task

Daily data update about weather for our analytics team.

## Solution

[Free weather API](http://www.7timer.info/doc.php?lang=en#api) + Python + App Engine + cron jobs + BigQuery

1. Set up service account: IAM & Admin -> Service Accounts -> Manage keys -> Add key
2. Bigquery: create dataset "Weather" 
   1. We can create the table either manually or via Python.
3. Manually check that the API works.
4. Set up a cron job.