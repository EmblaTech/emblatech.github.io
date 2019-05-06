---
layout: post
title: "Complete automation with Serverless/CloudFormation."
quote: "... comes a point when you realize you need to scale your servers as the traffic gets higher and higher, initially you just scale vertically hoping it would be enough and when you reach the vertical scaling limits you are forced into horizontal scaling."
image:
      url: /media/medium/denise-jans-1203943-unsplash.jpg
video: false
comments: true
author_name: Dasith Kuruppu
author_url: https://github.com/EmblaTech
author_pic: istockphoto-836272842-612x612.jpg
---

<style type="text/css"> #post-info { background-color: rgba(0,0,0,.5); padding: 10px; } </style>

During the early days** **of web development, a website was **deployed **by purchasing a server or access to a server by using a hosting provider and in some cases the hosting servers were in-house. Afterwards you would manually have to configure and install a bunch of utilities / software to allow the server to run & host your website or application.If you needed 3 similar server environments(eg: development, testing and production) you would have to repeat the process. Then comes a point when you realize you need to scale your servers as the traffic gets higher and higher, initially you just scale vertically hoping it would be enough and when you reach the vertical scaling limits you are **forced **into horizontal scaling. This is an entirely different beast altogether which usually ends up with major application reworks, hiring infrastructure Engineers & a lot more complex configurations which ultimately ends up with you making an over provision of resources/servers just to be on the safe side(This is a good thing).Finally when you have enough capacity and resources provisioned to accommodate more than enough traffic you realize during certain times of the year there is barely any traffic…and your provisioned resources stay Idle while you pay the bills. Ever considered this to be a problem ? or have you ever considered if there was an easier / better way to tackle this problem ?

Well if you have, **fortunately **the industry has now evolved into such a state where scalability , complexity , maintainability and cost of scaling has been considered as primary factors when designing a web applications more often in the initial stages itself rather than later. You can easily achieve this with the many services offered by the popular cloud providers(AWS, Azure, Google Cloud, Alibaba Cloud). They have turned most of their in-house software & opensource software to services with added value which scale **indefinitely **with usage. You may now have a question “What does this actually mean ?”.

Well it means most of the complexity of configuration and scaling has been abstracted over by cloud providers in a much elegant and cost efficient way such that resource provisioning , scaling and automation has become much easier and simpler to set up. Most cloud providers now provide ways to automate everything using IaaS(Infrastructure as a Service eg: Cloud formation) and IaC(Infrastructure as Code).With IaaS/IaC spawning servers , databases , VPC’s , gateways etc could be done within a few seconds.

So the blueprint for any architecture you can think of for your application could be written on to a template file like the one below which is using a [*Serverless](https://serverless.com/) *template(*Serverless -[*https://serverless.com/](https://serverless.com/)* *mentioned here* *is a framework that allows us to provide common template files to provision resources, the *Serverless *framework normalizes this template between the popular cloud providers allowing us to provision infrastructure / resources on any of them using a common template file). So for example the following yml template below

<iframe src="https://medium.com/media/b2a69513f1c53df30b930a4d33ee9a33" frameborder=0></iframe>

describes the following architecture.

![Architecture for the resources/services provisioned by the template file.](https://cdn-images-1.medium.com/max/3840/1*11hbHeTGTdlBkwn0HISM9w.png)*Architecture for the resources/services provisioned by the template file.*

This means that any infrastructure, service or resource that could possibly be used in the project / application is just held in one single file with the ability to replicate the architecture within seconds on any cloud provider(With the exception of vendor specific services). Meaning you would never have to worry about hardware issues , OS issues(with the use of lambda functions) , network issues or configuration and service availability issues. As all these become a responsibility of the cloud provider and you could set your sole focus on the application.With using serverless templates your entire application including the infrastructure becomes portable across any cloud vendor.This also allows you to replicate the same environment any number of times allowing you to reproduce identical test & production environments quite easily.

You many now have a question as to how this would this help us achieve ‘*complete automation*’.Well normally any application uses some sort of automation, It could be the build process , the testing or deployment process or all the mentioned processes. What most of them lack is the automation of the creation of resources / infrastructure itself but with *Serverless *templates this becomes quite easy to achieve. Where you could have salable infrastructure created on demand with the ability to port them across any cloud provider which is quite a powerful feat to have on an application. You can bootstrap your applications off of the repository from [https://github.com/DasithKuruppu/serverlessGraphQL](https://github.com/DasithKuruppu/serverlessGraphQL) if you prefer a graphQL api or if you prefer your own RESTful api you could create one by installing *serverless *and using the following command if you prefer a nodejs run-time :

    serverless create --template aws-nodejs

several other templates are also available supporting many different run-times.So the next time you start a project you may want to consider this kind of approach to automation which would massively benefit you in both the long and short run.
[**Going Serverless with NodeJS & GraphQL (Part I) — Setting up Serverless**
*So recently I have been interested in and looked into serverless on AWS using lambda functions and using…*levelup.gitconnected.com](https://levelup.gitconnected.com/going-serverless-with-nodejs-graphql-5b34f5d280f4)
[**Going Serverless with NodeJS & GraphQL (Part II) — Implementing GraphQL on AWS**
*Before you read this, note that there is the initial article on cloud-formation templates here. You can read that to…*levelup.gitconnected.com](https://levelup.gitconnected.com/going-serverless-with-nodejs-graphql-part-ii-1810445028a4)
