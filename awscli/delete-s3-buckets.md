# Delete S3 Buckets

The following script can be used to force delete an array of buckets from S3-compatible object storage platforms.


```bash
#!/bin/bash

###
# The following script will delete all buckets with the names listed in the
# 'b' variable below.
#
# The command uses a pre-set profile. To set this profile, use this command
#
# 
# aws configure --profile=PROFILE_NAME_HERE`
#



## Amazon AWS
#
s3_endpoint="https://s3.amazonaws.com"
s3_profile="AWS"

## IBM Cloud
#
#s3_endpoint="https://s3.eu.cloud-object-storage.appdomain.cloud"
#s3_profile="IBM"


### EDIT BELOW


b="bucket-to-delete-01
bucket-to-delete-01
bucket-to-delete-01"


### EDIT ABOVE

buckets_to_delete=($b)
for (( i=0; i<=${#buckets_to_delete[@]}; i++ )); do
	aws --endpoint=$s3_endpoint --profile=$s3_profile s3 rb s3://${buckets_to_delete[$i]} --force
done

echo ""
echo "...deleting finished"
echo ""
echo ""
echo ""
echo "NEW BUCKET LIST"
echo "---------------"
echo ""

aws --endpoint=$s3_endpoint --profile=$s3_profile s3 ls
```