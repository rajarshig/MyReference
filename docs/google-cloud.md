## Authentication
### Using service account
1. In Google cloud IAM & Admin > Create Service Account with Bigquery permission. Download the service account json in local system
2. Activate the service account using command
```
gcloud auth activate-service-account --key-file=internal-248613-4a7e38b1a204.json
```
which will show
```
"Activated service account credentials for: [internal-bigquery@internal-248613.iam.gserviceaccount.com]"
```
3. Test query
```
from google. cloud import bigquery
import pandas as pandas
query = "SELECT * FROM table"
out_raw = pd.read_gbq(query,project_id='internal-248613', dialect='standard')
```

### Using end user credentials from Google Cloud SDK
- Unset GOOGLE_APPLICATION_CREDENTIALS enviroment variable as it will conflict
```
unset GOOGLE_APPLICATION_CREDENTIALS
```
- Check default auth using
```
gcloud auth application-default login
```
You will be provided an url which can be used with the gmail account to authenticate. Afterwards that gmail account will be set as default auth of google cloud.
