# Introduction to the Serverless Framework:

Today we will be diving into one of my favorite tools to build full stack applications with, the serverless framework. Before we dive into the great things about serverless framework let's first break down what what the word serverless means in software development.

So what is serverless?

Serverless is a computation strategy and billing model that allows you to pay only for the computation power your application uses. Instead of paying for a typical server that
runs continuously in the cloud you can use serverless compute that will run only when you need it and turn off when you don't.

If a standard server in the cloud is a light bulb, serverless compute would be a light that has a motion sensor so it only turns on when you need it and turns off when you don't.

Another awesome benefit of serverless compute is auto scaling. Traditional servers have bandwidth limitations. This means the more users you have, them more servers you must provision. With serverless compute, your compute instances scale up and down with your resource needs automatically.

Sounds cool right? This is an awesome strategy that you can leverage across cloud providers making it a great tool for start ups and projects that may scale up in resource needs in a very short time.

As with all technical decisions, the choice to use the serverless strategy depends on your unique situation. Serverless is great for some uses cases and is not a great fit for others.

One of the main trade offs you must consider is the concept of cold starts. Serverless compute starts "coldly" this means that when an "event" triggers a serverless compute instance to run, it must first prepare the resources required to run your code which does take time.

Another trade off is "timeouts", Once your instance starts - it will timeout in 8 - 15 minutes in the cloud making this a bad fit for workloads that need to run for long periods of time.  

Timeouts can be mitigated by parallelizing workloads and using ephemeral storage (a usb drive so you do not lose important memory).

Across cloud service providers, serverless compute instances are named differently. For AWS it is Lambda, GCP has Cloud Functions and Azure has Azure Function Apps.

There is a shared concept between them which is Functions. I will try to communicate concepts as general as possible so you can apply them to Azure and Google however, note that I am using AWS cloud service.

If you want to use GCP or Azure, [this is what you seek.](https://sonnyfishback.com)


When developing serverless applications you can imagine your entire code base as individual isolated functions, each being stored in an independently deployable file.

Instead of a tightly coupled API that is deployed as a single artifact, you can change and deploy your serverless API one function at a time.

![serverless meme](https://blog.ymirapp.com/uploads/2022/06/serverless-scooby-doo-meme.jpg?height=666&width=500)


# What is the Serverless Framework

The serverless framework is a open source project that started in 2015 and since then has became one of the top frameworks for
building serverless applications today.

It enables you to rapidly develop serverless applications while serverless framework does the heavy lifting as you go.

The main concepts of Serverless Framework are:

- Functions (Your micro servers)
- Events (The reasons the micro servers start and the data that is forwarded to the micro-server)
- Resources (Infrastructure as Code resource configurations allowing you to create and deploy instances of cloud resources named in a config file)
- Services (A unit of organization - you can have multiple services for one application)

# Starting your project:

```
You will need a few things to follow along:
- Node.js
- Javascript
- AWS CLI Credentials
- Serverless Framework
```
To start a serverless project you need a [YAML](sonnyfishback.com) file named `serverless.yml`. (This can be JS, TS and JSON instead of YAML).

This is the configuration file for your serverless project. You will specify your function definitions that will map your function names in the serverless.yml file to the javascript file where the function code is located so when you deploy serverless knows where all the files/functions to deploy are located.

Also you can specify resource definitions in the serverless.yml that will create the resources you list and deploy them in your cloud.

Some resources you may deploy are databases, alarm configurations .etc.

```
1. Let's create our first lambda function using lambdas native function URL. (console.log the event!)

2. Let's create an HTML form and invoke the function using the native action attribute.

3. Let's check cloudwatch to see what the logs look like for our first invocation.

4. There are limitations around the native function URL. You have one URL per function, you cannot connect the function URL to a custom domain, limited features you may want for your API (rate limiting, authorization, advanced metrics).

5. Let's refactor our function to use httpApi (API Gateway V2).

6. Let's deploy a S3 bucket resource so we can host our static site form.

6. Let's refactor our form to use the fetch module in order to allow future logic for loading state, more complex client side validation and handle server side validation errors returned from the backend.

7. Let's manipulate this data on the server, do some server side validation and return some status codes. (302 redirect to our S3 bucket)

8. Let's open the floor up for any questions from students and staff.
