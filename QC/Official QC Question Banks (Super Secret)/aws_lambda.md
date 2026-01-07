## Unit

# AWS Lambda

## Links

* [Required Questions](#required-questions)
* [Preferred Questions](#preferred-questions)
* [Stretch Questions](#stretch-questions)

## Required Questions

[Back to top](#unit)

* **What is an AWS Lambda function? How do you create one in the AWS Console, and what are common use cases?**
  * Keywords, concepts, or topics that should be in the response:
    * Serverless compute service executing code in response to triggers
    * Creation steps: 
      1. Open Lambda Console → "Create function"
      2. Choose runtime (Node.js/Python/Java etc.)
      3. Configure execution role (IAM)
      4. Write code or upload ZIP
    * Use cases: 
      - API backends (API Gateway)
      - Event processing (S3/SQS)
      - Cron jobs (CloudWatch Events)
  * Possible follow-up questions
    * What file formats can you upload for Lambda code?
    * How do you test a function in the console?
    * What's the maximum execution time?

* **Explain IAM roles for Lambda. How do they enable secure interactions with AWS services?**
  * Keywords, concepts, or topics that should be in the response:
    * Identity and Access Management (IAM) roles provide temporary credentials
    * Execution role attached to Lambda during creation
    * Principle of least privilege (e.g., S3 read-only access)
    * Trust policy allowing `lambda.amazonaws.com` to assume the role
  * Possible follow-up questions
    * How would you grant DynamoDB access to a Lambda?
    * What happens if the role lacks required permissions?
    * How do resource-based policies differ?

* **What are Lambda Layers? How do they optimize deployment packages?**
  * Keywords, concepts, or topics that should be in the response:
    * Shared code/dependency distribution mechanism
    * Separation of function code from dependencies
    * Reusable across multiple functions
    * Reduced deployment package size
    * Example: Node.js layer with `node_modules`
  * Possible follow-up questions
    * How many layers can a function use? (5)
    * How do you create a layer for Python packages?
    * What's the maximum layer size? (250MB)

* **How does CloudWatch help debug Lambda functions? What insights does it provide?**
  * Keywords, concepts, or topics that should be in the response:
    * Automatic logging of executions (stdout/stderr)
    * Metrics: Duration, Errors, Throttles, ConcurrentExecutions
    * CloudWatch Logs Insights for querying logs
    * X-Ray integration for tracing
  * Possible follow-up questions
    * How would you find a specific failed request?
    * What do "IteratorAge" metrics indicate for stream processing?
    * How to set up error alarms?

## Preferred Questions

[Back to top](#unit)

* **What are cold starts? How can you mitigate their impact?**
  * Keywords, concepts, or topics that should be in the response:
    * Initial latency when function initializes (≈100ms-2s)
    * Caused by: 
      - Container provisioning
      - Runtime initialization
      - Large dependencies/code
    * Mitigation:
      - Provisioned Concurrency (pre-warmed instances)
      - Smaller deployment packages
      - Avoid VPCs when possible
      - Keep functions warm (scheduled pings)
  * Possible follow-up questions
    * When are cold starts most problematic?
    * How does Provisioned Concurrency affect costs?
    * Why do VPCs increase cold start duration?

* **How does Lambda pricing work? When does it become cost-effective vs. EC2?**
  * Keywords, concepts, or topics that should be in the response:
    * Pay per request ($0.20/million) + duration (GB-seconds)
    * Cost-effective for: 
      - Sparse workloads
      - Variable traffic
    * Less efficient for:
      - High-traffic steady workloads
      - Constant background processes
  * Possible follow-up questions
    * How does memory allocation affect pricing?
    * What's the cost impact of 100ms vs 500ms execution?
    * How would you calculate break-even vs. EC2?

## Stretch Questions

[Back to top](#unit)

* **How would you implement state management in stateless Lambda functions?**
  * Keywords, concepts, or topics that should be in the response:
    * External storage: DynamoDB, ElastiCache, S3
    * Ephemeral caching with TTL
    * Step Functions for workflow state
    * Avoidance of filesystem/global variables
  * Possible follow-up questions
    * Why is global variable caching dangerous?
    * How do you manage database connections?
    * When would you use DynamoDB vs. Redis?