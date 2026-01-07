## Unit

# AWS CodePipeline

## Links

* [Required Questions](#required-questions)
* [Preferred Questions](#preferred-questions)

## Required Questions

[Back to top](#unit)

* **Explain AWS CodePipeline, CI/CD concepts, and CodePipeline's core architecture.**
  * Keywords, concepts, or topics that should be in the response:
    * **CodePipeline**: Fully managed CI/CD service automating release pipelines
    * **CI/CD**: Continuous Integration (merge/test code) + Continuous Delivery (deploy to environments)
    * **Architecture components**:
      - Pipeline: End-to-end workflow
      - Stages: Logical divisions (Source → Build → Test → Deploy)
      - Actions: Tasks within stages (e.g., "Invoke Lambda")
      - Transitions: Stage-to-stage movement
    * **Event-driven execution**: Triggered by code changes
  * Possible follow-up questions
    * How does this differ from Jenkins?
    * What's the relationship between pipelines and stages?
    * Can stages run in parallel?

* **What are the main components of a CodePipeline workflow? Describe each.**
  * Keywords, concepts, or topics that should be in the response:
    * **Source Stage**: Connects to repo (CodeCommit, GitHub, S3)
    * **Build Stage**: Compiles code (CodeBuild, Jenkins)
    * **Test Stage**: Automated tests (CodeBuild, 3rd-party tools)
    * **Deploy Stage**: Releases artifacts (CodeDeploy, CloudFormation, ECS)
  * Possible follow-up questions
    * How would you add a security scan stage?
    * Can you have multiple actions in one stage?
    * What artifact formats does CodePipeline support?

## Preferred Questions

[Back to top](#unit)

* **What monitoring and troubleshooting tools are available for pipelines?**
  * Keywords, concepts, or topics that should be in the response:
    * Pipeline execution history (success/failure states)
    * CloudWatch Metrics: Failed actions, duration
    * CloudTrail for API auditing
    * Detailed action logs (CodeBuild/CodeDeploy logs)
    * Visual debugging with CodePipeline console
  * Possible follow-up questions
    * How would you alert for stuck pipelines?
    * Where do you find "Action execution failed" details?
    * How do you retry failed actions?
