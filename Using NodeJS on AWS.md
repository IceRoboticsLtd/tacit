Using NodeJS on AWS

See also http://aws.amazon.com/developers/getting-started/nodejs/

1) Install the SDK and dependencies

From the tacit projects directory (e.g. ~/git/vanHeemstraSystems/core/), run:

sudo npm install

NOTE: The package.json file will contain these special AWS dependencies

{
    "dependencies": {
        "aws-sdk": ">= 2.0.9",
        "node-uuid": ">= 1.4.1"
    }
}

2) Configure the Access Keys

Create your own credentials file at ~/.aws/credentials (C:\Users\USER_NAME\.aws\credentials for Windows users, ~/.aws/credentials for Mac OSX and Linux users) and save the following lines after replacing the underlined values with your own.

[default]
aws_access_key_id = YOUR_ACCESS_KEY_ID
aws_secret_access_key = YOUR_SECRET_ACCESS_KEY

When you access AWS programmatically, you use an access key to verify your identity and the identity of your applications. An access key consists of an access key ID (something like AKIAIOSFODNN7EXAMPLE) and a secret access key (something like wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY).

Collect the above information, by logging into your AWS account at https://eu-west-1.console.aws.amazon.com/console/home?region=eu-west-1#
directly
https://vanheemstrasystems.signin.aws.amazon.com/console

Note: you can no longer retrieve existing secret access keys for the root account. If you lose your secret access key, you must generate a new access key (an access key ID and a secret access key). Follow their best practices and create an AWS Identity and Access Management (IAM) user that has access keys, instead of relying on root access keys. Using IAM will allow you to set up fine-grained control over access to your AWS resources. See https://docs.aws.amazon.com/general/latest/gr/aws-access-keys-best-practices.html

See http://docs.aws.amazon.com/IAM/latest/UserGuide/GSGHowToCreateAdminsGroup.html
for Creating an Administrators Group Using the Console and hence creating an IAM user with access keys.

You should be able to see the access keys here (if logged in):
https://console.aws.amazon.com/iam/home?region=eu-west-1#users/WvanHeemstra

3) Run the Sample

node sample.js

If the credentials were set and are valid, the above script will reply like so:
Successfully uploaded data to node-sdk-sample-acb9ff5a-2851-4237-a532-6157f58e2912/hello_world.txt

The bucket and txt file can be found here (if logged in):
https://console.aws.amazon.com/s3/home?region=eu-west-1#

Here is how to work with buckets (i.e. where the hello_world.txt was stored).
http://docs.aws.amazon.com/AmazonS3/latest/UG/BucketOperations.html

Every object you store in Amazon S3 resides in a bucket. You can use buckets to group related objects in the same way that you use a directory to group files in a file system. Buckets have properties, such as access permissions and versioning status, and you can specify the region where you want them to reside.
