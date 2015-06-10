Deploying NodeJS as AWS Elastic Beanstake Application

See also http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create_deploy_nodejs.html

This section provides step-by-step instructions for deploying your Node.js web application to Elastic Beanstalk using EB Command Line Interface (CLI) 3.x and Git. EB CLI is a command line interface tool that enables you to deploy applications more easily using Git.

1) Develop, Test, and Deploy

![Image](../master/images/develop_test_deploy_aws_elastic_beanstalk.png?raw=true)

Typically, after developing and testing our application locally, we will deploy our application to Elastic Beanstalk. At this point, our application will be live at the URL such as http://core-wpams3yrvj.elasticbeanstalk.com.

NOTE: Because our application will be live, we should consider setting up multiple environments, such as a testing environment and a production environment. We can point our domain name to the Amazon Route 53 (a highly available and scalable Domain Name System (DNS) web service) CNAME <ourappname>.elasticbeanstalk.com. We should contact our DNS provider to set this up. For information about how to map your root domain to your Elastic Load Balancer, see [Using Elastic Beanstalk with Amazon Route 53 to Map Your Domain to Your Load Balancer]([http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.Route53.html).  
