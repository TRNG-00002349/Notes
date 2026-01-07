# Unit: AWS

## Modules

* [AWS Serverless: Lambda](#lambda)
* [AWS Serverless: DynamoDB](#dynamodb)
* [AWS Serverless: SAM](#sam)
* [AWS Cognito](#cognito)
* [AWS DevOps: CloudFormation](#cloudformation)
* [AWS DevOps: CloudWatch](#cloudwatch)
* [AWS DevOps: CodeBuild](#codebuild)
* [AWS DevOps: CodePipeline](#codepipeline)
* [AWS DevOps: CodeDeploy](#codedeploy)
* [AWS DevOps: CodeCommit](#codecommit)
* [AWS Identity and Access Management(IAM)](#iam)
* [AWS Virtual Private Cloud(VPC)](#vpc)
* [AWS CloudFront](#cloudfront)
* [AWS Elastic Load Balancer(ELB)](#elb)
* [AWS Elastic Container Service(ECS)](#ecs)
* [AWS Route 53](#route-53)
* [AWS Simple Queue Service(SQS)](#sqs)
* [AWS Simple Notification Service(SNS)](#sns)
* [AWS Key Management Service (KMS)](#kms)
* [AWS API Gateway](#api-gateway)

## SAM

[Back to top](#unit:-aws)

* **What is AWS SAM?**
  * Keywords, concepts, or topics that should be in the response:
    * Stands for `Serverless Application Model`
    * Open-source framework for building serverless applications
    * You can define the application you want and model it using YAML
    * During deployment, SAM transforms and expands the SAM syntax into the CloudFormation syntax which helps us build serverless applications faster
  * Possible follow-up questions:
* **What are some benefits to using AWS SAM?**
  * Keywords, concepts, or topics that should be in the response:
  * Possible follow-up questions:
* **What is the AWS SAM CLI?**
  * Keywords, concepts, or topics that should be in the response:
    * SAM CLI is the command line interface for our serverless application model
  * Possible follow-up questions:
    * **What can we do with the AWS SAM CLI?**
      * We can use it to execute environments to locally build, test, and debug applications
      * We can use it to deploy our applications to AWS
      * We can use it to create secure continuous integration and deployment pipelines

## Lambda

[Back to top](#unit:-aws)

* **What is lambda?**
  * Keywords, concepts, or topics that should be in the response:
    * A Function-as-a-Service (FaaS) offering by AWS which allows execution of code without managing a cloud server like EC2
    * Highly scalable and flexible - very cost effective for some business use cases
    * Part of "serverless" technology where maintenance of virtual machines like EC2 not needed by the developer
    * Possible follow-up questions
      * **What do we mean by saying Lambda is serverless?**
        * We provide the code to run but don't have to manage a server, AWS takes care of that for us

* **Advantages / disadvantages of serverless?**
  * Keywords, concepts, or topics that should be in the response:
    * Benefits
      * less maintenance
      * rapid scaling
      * modular & composable
      * event-driven
    * Downsides
      * first request is slower (cold start)
      * limitations on runtime, size of function
      * AWS Lambda relies on the AWS infrastructure, developers won't be able to install any extra software if the code needs it
    * Possible follow-up questions:

* **What languages does Lambda support?**
  * Keywords, concepts, or topics that should be in the response:
    * Lambda natively supports Java, Go, PowerShell, Node.js, C#, Python, and Ruby code
    * Provides a Runtime API which allows you to use any additional programming languages

* **What are some use cases for AWS Lambda?**
  * Keywords, concepts, or topics that should be in the response:
    * Assists with ETL procedure
    * Data can be filtered and transformed using AWS Lambda
    * Data processing such as real-time streaming analytics can be done with AWS Lambda
    * Data collection, processing, and analysis for IoT devices.
    * Running scheduled tasks such as backups, cleanups, and maintenance jobs using CloudWatch Events.
    * Backend for serverless web applications, handling HTTP requests via API Gateway.
    * Sending notifications and alerts in response to events like database updates or incoming messages.

* **What is the pricing model for lambda?**
  * Keywords, concepts, or topics that should be in the response:
    * Charged based on number of requests + duration (down to ms)
    * Up to 1M requests per month in free tier

* **What is meant by "serverless" in the context of AWS Lambda?**
  * "Serverless" in the context of AWS Lambda means that the underlying infrastructure management, such as server provisioning, scaling, and maintenance, is completely abstracted away from the user. Developers can focus on writing and deploying code without worrying about the underlying hardware.
  * AWS Lambda automatically scales the compute capacity to meet the incoming request rate and handles all the server-side logic, allowing developers to build applications quickly and efficiently.

* **Why are IAM roles important for Lambda functions, and how do you configure them?**
  * IAM roles are crucial for Lambda functions because they define the permissions the function has to access other AWS services and resources.
  * By assigning an IAM role to a Lambda function, you can control what actions the function can perform, such as reading from an S3 bucket, writing to a DynamoDB table, or invoking other AWS services.
  * To configure IAM roles for Lambda functions:
    1. **Create an IAM Role**:
        * In the AWS Management Console, go to the IAM service.
        * Create a new role and select "Lambda" as the trusted entity.
        * Attach policies that grant the necessary permissions for the Lambda function.
    2. Assign the Role to the Lambda Function:
        * In the AWS Lambda console, navigate to your function's configuration.
        * Under the "Execution role" section, choose the IAM role you created.

* **What is Function-as-a-Service (FaaS) and how does AWS Lambda fit into this model?**
  * **Function-as-a-Service (FaaS)** is a cloud computing model that allows developers to deploy individual functions in the cloud, which are executed in response to events.
  * AWS Lambda is a prime example of FaaS, providing a platform where developers can run code in response to triggers such as HTTP requests, changes in data, or scheduled events.

* **How do you create and deploy a Lambda function?**
  * To create and deploy a Lambda function, follow these steps:
    1. **Create the Function**:
        * Go to the AWS Lambda console and click "Create function."
        * Choose a function blueprint or author from scratch.
        * Configure the function name, runtime (e.g., Node.js, Python), and execution role.
    2. **Write the Code**:
        * Write the function code in the built-in editor or upload a .zip file containing your code.
        * Alternatively, use an S3 bucket to store the code and provide the bucket details.
    3. **Configure Triggers**:
        * Add triggers such as an API Gateway, S3 event, or CloudWatch Events to invoke the function.
    4. **Deploy the Function**:
        * Save the function configuration and deploy the code.
        * Test the function using the console or by triggering the configured events.

## DynamoDB

[Back to top](#unit:-aws)

### DynamoDB: CRITICAL

* **What is DynamoDB?**
  * Keywords, concepts, or topics that should be in the response:
    * A key-value document store type NoSQL database solution
    * Is a fully managed NoSQL database service
    * We don't have to worry about hardware provisioning, setup and configuration, replication or software patching
    * Has fast and flexible data access
    * DynamoDB also offers encryption
  * Possible follow-up questions:

* **What is the difference between SQL and NoSQL databases?**
  * Keywords, concepts, or topics that should be in the response:
    * `SQL`:
      * is a relational database where data is stored in rows and tables are linked in various ways to each other
      * Must exhibit four properties, known as ACID, Atomicity, Consistency, Isolation, Durability
      * Can scale `vertically`, horizontal scaling through sharding or partitioning logic is also possible, but not well-supported
    * `NoSQL`:
      * Is a non-relational database, and allows for more flexibility to use a format that best fits the data
      * Requires less pre-planning and pre-organizing the data
      * Scales better `horizontally`, which means adding additional servers or nodes to increase our load
      * Is sometimes defined as "not only SQL"
  * Possible follow-up questions:
* **What 4 types of structures would our NoSQL database most likely fall into?**
  * Keywords, concepts, or topics that should be in the response:
    * `Column-oriented`:
      * Data is stored in cells grouped in a virtually unlimited number of columns rather than rows
    * `Key-value stores`:
      * Uses a dictionary/map as the data model
      * This model represents data as a collection of key-value pairs
    * `Document stores`:
      * Uses documents to hold and encode data in standard formats, such as XML, YAML, JSON, and BSON
      * Benefit is that documents within a single database can have different data types
    * `Graph databases`:
      * Represents data on a graph that shows how different sets of data relate to each other
  * Possible follow-up questions:
* **What kind of keys can we specify in DynamoDB?**
  * Keywords, concepts, or topics that should be in the response:
    * Partition Key
    * Sort Key
  * Possible follow-up questions:
    * **In DynamoDB, what must a Primary Key consist of?**
      * Partition Key
* **What is the difference between global and local secondary indexes in DynamoDB?**
  * Keywords, concepts, or topics that should be in the response:
    * `Global secondary index`:
      * An index with both a partition key and a sort key that can be different from those on the base table
      * Queries on the index can span all of the data in the base table, across all partitions
      * Has no size limitations
      * Has its own provisioned throughput settings for read and write activity that are separate from those of the table
    * `Local secondary index`:
      * An index that has the same partition key as the base table, but different sort key
      * Every partition is scoped to a base table partition that has the same partition key value
      * The total size of indexed items for any one partition key value cannot exceed 10 GB
  * Possible follow-up questions:
* **How do we go about creating a DynamoDB table using the AWS Management Console of AWS CLI?**
  * Keywords, concepts, or topics that should be in the response:
    * Open DynamoDB console
    * Choose Create table
    * When settings are done, choose `Create`
  * Possible follow-up questions:
* **What is a DynamoDB projection?**
  * Keywords, concepts, or topics that should be in the response:
    * A parameter that defines which fields will be returned from the table
  * Possible follow-up questions:
* **What are some ways we can read data from DynamoDB? What are some differences between the different ways to read data?**
  * Keywords, concepts, or topics that should be in the response:
    * `getItem`
      * Specify exact value of Primary Key (Partition Key & Sort Key)
      * Returns exactly 0 or 1 items
      * Will consume Read Capacity Units (RCUs) based on the size of the item
    * `query`
      * Specify exact value of Partition Key and optionally a Sort Key
      * Optionally add filter conditions on non-key attributes (not index optimized, still consumes RCUs whether or not items match the filter)
      * Returns matching items (possibly multiple)
      * Will consume RCUs based on the size of the items matching the key conditions, returning a single aggregated result
    * `scan`
      * Don't specify any keys
      * Optionally specify filter conditions on non-key attributes
      * Return all items from the table that match filter expression
      * Will consume RCUs to read all items on the table
  * Possible follow-up questions:

### DynamoDB: HIGH

* **When would you use a SQL database?**
  * Keywords, concepts, or topics that should be in the response:
    * Make it easy to handle a great deal of information
    * When one user updates a specific record, every instance of that database automatically refreshes and updates in real-time
  * Possible follow-up questions:
* **When would you use a NoSQL database?**
  * Keywords, concepts, or topics that should be in the response:
    * NoSQL is more important when we need the data fast, with ever changing requirements from a company
    * NoSQL is a good choice when we have large amounts or ever-changing data sets that don't fit into a relational model
    * If we have a lot of unstructured data, then Document store databases are a good fit
    * For quick access then we would be looking at key-value store
  * Possible follow-up questions:
* **Which one should we use generally? `Global secondary index` or `Local secondary index`? Why?**
  * Keywords, concepts, or topics that should be in the response:
    * We should use `Global secondary index`, unless we want strong consistency in our query results, then we use `Local secondary index`
  * Possible follow-up questions:
* **Do we need to provision a server for the application to run on when creating a DynamoDB instance?**
  * Keywords, concepts, or topics that should be in the response:
    * No
  * Possible follow-up questions:
* **What is the AWS SDK DynamoDB Client?**
  * Keywords, concepts, or topics that should be in the response:
    * This is used to help us handle DynamoDB requests through JavaScript
  * Possible follow-up questions:
    * **How do we import the DynamoDBClient into our JavaScript code?**

    ```javascript
    import { DynamoDBClient, BatchExecuteStatementCommand } from "@aws-sdk/client-dynamodb";
    ```

* **What is the DocumentClient?**
  * Keywords, concepts, or topics that should be in the response:
    * It simplifies working with items in the Amazon DynamoDB by abstracting away the notion of attribute values
    * Annotates native JavaScript types supplied as input parameters
    * Converts annotated response data to native JavaScript types
    * Helps simplify the JavaScript development experience with Amazon DynamoDB

    * | JavaScript Type | DynamoDB AttributeValue |
      | --------------- | ----------------------- |
      | String | S |
      | Number | N |
      | Boolean | BOOL |
      | null | NULL |
      | Array | L |
      | Object | M |
      | Buffer, File, Blob, ArrayBuffer, DataView, and JavaScript typed arrays | B |

  * Possible follow-up questions:
    * **What are some methods we can call using the DocumentClient?**
      * `batchGet(params, callback) => AWS.Request`
        * Returns the attributes of one or mote items from one or more tables
      * `batchWrite(params, callback) => AWS.Request`
        * Puts or deletes multiple items in one or more tables
      * `createSet(list, options) => void`
        * Creates a set of elements inferring the type of set from the type of the first element
      * `delete(params, callback) => AWS.Request`
        * Deletes a single item in a table by Primary Key
      * `get(params, callback) => AWS.Request`
        * Returns a set of attributes for the item with the given Primary Key
      * `put(params, callback) => AWS.Request`
        * Creates a new item, or replaces an old item with a new item
      * `query(params, callback) => AWS.Request`
        * Directly access items from a table by Primary Key or a Secondary INdex
      * `scan(params, callback) => AWS.Request`
        * Returns one or more items and item attributes
      * `transactGet(params, callback) => AWS.Request`
        * Atomically retrieves multiple items from one or more tables
      * `transactWrite(params, callback) => AWS.Request`
        * Synchronous write operation that groups up to 25 action requests
      * `update(params, callback) => AWS.Request`
        * Edits an existing item's attributes, or adds a new item to the table if it does not already exist

### DynamoDB: REGULAR

* **How many `Global secondary indexes` can a DynamoDB table have? What about `Local secondary indexes?`**
  * `Global secondary index`: 20
  * `Local secondary index`: 5

## Cognito

[Back to top](#unit:-aws)

* **What is AWS Cognito?**
  * Keywords, concepts, or topics that should be in the response:
    * Provides authentication, authorization, and user management for our web and mobile applications
    * Our users can sign in directly with a username and password, or through 3rd party logins such as Facebook, Amazon, Google, or Apple
  * Possible follow-up questions:
    * **What are the 2 main pools of AWS Cognito? What do they do?**
      * `User Pools`
        * Sign-up and sign-in services
        * A built-in, customizable web UI to sign in users
        * Social sign-in with Facebook, Google, Login with Amazon, and Sign in with Apple
        * User directory management and user profiles
        * Security features such as multi-factor authentication (MFA), checks for compromised credentials, account takeover protection, and phone and email verification
        * Customized workflows and user migration through AWS Lambda triggers
      * `Identity Pools`
        * Our users can obtain temporary AWS credentials to access AWS services, such as Amazon S3 and DynamoDB
        * Support anonymous guest users
      * We can use them separately or together

## CloudFormation

[Back to top](#unit:-aws)

### CloudFormation: CRITICAL

* **What is AWS CloudFormation?**
  * Keywords, concepts, or topics that should be in the response:
    * A service that helps us model and set up our AWS resources so that we can spend less time managing those resources and more time focusing on our applications that run on AWS

* **What AWS service is an "Infrastructure as Code" tool?**
  * Keywords, concepts, or topics that should be in the response:
    * AWS CloudFormation

* **What are some benefits of Infrastructure as Code?**
  * Keywords, concepts, or topics that should be in the response:
    * Versioning - track changes over time by checking into version control system
    * Transparency & visibility of all infrastructure
    * Easy scaling & replication

## CloudFormation: HIGH

* **What are some features of AWS CloudFormation?**
  * Keywords, concepts, or topics that should be in the response:
    * We can create templates that describes all the AWS resources that we want
    * CloudFormation will take care of all the provisioning and configuration of the resources for us
  * Possible follow-up questions:
    * **What are some AWS resources we can describe using CloudFormation templates?**
      * AWS EC2 instances
      * AWS RDS DB instances
  
* **What are some benefits of AWS CloudFormation?**
  * Keywords, concepts, or topics that should be in the response:
    * We can create a template that describes all of the resources and properties
    * CloudFormation will provision the autoscaling group, load balance, and DB for us
    * We can delete the stack which will delete all the resources in the stack
    * A great way to manage the collection of resources as a single unit
    * Can quickly replicate the whole infrastructure across multiple regions
    * Can easily control and track changes to our infrastructure

* **What is a template?**
  * Keywords, concepts, or topics that should be in the response:
    * It's a form of JSON or YAML or Text file
    * Has the extension `.json`, `.yaml`, `.template`, or `.txt`
    * Whenever we create a stack we can specify a template that CloudFormation is going to use

* **What is a stack?**
  * Keywords, concepts, or topics that should be in the response:
    * We manage related resources as a single unit called a stack
    * Create, update, delete a collection of resources by creating, updating, deleting stacks
    * Everything in the stack is defined by the CloudFormation template
  * Possible follow-up questions:
    * **How do we work with a stack?**
      * Can work with stacks by using the CloudFormation console or AWS CLI

* **What is the difference between a resource and a Stack?**
  * Keywords, concepts, or topics that should be in the response:
    * A Stack is a collection of cloud resources that can be managed and deployed as a group

## CloudFormation: REGULAR

* **Explain the following sections in a CloudFormation template**
  * Keywords, concepts, or topics that should be in the response:
    * Resources - the cloud resources you want to use
    * Parameters - enable you to input custom values to your template each time you create or update a stack
    * Rules - validates a parameter or a combination of parameters passed to a template during a stack creation or stack update
    * Conditions - contains statements that define the circumstances under which entities are created or configured
    * Outputs - declares output values that you can import into other stacks, return in response, or view on the AWS CloudFormation console

* **What are Change Sets?**
  * Keywords, concepts, or topics that should be in the response:
    * If we need to make any changes to running resources in a given stack we can generate a Change Set
    * Summary of our proposed changes
    * Allows us to see how our changes may impact our running resources, especially for critical resources before implementing them

## CloudWatch

[Back to top](#unit:-aws)

### CloudWatch: CRITICAL

* **What is AWS CloudWatch?**
  * Keywords, concepts, or topics that should be in the response:
    * It is AWS's monitoring and management service which is designed to maintain services and resources we are using
  * Possible follow-up questions:
    * **How does AWS CloudWatch help us achieve that?**
      * It will collect data and statistics
      * It will display insights on AWS services that we are using

* **What are some benefits to using AWS CloudWatch?**
  * Keywords, concepts, or topics that should be in the response:
    * The collected data will be in logs
    * We can create automated actions
    * Troubleshooting our apps will also be much easier

* **What are some features of AWS CloudWatch?**
  * Logging
  * Metrics

### CloudWatch: HIGH

* **What does the logging service include?**
  * Keywords, concepts, or topics that should be in the response:
    * Storing
    * Monitoring
    * Viewing
    * Capturing
    * Managing Service
    * Application Logs

* **Any examples of AWS CloudWatch services?**
  * Keywords, concepts, or topics that should be in the response:
    * CloudWatch Logs Insights
    * CloudWatch Logs
    * CloudWatch Alarms
    * CloudWatch Events

### CloudWatch: REGULAR

* **What does CloudWatch Logs Insights do?**
  * Keywords, concepts, or topics that should be in the response:
    * It's an interactive tool that helps developers visualize and analyze log data
    * Can create time-series graphs to visualize data
    * Can publish to CloudWatch dashboard

## CodeBuild

[Back to top](#unit:-aws)

### CodeBuild: CRITICAL

* **What is AWS CodeBuild?**
  * Keywords, concepts, or topics that should be in the response:
    * Is a service provided by AWS which manages in-house build service
    * Helps the compilation of source code, testing, and production of software packages that are ready to be deployed

* **What are some benefits of AWS CodeBuild?**
  * Keywords, concepts, or topics that should be in the response:
    * No need for management, allocation, or provision to scale the build servers as this is automatically scaled for us
    * Build operations occur concurrently in servers, thereby providing the largest advantage of not having to leave any builds waiting in the queue

* **How does CodeBuild automate the release process?**
  * Keywords, concepts, or topics that should be in the response:
    * It can be easily setup and configured by setting up CodeBuild and then integrating it directly with CodePipeline
    * AWS will take care of the continuous integration and continuous deployment process

* **Can you give me a brief rundown of the build process when we are using AWS CodeBuild?**
  * Keywords, concepts, or topics that should be in the response:
    1. CodeBuild will create a temporary container used for computing purposes. This is done on the defined class for the building project
    2. Load the required runtime and pull the source code
    3. Commands will be executed and the project is configured
    4. Project is uploaded, along with the artifacts that are generated and placed in an S3 bucket
    5. The Compute Container is no longer required so the developers can destroy it
    6. When we are building, CodeBuild will output logs into Amazon CloudWatch logs for us to monitor

## CodePipeline

[Back to top](#unit:-aws)

* **What is AWS CodePipeline?**
  * Keywords, concepts, or topics that should be in the response:
    * Service provided by AWS for continuous integration and continuous delivery services
    * Automates the build, test, and deploy phases every time there is a change to the code
    * AWS's implementation of Jenkins

* **When should you use AWS CodePipeline?**
  * Use AWS CodePipeline when you need to automate the entire CI/CD workflow, including code commits, builds, tests, and deployments.
  * It's ideal for orchestrating complex release processes and ensuring that your software delivery pipeline is consistent and repeatable

* **What are some benefits of AWS CodePipeline?**
  * Keywords, concepts, or topics that should be in the response:
    * Ensures that we can reliably deliver new software updates and features rapidly
    * Only pay for what we use
    * Easy to integrate, can use our own custom plugins

## CodeDeploy

[Back to top](#unit:-aws)

* **What is AWS CodeDeploy?**
  * Keywords, concepts, or topics that should be in the response:
    * A service that automates the process of deploying code to any instances, be it on local servers or AWS EC2 instances

* **When should you use AWS CodeDeploy?**
  * Use AWS CodeDeploy when you need to automate the deployment of applications to various compute environments such as EC2, Lambda, or on-premises servers.
  * It is ideal for managing deployment complexity, ensuring consistency, and minimizing downtime through strategies like blue/green deployments.

* **What are some benefits of AWS CodeDeploy?**
  * Keywords, concepts, or topics that should be in the response:
    * Helps developers release new builds and model features and avoid any downtime during the deployment process

## CodeCommit

[Back to top](#unit:-aws)

* **What is AWS CodeCommit?**
  * Keywords, concepts, or topics that should be in the response:
    * Similar to Github
    * Source control service provided in AWS that helps developers host git repositories safely and in a highly scalable manner

* **What are some benefits of AWS CodeCommit?**
  * Keywords, concepts, or topics that should be in the response:
    * Developers can eliminate the requirement of setting up and maintaining a source control system and scaling the infrastructure

## IAM

[Back to top](#unit:-aws)

### CRITICAL

* **What is AWS IAM?**
  * AWS IAM, or Identity and Access Management, is a service provided by Amazon Web Services (AWS) that enables you to securely control access to AWS services and resources for your users.
  * IAM allows you to manage users, groups, roles, and permissions, helping you adhere to the least privilege principle and enforce security best practices within your AWS environment.

* **How can I create new users in AWS IAM?**
  * Using AWS Management Console (Portal)
    * **Creating New Users**
      1. Sign in to the AWS Management Console and open the IAM console at <https://console.aws.amazon.com/iam/>.
      2. In the navigation pane, choose Users and then choose Add user.
      3. Enter the User Name and select the type of access (Programmatic access, AWS Management Console access, or both).
      4. Set Permissions:<br>
        a. Choose Attach existing policies directly to assign permissions.<br>
        b. Choose Add user to group to add the user to an existing group.<br>
        c. Choose Copy permissions from existing user to copy permissions from another user.<br>
        d. Choose Attach existing policies directly and select the policies you want to attach.<br>
      5. Set permissions boundary (optional).
      6. Add Tags (optional) to the user.
      7. Review and Create:<br>
        a. Review your choices and click Create user.

* **How do I create new groups in AWS IAM?**
  * Using AWS Management Console (Portal)
    * **Creating New Groups**
       1. Sign in to the AWS Management Console and open the IAM console at <https://console.aws.amazon.com/iam/>.
       2. In the navigation pane, choose Groups and then choose Create New Group.
       3. Enter the Group Name and click Next Step.
       4. Attach Policy:
      * Select the policies you want to attach to the group.
       5. Review and Create:
      * Review your choices and click Create Group.

### HIGH

* **How can I use AWS IAM to interact with AWS resources?**
  * AWS Identity and Access Management (IAM) enables you to manage access to AWS services and resources securely.
  * Here's how you can use IAM to interact with AWS resources:
    * **Create IAM Users**: You can create IAM users with specific permissions to access AWS services programmatically or through the AWS Management Console.
    * **Create IAM Groups**: Group users with similar permissions together by creating IAM groups and attaching policies to those groups.
    * **Assign Policies**: IAM policies define permissions, and you can attach them to IAM users, groups, or roles. Policies specify what actions are allowed or denied on which resources.
    * **IAM Roles**: IAM roles are sets of permissions that you can create and manage to enable IAM users, applications, or AWS services to assume their permissions.

## VPC

[Back to top](#unit:-aws)

### CRITICAL

* **What is a VPC (Virtual Private Cloud) in AWS?**
  * A Virtual Private Cloud (VPC) is a virtual network environment within the Amazon Web Services (AWS) cloud where you can launch AWS resources.
  * It provides you with complete control over your virtual networking environment, including the selection of your IP address range, creation of subnets, and configuration of route tables and network gateways.
  * With VPC, you can isolate your resources and securely connect them to your on-premises network or other AWS services.

* ** How can I requisition a new VPC in AWS?**
  * To requisition a new VPC in AWS, follow these steps:
    * **Sign in to the AWS Management Console** and **navigate to the VPC dashboard**.
    * Click on **"Create VPC"** to start the wizard.
    * Enter a **name for your VPC** and **specify the IPv4 CIDR block** for the VPC (e.g., 10.0.0.0/16).
    * Optionally, you can configure an **IPv6 CIDR block for the VPC**.
    * Choose whether to **enable DNS hostname resolution and DNS support** for the VPC.
    * Click **"Create VPC"** to create the **new VPC**.
  * Once created, you can further customize your VPC by adding subnets, route tables, network ACLs, security groups, and VPN connections as needed.

* ** How do I requisition new subnets within an AWS VPC?**
  * To requisition new subnets within an AWS VPC, follow these steps:
    * Navigate to the **VPC dashboard** in the AWS Management Console.
    * **Select the VPC** for which you want to create subnets.
    * Click on **"Subnets"** in the navigation pane.
    * Click on **"Create subnet"** to start the subnet creation wizard.
    * Enter a **name for the subnet** and **select the VPC** in which you want to create the subnet.
    * **Specify the IPv4 CIDR block** for the subnet within the CIDR block of the VPC.
    * Optionally, you can configure an **IPv6 CIDR block** for the subnet.
    * Choose the **availability zone** in which you want to create the subnet.
    * Click **"Create subnet"** to create the **new subnet**.

## CloudFront

[Back to top](#unit:-aws)

### CRITICAL

* **What is AWS CloudFront?**
  * AWS CloudFront is a content delivery network (CDN) service provided by Amazon Web Services (AWS) that accelerates the delivery of your web content, including static and dynamic assets, to users across the globe.
  * CloudFront caches your content at edge locations located in multiple geographic regions, reducing latency and improving the overall performance of your web applications.
  * It also provides features such as DDoS protection, HTTPS encryption, and integration with other AWS services to deliver a secure and scalable content delivery solution.

* **How does caching work in AWS CloudFront, and what are caching policies?**
  * In AWS CloudFront, caching improves the performance of your web applications by storing copies of your content at edge locations closer to your users. When a user requests content that is cached in a CloudFront edge location, CloudFront serves the content directly from the cache, reducing the need to fetch it from the origin server.
  * **Caching policies** in CloudFront allow you to control how CloudFront caches and forwards requests to your origin server based on various criteria such as path patterns, query strings, and HTTP headers.

### HIGH

* **How can I manage caching invalidations and behaviors in AWS CloudFront?**
  * In AWS CloudFront, you can manage caching invalidations and behaviors to control how CloudFront caches and serves your content:
    * **Invalidations**: CloudFront allows you to invalidate cached objects to remove them from edge locations before they expire naturally. You can create invalidation requests to invalidate specific files, directories, or wildcard patterns, ensuring that users receive the latest version of your content when necessary.
    * **Behaviors**: CloudFront behaviors define how CloudFront processes and caches requests based on request characteristics such as path patterns, query strings, and HTTP headers. You can create multiple caching behaviors to customize caching settings for different types of content and request patterns, enabling fine-grained control over caching behavior and content delivery optimization.

* **What are signed URLs and cookies in AWS CloudFront?**
  * In AWS CloudFront, signed URLs and cookies are mechanisms for controlling access to your content and restricting distribution to authorized users:
    * **Signed URLs**: CloudFront signed URLs allow you to grant temporary access to private content by generating URLs with embedded cryptographic signatures. You can create signed URLs with specific expiration times and optional access controls, such as IP address restrictions and custom policy statements, to securely distribute content to trusted users and applications.
    * **Signed Cookies**: CloudFront signed cookies provide an alternative method for controlling access to private content by using HTTP cookies instead of URL parameters. You can generate signed cookies with expiration times and access controls similar to signed URLs, allowing you to enforce access policies and authenticate users based on cookie-based authentication mechanisms.

### REGULAR

* **How does geo-restriction work in AWS CloudFront?**
  * AWS CloudFront offers geo-restriction capabilities to control access to your content based on the geographic location of the viewer:
    * **Whitelist**: You can create a whitelist of countries or regions from which you want to allow access to your content. Requests originating from whitelisted locations are served normally, while requests from non-whitelisted locations are denied access with an HTTP 403 Forbidden response.
    * **Blacklist**: Conversely, you can create a blacklist of countries or regions that you want to deny access to your content.

* **Can I use an Application Load Balancer (ALB) as an origin for AWS CloudFront?**
  * Yes, you can use an AWS Application Load Balancer (ALB) as an origin for AWS CloudFront distributions.
  * By configuring CloudFront to use an ALB as its origin, you can leverage the scalability, availability, and routing capabilities of ALB to distribute incoming requests across multiple backend targets, such as EC2 instances, containers, and Lambda functions. CloudFront retrieves content from the ALB origin servers and caches it at edge locations.

## ELB

[Back to top](#unit:-aws)

### CRITICAL

* **What is AWS Elastic Load Balancing (ELB), and how does it contribute to high availability and scalability in a DevOps environment?**
  * AWS Elastic Load Balancing is a service that automatically distributes incoming application traffic across multiple targets, such as EC2 instances, containers, or Lambda functions.
  * It contributes to high availability and scalability in DevOps environments by distributing traffic, ensuring fault tolerance, and optimizing resource utilization.

* ** Explain the different types of Elastic Load Balancers provided by AWS, and when would you choose one over the other?**
  * AWS offers three types of ELBs:
    * **Application Load Balancer (ALB)**: Best for HTTP/HTTPS traffic and advanced routing features.
    * **Network Load Balancer (NLB)**: Ideal for high-performance, low-latency, and TCP/UDP traffic.
    * **Classic Load Balancer/Elastic Load Balancer**: Provides basic load balancing for applications that rely on classic EC2 instances.
  
* **How can you create and configure an Elastic Load Balancer in AWS, and what are the key parameters you need to define during setup?**
  * You can create an ELB using the AWS Management Console, AWS CLI, or CloudFormation.
  * During setup, you define parameters such as the listener configuration, target groups, security groups, and optionally, the routing rules for an ALB.

### HIGH

* **Explain the concept of cross-zone load balancing in AWS ELB.**
  * Cross-zone load balancing allows ELBs to evenly distribute traffic across instances in different Availability Zones.
  * By default, ELBs evenly distribute traffic to all healthy instances, regardless of the AZ they belong to, promoting balanced traffic distribution.

* **How can you ensure the security of Elastic Load Balancers?**
  * Best practices for ELB security include
    * using **security groups** to restrict access to your load balancer and back-end instances
    * enabling **encryption using SSL/TLS**
    * using **Web Application Firewall (WAF)** for advanced security features.

* **What are sticky sessions in Elastic Load Balancers?**
  * Sticky sessions, also known as session affinity or session persistence, is a feature of Elastic Load Balancers (ELBs) that ensures that subsequent requests from a client are routed to the same backend target that handled the initial request.
  * With sticky sessions enabled, ELB associates a user's session with a specific backend target for a configurable duration, typically based on a session cookie or source IP address.
  * This allows stateful applications, such as those that rely on user sessions or shopping carts, to maintain session consistency and data integrity across multiple requests, improving user experience and application performance.

## ECS

[Back to top](#unit:-aws)

### CRITICAL

* **What is AWS ECS?**
  * AWS ECS, or Elastic Container Service, is a fully managed container orchestration service provided by Amazon Web Services.
  * It allows you to run Docker containers at scale, managing the infrastructure required to deploy, scale, and manage containerized applications.

* **What is an ECS cluster?**
  * An ECS cluster is a logical grouping of EC2 instances or Fargate tasks that run containerized applications. It acts as the foundation for running and managing containers in ECS.

* **What is an ECS service?**
  * An ECS service is a configuration that allows you to run and maintain a specified number of instances of a task definition simultaneously in an ECS cluster. It ensures that the desired number of tasks are running and handles task placement and scaling.

### HIGH

* **How does ECS handle task placement?**
  * ECS uses task placement strategies to determine where to place tasks within a cluster.
  * You can specify constraints, such as CPU and memory requirements, host availability, or custom placement rules, to control where tasks are scheduled.

* **How does auto-scaling work in ECS?**
  * ECS supports auto-scaling at the service level, allowing you to automatically adjust the number of tasks in response to changes in demand or other metrics. You can define scaling policies based on CPU or memory utilization, request count, or custom CloudWatch metrics.

* **What are rolling updates in ECS?**
  * Rolling updates in ECS allow you to update your service's task definition and deploy new versions of your containers with minimal disruption.
  * ECS orchestrates the deployment, gradually replacing old tasks with new ones, ensuring that the service remains available throughout the process.

* **What is an ECS task definition?**
  * An ECS task definition is a blueprint for your application, defining parameters such as
    * which Docker image to use
    * how much CPU and memory to allocate
    * networking configuration
    * container dependencies.

## Route 53

[Back to top](#unit:-aws)

### CRITICAL

* **What is DNS, and what role does it play in networking?**
  * DNS stands for Domain Name System.
  * It translates domain names (e.g., <www.example.com>) into IP addresses (e.g., 192.0.2.1), allowing users to access websites and services using human-readable names rather than numerical IP addresses.

* **What is AWS Route 53?**
  * AWS Route 53 is a scalable and highly available Domain Name System (DNS) web service provided by Amazon Web Services.
  * It allows you to register domain names, route traffic to resources such as EC2 instances, load balancers, and S3 buckets, and perform health checks on your resources.

* **How do you register a domain name using AWS Route 53?**
  * To register a domain name with Route 53, you can use the AWS Management Console or the Route 53 API.
  * Simply search for the desired domain name, follow the registration process, and provide the necessary contact information and payment details.

### HIGH

* **What types of DNS records can you create in Route 53?**
  * Route 53 supports various types of DNS records (but not limited to), including
    * A records (IPv4 addresses)
    * AAAA records (IPv6 addresses)
    * CNAME records (canonical names)
    * MX records (mail exchange servers)
    * TXT records (text records)

* **What are the routing policies available in Route 53, and when would you use each?**
  * Route 53 supports several routing policies, including Simple, Weighted, Latency-Based, Failover, Geolocation, and Multi-Value.
  * Each policy is used in different scenarios, such as load balancing traffic across multiple resources, routing traffic based on geographic location, or implementing failover for high availability.

### REGULAR

* **What is TTL (Time to Live), and how does it affect DNS resolution?**
  * TTL is a setting in DNS records that specifies the amount of time a DNS resolver should cache the record before querying the authoritative DNS server again.
  * Shorter TTL values result in faster DNS updates but can increase DNS query load.

* **What is the difference between a CNAME record and an Alias record in Route 53?**
  * A **CNAME record** is a canonical name that maps an alias name to the true or canonical domain name.
  * An **Alias record**, on the other hand, is a Route 53-specific record type that maps a DNS name to specific AWS resources such as ELB load balancers, CloudFront distributions, or S3 buckets.

* **How do health checks work in Route 53, and why are they important?**
  * Health checks in Route 53 monitor the health and availability of your resources, such as EC2 instances or load balancers.
  * They periodically send requests to your endpoints and change DNS responses based on the health status.
  * Health checks are crucial for ensuring the reliability and availability of your applications and services.

## SQS

[Back to top](#unit:-aws)

### CRITICAL

* **What is AWS SQS?**
  * AWS SQS, or Simple Queue Service, is a fully managed message queuing service provided by Amazon Web Services.
  * It allows you to decouple and scale microservices, distributed systems, and serverless applications by enabling asynchronous communication between components.

* **What are the limitations of Amazon SQS regarding message size and retention periods?**
  * Amazon SQS has a message **size limit of 256 KB** and a retention period ranging from **1 minute to 14 days**.

* **What is a queue access policy in AWS SQS?**
  * A queue access policy in AWS SQS is a JSON document that defines who can access a queue and what actions they can perform.
  * It allows you to control permissions such as sending messages, receiving messages, and deleting messages, using AWS Identity and Access Management (IAM) policies.

### HIGH

* **What is message visibility timeout in AWS SQS?**
  * Message visibility timeout in AWS SQS is the amount of time that a message remains invisible to other consumers after it has been received by a consumer.
  * During this time, the consumer processes the message, and if it fails to process it within the timeout period, the message becomes visible again and can be processed by another consumer.

* **What is a dead letter queue (DLQ) in AWS SQS?**
  * A dead letter queue (DLQ) in AWS SQS is a separate queue that receives messages that cannot be processed successfully after a certain number of attempts.
  * It helps you isolate and troubleshoot failed messages by storing them separately from the main queue, allowing you to analyze and reprocess them later.

* **What is a delay queue in AWS SQS?**
  * A delay queue in AWS SQS is a queue that delays the delivery of messages for a specified amount of time after they are sent.
  * This delay can be useful for scenarios where you want to introduce a delay before processing messages, such as implementing retry mechanisms or rate limiting.

* **What is a FIFO queue in AWS SQS?**
  * A FIFO (First-In-First-Out) queue in AWS SQS is a type of queue that preserves the order in which messages are sent and received.
  * It ensures that messages are processed in the order they are sent and supports exactly-once processing, deduplication, and message grouping based on message attributes.

## SNS

[Back to top](#unit:-aws)

### CRITICAL

* **What is AWS SNS?**
  * AWS SNS, or Simple Notification Service, is a fully managed messaging service provided by Amazon Web Services.
  * It enables you to send notifications and messages to distributed systems, mobile devices, email, SMS, and other endpoints.

* **What is the fan-out pattern in AWS SNS and SQS?**
  * The fan-out pattern is a messaging pattern where messages published to an SNS topic are delivered to multiple SQS queues, allowing multiple consumers to process the same message independently.

* **How do you implement the fan-out pattern with AWS SNS and SQS?**
  * To implement the fan-out pattern with AWS SNS and SQS:
    * Create an SNS topic.
    * Subscribe multiple SQS queues to the SNS topic.
    * Publish messages to the SNS topic.
    * Each SQS queue receives a copy of the message and processes it independently.

## KMS

[Back to top](#unit:-aws)

### CRITICAL

* **What is AWS KMS and what are its main features?**
  * AWS Key Management Service (KMS) is a managed service that makes it easy to create and control cryptographic keys and to use them to encrypt data across a wide range of AWS services and in your applications.
  * The main features of AWS KMS include:
    * **Centralized Key Management**: Manage encryption keys and control their use across a wide range of AWS services and in your applications.
    * **Security and Compliance**: Keys are stored in FIPS 140-2 validated hardware security modules (HSMs) and are protected by AWS Identity and Access Management (IAM) policies.
    * **Key Rotation**: Automatic rotation of customer master keys (CMKs) to meet security and compliance requirements.
    * **Data Encryption**: Integration with various AWS services like S3, EBS, RDS, and others for seamless data encryption.
    * **Audit and Compliance**: Integration with AWS CloudTrail to log all key usage and management activities.

* **How do you create a KMS key in AWS KMS?**
  * To create a KMS key in AWS KMS:
    * **Sign in to the AWS Management Console**: Navigate to the KMS service.
    * **Create a Key**: Click on "Create key" and select the key type (symmetric or asymmetric).
    * **Configure Key Settings**: Provide an alias and description for the key.
    * **Define Key Usage Permissions**: Set the IAM roles or users who can administer and use the key.
    * **Enable Key Rotation (optional)**: Enable automatic yearly rotation for the key if required.
    * **Review and Create**: Review the settings and create the key.

### HIGH

* **What is the difference between a symmetric KMS key and an asymmetric KMS key in AWS KMS?**
  * **Symmetric KMS key**:
    * Uses a single encryption key for both encryption and decryption.
    * It is used for most AWS services that support encryption and is ideal for scenarios where you only need one key to encrypt and decrypt data.
  * **Asymmetric KMS key**:
    * Uses a public and a private key pair.
    * The public key is used for encryption and the private key is used for decryption.
    * This is useful for digital signatures and other use cases that require public key cryptography.

* **How does the AWS KMS service integrate with other AWS services to provide data encryption?**
  * AWS Key Management Service (KMS) integrates with various AWS services to offer data encryption and key management such as:
    * **Amazon S3**: KMS enables server-side encryption for objects stored in S3 buckets using the SSE-KMS option. Users can specify a KMS key during object upload or configure default bucket encryption.
    * **Amazon EBS**: KMS allows encrypting EBS volumes by selecting a KMS key at volume creation.
    * **Amazon RDS**: KMS integration facilitates encryption at rest for database instances and snapshots. Users choose a KMS key when creating an encrypted instance.

* **Why to integrate AWS KMS with AWS CloudTrail?**
  * AWS KMS is integrated with AWS CloudTrail, which provides detailed logs of all API calls made within your AWS account, including those made to KMS. This integration helps in auditing and compliance by providing:
    * **Logging of Key Usage**: Tracks when and how keys are used, including encrypt, decrypt, and management operations.
    * **Security Monitoring**: Helps in detecting unauthorized access attempts or misconfigurations.
    * **Compliance Reports**: Assists in generating compliance reports by logging all key management activities.

## API Gateway

[Back to top](#unit:-aws)

### CRITICAL

* **Describe AWS API Gateway.**
  * AWS API Gateway is a fully managed service that enables developers to create, publish, maintain, monitor, and secure APIs at any scale.
  * It acts as a "front door" for applications to access data, business logic, or functionality from backend services such as AWS Lambda, Amazon EC2, or other web services.

* **What are resources and methods in AWS API Gateway, and how are they used?**
  * **Resources**: Resources are individual endpoints in your REST API that represent a collection of related API operations. For example, a resource might represent a specific URL path such as /users.
  * **Methods**: Methods are HTTP methods (such as GET, POST, PUT, DELETE) that are allowed on a resource. Each method can have different configurations, including request validation, authorization, and backend integration settings.
  * To use resources and methods:
    * **Create a Resource**: Define a new resource in your API, such as /items.
    * **Add Methods**: Attach HTTP methods to the resource. For example, you might add GET and POST methods to the /items resource.
    * **Configure Integrations**: Specify the backend service for each method. For instance, configure the GET method to invoke an AWS Lambda function that retrieves items.

### HIGH

* **How does AWS API Gateway process an HTTP request?**
  * AWS API Gateway processes an HTTP request in several stages:
    * **Request Receiving**: API Gateway receives the HTTP request.
    * **Mapping Templates**: It processes any request mapping templates to transform the incoming request data.
    * **Authorization**: API Gateway checks for authorization using IAM policies, Cognito user pools, custom authorizers, or API keys.
    * **Integration Request**: It forwards the request to the configured backend integration (e.g., AWS Lambda, HTTP endpoint, mock integration).
    * **Backend Processing**: The backend service processes the request and returns a response to API Gateway.
    * **Integration Response**: API Gateway processes any response mapping templates to transform the response data.
    * **Response Returning**: Finally, API Gateway returns the processed response to the client.

* **How do you create and deploy a REST API using AWS API Gateway?**
  * To deploy a REST API using AWS API Gateway:
    1. **Create an API**: Define the API with its resources and methods in the API Gateway console.
    2. **Configure Stages**: Create a stage (e.g., dev, test, prod) to manage different versions and environments of your API.
    3. **Deploy the API**:
    * In the API Gateway console, select the API you want to deploy.
    * Choose "Actions" and then "Deploy API."
    * Select the stage to which you want to deploy the API or create a new stage.

* **How does AWS API Gateway handle errors and retries?**
  * AWS API Gateway handles errors and retries using several mechanisms:
    * **Integration Responses**: Define how API Gateway transforms backend responses, including error responses. You can set up custom error mappings based on HTTP status codes.
    * **Client-Side Errors**: Errors in the 4xx range (e.g., 400 Bad Request, 401 Unauthorized) are typically due to client issues. API Gateway returns these errors directly to the client.
    * **Server-Side Errors**: Errors in the 5xx range (e.g., 500 Internal Server Error) are typically due to server or integration issues. API Gateway can automatically retry these requests.
    * **Retry Logic**: API Gateway can be configured with retry policies for certain integrations (e.g., AWS Lambda). You can specify the number of retries and the backoff strategy.

* **What is a cold start in the context of AWS Lambda and API Gateway?**
  * A cold start occurs when an AWS Lambda function is invoked after not being used for a while, resulting in additional latency as the Lambda service initializes a new execution environment.
  * This initialization includes loading the function code, setting up the runtime, and initializing any dependencies, which can add a noticeable delay to the request processing time.

* **How can you mitigate cold starts in AWS Lambda when using API Gateway?**
  * To mitigate cold starts in AWS Lambda when using API Gateway:
    * **Provisioned Concurrency**: Use provisioned concurrency to keep a specified number of function instances initialized and ready to handle requests.
    * **Optimize Function Initialization**: Reduce the initialization time by optimizing your function's initialization code and dependencies.
    * **Keep Functions Warm**: Implement a mechanism to periodically invoke your Lambda functions to keep them warm. This can be done using CloudWatch Events or another scheduling service.
    * **Minimize Dependencies**: Reduce the number of dependencies and their size to decrease the initialization time.
