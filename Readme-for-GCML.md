### Steps to upload model to Google cloud ML:

1. Convert the generated model to the required format using convert.py.
2. Create a bucket on GCP to store the model.
3. Create a model on the google cloud ML page
4. Click create a version and browse to the location of the folder where the model is uploaded.
5. Will take a couple of mins to create the version.
6. Once created you can query the model using gcloud prediction api or predict-request.py
