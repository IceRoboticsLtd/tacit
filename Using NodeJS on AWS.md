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

3) Run the Sample

node sample.js
