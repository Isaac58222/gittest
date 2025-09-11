# name: Rollout MIG with Zero Downtime

# on:
#   push:
#     branches:
#       - main

# jobs:
#   rollout:
#     runs-on: ubuntu-latest

#     permissions:
#       contents: read
#       id-token: write   # required for Workload Identity Federation

#     steps:
#       - name: Checkout repository
#         uses: actions/checkout@v4

#       - name: Authenticate to GCP with Workload Identity Federation
#         uses: google-github-actions/auth@v2
#         with:
#           token_format: access_token
#           workload_identity_provider: projects/515228593779/locations/global/workloadIdentityPools/wp-test/providers/wp-test
#           service_account: wp-test@micro-answer-469207-r4.iam.gserviceaccount.com

#       - name: Setup gcloud
#         uses: google-github-actions/setup-gcloud@v2
#         with:
#           project_id: micro-answer-469207-r4
#           export_default_credentials: true

#       - name: Rollout MIG (zero downtime)
#         run: |
#           gcloud compute instance-groups managed rolling-action replace wp-mig \
#             --zone=us-central1-c \
#             --max-surge=1 \
#             --max-unavailable=0 \
#             --replacement-method=substitute         
