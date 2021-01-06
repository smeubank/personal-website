# Serverless Website and Delivery Project

http://www.steven-eubank.com/

## Purpose

What started out as a desire to have my own profile, turned into a project which would allow anyone to see a simple example of how easy it is to host content in the cloud. Then, further even allow any casual user to contribute to the site as a casual user and take part in a kind of simplified CI/CD pipeline.

So, simple enough the above website is [serverless](https://en.wikipedia.org/wiki/Serverless_computing), and all that really means is that it takes advantage of the next stage of the cloud, where the content creator (you, me, anyone) does not have to worry anymore above configuring any cloud compute instance (EC2) or storage (databases) and so on. Of course there are pros and cons, but it does allow for rapid prototyping at the very least with little no costs.

Navigate to the site, and in the "about" section towards the top there are links to how to create a fork and pull request on a GitHub repo, if you never have before. To protect the site, and make sure it stays safe for work and school purposes, I will not merge any inappropriate PRs.

Below you will find more details and links about how all this works, so you can figure out how to set this up on your very own! Otherwise feel free to contribute to the page as stated above, and get some hands cloud/serverless/CI/CD experience :D !!

*from time of merge to delivery of your code changes is about 1 minutes, if you don't see your changes on the site directly, double check with dev mode in your browser if the HTML has your changes, they just aren't visible for some reason*

## Serverless architecture:

### All the Bells and Whistles

All the major Cloud providers today (Amazon AWS, Microsoft Azure, Google Cloud Platform) provide some form of serverless, but AWS is arguable the most widely known. This site is done only with AWS, (excluding GitHub of course) but I am sure similar or same could be done with the other major providers as well. All of this will be useful when doing any AWS certifications as well.

*many of the links below are simply for help, I did not use or even read them all TLDR*

* [Static Website Content:](https://bootstrapmade.com/) I didn't really want to test my web development expertise so I used a free bootstrap, to make sure it looks clean and professional. At least that's what I say when I wear my "enterprise architect" hat :)
* [S3 - Simplified Storage Service:](https://docs.aws.amazon.com/AmazonS3/latest/user-guide/static-website-hosting.html) think windows style folders storage for files, docs, images, almost anything. If you use some cloud photo storage, something like this is typically behind it
* [CloudFront and Lambda@Edge:](https://aws.amazon.com/premiumsupport/knowledge-center/cloudfront-serve-static-website/) non-mandatory, it helps to make your content more easily accessible and around the globe. Overkill for this site, since it is very simple, but a good exercise none the less.
* AWS Certificate Manager: non-mandatory, if you read through the S3 documentation, basically you will learn your site will only be HTTP, and with this you can make it HTTPS, which protects your visitors' data. Again a bit overkill since the site is not asking for any info from visitors, but important for learning.
* [Route 53;](https://docs.aws.amazon.com/AmazonS3/latest/dev/website-hosting-custom-domain-walkthrough.html) non-mandatory, and pretty much the only thing here which would cost you any meaningful amount of money, but important when understanding how web traffic works.

![alt text](https://github.com/smeubank/personal-website/blob/master/assets/img/serverless-architecture.PNG?raw=true)

### Build pipeline:

Once you have everything served up for your visitors, you don't want to have to start from scratch everytime when maintaining your code and putting in S3. At least I am too lazy for that. So what should you do? Set up a build pipeline. This one is very simple. And I will describe as above with the architecture.

* GitHub - version control provider using Git, this is not the only Git provider, AWS also has some service
* [AWS CodePipeline:](https://docs.aws.amazon.com/codepipeline/latest/userguide/tutorials-s3deploy.html) This takes care that whenever the main branch of this repo is changed, a webook will trigger the build to collect the code, then deploy it to S3 and finally to solve the issue with CloudFront data cache and TTL (time to live), triggers a Lambda function which will "invalidate"
* [AWS Lambda:](https://medium.com/@yagonobre/automatically-invalidate-cloudfront-cache-for-site-hosted-on-s3-3c7818099868) - serverless code, massively simplifies running code on the internet to big or small tasks, in this case just making sure visitors always see the latest version of the web content, and setting the build job to "completed"
** [This lambda function](https://github.com/smeubank/invalidate-cache-lambda) is also set up so that it can be automatically deployed upon change

All of this generally takes about 45 seconds in my experience, so if look for your changes after the PR is merged that is about how long it will take.

![alt text](https://github.com/smeubank/personal-website/blob/master/assets/img/serverless-site-build-pipeline.PNG?raw=true)

Thanks for downloading this template!

Template Name: iPortfolio
Template URL: https://bootstrapmade.com/iportfolio-bootstrap-portfolio-websites-template/
Author: BootstrapMade.com
License: https://bootstrapmade.com/license/


*for non-commercial purposes*
