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

========= Develop Locally =========
