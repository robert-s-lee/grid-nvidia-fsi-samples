```bash
aws s3api put-object-acl --bucket gridai-tabformer --key data.tar.gz --acl public-read
```

add [--no-sign-request](https://stackoverflow.com/questions/36144757/aws-cli-s3-a-client-error-403-occurred-when-calling-the-headobject-operation)



# download the dir of interest

```bash
mkdir tabformer
cd tabformer
git init
git remote add origin -f https://github.com/NVIDIA/fsi-samples/
git checkout fraud_detection
cat <<EOF >>.git/info/sparse-checkout
fraud_detection/TabFormer
EOF
git pull origin main

```

(this is essentially the opposite of the gitignore file).

Then we can 

git pull origin master


# s3 bucket of data
export AWS_PROFILE=byoc-admin
aws s3api create-bucket --bucket gridai-tabformer --region us-east-1
aws s3 cp transactions.tgz s3://gridai-tabformer/data.tar.gz

 - | tar -xz --to-command='aws s3 cp - s3://bucket/$TAR_REALNAME'

aws s3 cp ./ s3://gridai-tabformer/ --recursive


aws s3 ls s3://gridai-tabformer/ 
aws s3 cp ./ s3://gridai-tabformer/ --recursive

aws s3api delete-bucket --bucket gridai-tabformer --region us-east-1



gh repo clone https://github.com/NVIDIA/fsi-samples/tree/fraud_detection/fraud_detection/TabFormer

gh repo clone https://github.com/NVIDIA/fsi-samples/tree/fraud_detection/ fraud_detection/TabFormer