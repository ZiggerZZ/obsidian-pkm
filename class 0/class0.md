## Task

Daily data update about weather for our analytics team.

## Prerequisites

- [[class 0/gcloud]]

## Solution

[Free weather API](http://www.7timer.info/doc.php?lang=en#api) + Python + App Engine + cron jobs + BigQuery

1. Set up service account: IAM & Admin -> Service Accounts -> Manage keys -> Add key
2. Bigquery: create dataset "Weather" 
   1. We can create the table either manually or via Python.
3. Manually check that the API works.
4. Set up a cron job: 

We will go through setting things up together and will learn how to get help from mistakes.

### Service account

- You must grant Storage Object Viewer permission to xxx@cloudbuild.gserviceaccount.com (IAM & Admin -> IAM -> edit principal).

### Python

We will use [FastAPI](https://fastapi.tiangolo.com/) to build a simple API with one endpoint.

### App Engine

App Engine allows us to easily deploy web services.

#### Config app.yaml

[Reference](https://cloud.google.com/appengine/docs/standard/python3/config/appref)

Example:
```yaml
runtime: python39
service: weather

handlers:
  - url: /.*
    script: auto
```

Important fields: `instance_class`, `runtime`.

#### Deploy

The very first App Engine service must be called `default`. `app.yaml`:
```yaml
runtime: python39
service: default

handlers:
  - url: /.*
    script: auto
```

Once `gcloud` is set up, just `gcloud app deploy`.  
Once the default service is uploaded, change the name back to our service - `weather`.
