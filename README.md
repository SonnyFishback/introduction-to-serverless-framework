# Introduction to the Serverless Framework:

Today we will be diving into one of my favorite tools to build full stack applications with, the serverless framework. Before we dive into the great things about serverless framework let's first break down what what the word serverless means.

What is serverless?

Serverless is a computation strategy and billing model that allows you to pay only for the computation power your application needs. Instead of paying for a typical server that
runs continuously in the cloud you can use serverless compute that is will only when you need it.

If a standard server in the cloud is a light bulb, serverless compute would be a light that has a motion sensor so it only turns on when you need it and turns off when you do not.

Sounds cool right? This is an awesome strategy that you can leverage across cloud providers making it a great tool for start ups and projects that may scale
up in resource needs in a very short time.

As with all technical decisions, the choice to use the serverless strategy depends on your unique situation. Serverless is great for some uses cases and is not a great fit for others.

One of the main trade offs you must consider is the concept of cold starts. Serverless compute starts "coldly" this means that when an "event" triggers a serverless compute instance to run, it must first prepare the resources required to run your code which does take time. Once your instance starts - it will timeout in 8 - 15 minutes in the cloud

Timeouts can be mitigated by parallelizing workloads and using ephemeral storage (a usb drive so you do not lose important memory).

Across cloud service providers, serverless compute instances are named differently. For AWS it is Lambda, GCP has Cloud Functions and Azure has Azure Function Apps.

There is a shared concept between them which is Functions. I will try to communicate concepts as general as possible that you can apply them to Azure and Google however note that I am using AWS cloud service.

When developing serverless applications composed of isolated functions, your code to a function will look like this:

```javascript
/**
 * This handler function is the entry point of your application.
 * 
 * The cloud service provider will take this file and run it on a server.
 * 
 * Every time the cloud service receives an "event" that is supposed to "invoke"
 * your function it will forward the event to the entry point of the file and all the code will
 * be executed and return the data returned in the function.
 * 
 */
import { database} '../database.js';
export function handler(event) => {
    if (!database) return {};
    // get the index that was requested from the frontend.
    const userIndex = event.userIndex

    // use that index to get the user by index from the database.
    const user = database.users[userIndex];

    // if no user return no user to frontend.
    if (!user) return 'user not found';

    // return that user
    return user;
};
```

The serverless framework is a open source project that started in 2015 and since then has became one of the top frameworks for
building serverless applications today.

It enables you to rapidly develop serverless applications and allow serverless framework code to do the heavy lifting as you go.

There is so much to cover and I strongly suggest you dive into the documentation to gain a better understanding.

If you want to use GCP or Azure, [this is what you seek.](https://sonnyfishback.com)

# Starting your project:

```
You will need a few things to follow along:
- Node.js
- Javascript
- AWS CLI Credentials
- Serverless Framework
```

To start a serverless project you need a [YAML](sonnyfishback.com) file named `serverless.yml`

This is the configuration file for your serverless project. You will specify your function definitions that will map your function names in the file to the javascript file so when you deploy serverless deploys it knows where all the files/functions to deploy are.

Also you can specify resource definitions in this file that will create the resources you list in the serverless.yml file and deploy them in your cloud.
```

# Create our first function using native function URL:

# Create an .ignore file to hide .serverless folder form version control.

# Invoke our function - investigate the event.

# Create form and submit form data to endpoint using HTML
# action attribute and redirect request to "sonnyfishback.com" for now.

# Let's deploy a resource to host our website and redirect back to the website.

Yes, you can redirect users. Here is [more information on response types](sonnyfishback.com).

# How about a more complex API example? Limitations of native lambda url?
# Add event configuration for httpApi for POST event.
# Let's manipulate this data on the server and register the user.

# Now let's use the fetch module to make the request instead of the form action.


# Any questions?
