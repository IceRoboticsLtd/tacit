Deploying NodeJS as AWS Elastic Beanstake Application

See also http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create_deploy_nodejs.html

This section provides step-by-step instructions for deploying your Node.js web application to Elastic Beanstalk using EB Command Line Interface (CLI) 3.x and Git. EB CLI is a command line interface tool that enables you to deploy applications more easily using Git.

1) Develop, Test, and Deploy

![Image](../master/images/develop_test_deploy_aws_elastic_beanstalk.png?raw=true)

Typically, after developing and testing our application locally, we will deploy our application to Elastic Beanstalk. At this point, our application will be live at the URL such as http://core-wpams3yrvj.elasticbeanstalk.com.

NOTE: Because our application will be live, we should consider setting up multiple environments, such as a testing environment and a production environment. We can point our domain name to the Amazon Route 53 (a highly available and scalable Domain Name System (DNS) web service) CNAME <ourappname>.elasticbeanstalk.com. We should contact our DNS provider to set this up. For information about how to map your root domain to your Elastic Load Balancer, see [Using Elastic Beanstalk with Amazon Route 53 to Map Your Domain to Your Load Balancer] (http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.Route53.html).  
After we remotely test and debug our Elastic Beanstalk application, we can then make any updates and redeploy to Elastic Beanstalk. After we are satisfied with all of our changes, we can upload our latest version to our production environment. The following sections provide more details explaining each stage of the software development life cycle.

========= Get Set Up =========

EB CLI is a command line interface that we can use with Git to deploy applications quickly and more easily. EB is available as part of the Elastic Beanstalk command line tools package. For instructions to install EB CLI, see [Installing the EB Command Line Interface (CLI)] (http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install.html).

After having created and initialized a Git repository locally, run the following command inside the repository and EB CLI will recognize that your application is set up with Git.

eb init

You will be asked the following:

Select a default region
1) us-east-1 : US East (N. Virginia)
2) us-west-1 : US West (N. California)
3) us-west-2 : US West (Oregon)
4) eu-west-1 : EU (Ireland)
5) eu-central-1 : EU (Frankfurt)
6) ap-southeast-1 : Asia Pacific (Singapore)
7) ap-southeast-2 : Asia Pacific (Sydney)
8) ap-northeast-1 : Asia Pacific (Tokyo)
9) sa-east-1 : South America (Sao Paulo)
(default is 3):

We pick 4 for eu-west-1

Enter Application Name
(default is "core"):

We type the application name (e.g. core)

Application core has been created.

Select a platform.
1) PHP
2) Node.js
3) IIS
4) Tomcat
5) Python
6) Ruby
7) Docker
8) Multi-container Docker
9) GlassFish
10) Go
(default is 1):

We type 2 for Node.js

Do you want to set up SSH for your instances?
(y/n):

We type y for yes

Select a keypair.
1) tacit-core-key-pair-eu
2) [ Create new KeyPair ]
(default is 2):

We type 2 for create new KeyPair

Type a keypair name.
(Default is aws-eb):

We type core-aws-eb

Generating public/private rsa key pair.
Enter passphrase (empty for no passphrase):

We type a passphrase (*************)

Enter same passphrase again:

We type same passphrase

Your identification has been saved in /Users/wvanheemstra/.ssh/core-aws-eb.
Your public key has been saved in /Users/wvanheemstra/.ssh/core-aws-eb.pub.
The key fingerprint is:
f7:75:12:bb:73:73:65:f1:74:de:ef:6f:7d:c1:f9:3d core-aws-eb
The key's randomart image is:
+--[ RSA 2048]----+
|                 |
|                 |
|              ..o|
|               ==|
|        S .   = O|
|         . . . Oo|
|            . o.O|
|               EO|
|               .*|
+-----------------+
Enter passphrase:

We type passphrase (like before)

WARNING: Uploaded SSH public key for "core-aws-eb" into EC2 for region eu-west-1.

========= Develop Locally =========

After installing EB CLI 3.x on our local computer, we use the Git command line as we normally would to manage our local repository and add and commit changes. We develop our Node.js application as we normally would with our favorite editor.

Next, we run our program, add it to our repository, and commit our changes.

========= Test Locally =========

At this point we would test our application locally before deploying to Elastic Beanstalk. Suppose we find a few issues, we fix them before committing our changes to Git.

========= Deploy to AWS Elastic Beanstalk =========

After testing our application, we are ready to deploy it to Elastic Beanstalk. Deploying requires the following steps:

- Configure Elastic Beanstalk.

- Deploy a sample application.

- Update the sample application with our application.

When we update the sample application with our application, Elastic Beanstalk replaces the existing sample application version with our new application version in the existing environment.

Create your running environment, by typing:

eb create

Enter Environment Name
(default is core-dev):

We type core-dev if we want to deploy to the development environment (core-prod if we want to deploy to the production environment)

Enter DNS CNAME prefix
(default is core-dev):

Creating application version archive "6b3f".
Uploading core/6b3f.zip to S3. This may take a while.
Upload Complete.
Environment details for: core-dev
  Application name: core
  Region: eu-west-1
  Deployed Version: 6b3f
  Environment ID: e-kpwdcfcipb
  Platform: 64bit Amazon Linux 2015.03 v1.4.1 running Node.js
  Tier: WebServer-Standard
  CNAME: core-dev.elasticbeanstalk.com
  Updated: 2015-06-10 13:19:52.570000+00:00
Printing Status:
INFO: createEnvironment is starting.
INFO: Using elasticbeanstalk-eu-west-1-506043967056 as Amazon S3 storage bucket for environment data.
INFO: Created security group named: sg-248bbb41
INFO: Created load balancer named: awseb-e-k-AWSEBLoa-66QZU7Y98NTE
INFO: Created security group named: awseb-e-kpwdcfcipb-stack-AWSEBSecurityGroup-AZBM01N4XD0B
INFO: Created Auto Scaling launch configuration named: awseb-e-kpwdcfcipb-stack-AWSEBAutoScalingLaunchConfiguration-1IJ5RCBVRTMHC
INFO: Waiting for EC2 instances to launch. This may take a few minutes.
INFO: Created Auto Scaling group policy named: arn:aws:autoscaling:eu-west-1:506043967056:scalingPolicy:ff446edb-2c7d-4ed1-ae0d-39d25f087816:autoScalingGroupName/awseb-e-kpwdcfcipb-stack-AWSEBAutoScalingGroup-MQ1OCU6PRYNM:policyName/awseb-e-kpwdcfcipb-stack-AWSEBAutoScalingScaleUpPolicy-FRS20F0IRBEC
INFO: Created Auto Scaling group policy named: arn:aws:autoscaling:eu-west-1:506043967056:scalingPolicy:5bb1d696-6fa2-414c-8852-ec6bf6807824:autoScalingGroupName/awseb-e-kpwdcfcipb-stack-AWSEBAutoScalingGroup-MQ1OCU6PRYNM:policyName/awseb-e-kpwdcfcipb-stack-AWSEBAutoScalingScaleDownPolicy-ROI66K2YMR68
INFO: Created CloudWatch alarm named: awseb-e-kpwdcfcipb-stack-AWSEBCloudwatchAlarmHigh-FQFFOMYWNPZQ
INFO: Created CloudWatch alarm named: awseb-e-kpwdcfcipb-stack-AWSEBCloudwatchAlarmLow-1IV0X5MJYGTFA

View the application by typing the following:

eb open

To update the sample application with our local application

1. Make changes to our code, and then type the following command:

eb deploy

Elastic Beanstalk will attempt to start app.js, then server.js, and then "npm start" in that order. NOTE: If server.js is in a subfolder (e.g. servers), the path needs to be set in the package.json as the value of the key 'main', for Elastic Beansteak to be able to find it and start it.

2. If everything worked as expected, we should see something similar to the following:



NOTE: To configure an Elastic Beanstalk environment using the AWS Management Console:

Open the Elastic Beanstalk console at https://console.aws.amazon.com/elasticbeanstalk/.

- From the region list, select the region that includes the environment that we want to work with. (e.g. Ireland).

- On the Elastic Beanstalk console applications page, click the name of the environment with the settings that we want to edit.



... more
