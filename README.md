# building and submit container specifying project id and service name 
gcloud builds submit --tag gcr.io/octave-272909/testv2 --project=octave-272909

# deploy container image, specifying wheter it's platform managed, allowing unauthetication, project id, service name and region 
gcloud run deploy testv2 --image gcr.io/octave-272909/testv2 --platform managed --project=octave-272909 --allow-unauthenticated --region us-central1

# checking service accounts
gcloud iam service-accounts list --project=octave-272909

# generating keys.json for the service account
gcloud iam service-accounts keys create ./keys.json --iam-account github-actions-test@octave-272909.iam.gserviceaccount.com

# checking authentication with key file 
gcloud auth activate-service-account --key-file=keys.json