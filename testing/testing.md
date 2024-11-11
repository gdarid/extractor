# Testing

## Sample Curl Commands

### POSTing images, Local Dev

```bash
curl -X POST localhost:$FUNCTIONS_PORT \
   -H "Content-Type: multipart/form-data" \
   -F "uploaded=@./testing/images/beforeandafter.jpg" \
   -F "to_lang=en"

```

### POSTing images to our GCP Cloud Function

```bash
export PROJECT_ID=$(gcloud config list --format='value(core.project)')
gcloud auth application-default login

curl -X POST $BACKEND_GCF \
    -H "Authorization: Bearer $(gcloud auth print-identity-token)" \
    -H "Content-Type: multipart/form-data" \
    -F "uploaded=@$HOME/localdev/gcp/image-text-translator/testing/images/beforeandafter.jpg" \
    -F "to_lang=en"


```