### Code Kata Exercise: Deploying and Managing a Web Application with CI/CD and AWS Beanstalk

---

## Objective
Create a fully automated deployment pipeline for a simple "Hello World" web application using Amazon Elastic Beanstalk, GitHub Actions, and AWS CloudWatch. This project will teach you about CI/CD, semantic versioning, monitoring, and alerting.

Make sure to commit code frequently and atleast daily. 

Use a public GitHub instance, and a Free Tier AWS instance. Remember to cleanup (delete) your AWS resources after. 

---

## Exercise Steps

### Basic Steps

1. **Create a "Hello World" Web Application**
   - Choose a Beanstalk-compatible programming language (Go, Java, .NET, Node.js, PHP, Python, Ruby).
   - Write a basic web application where accessing the `index.html` or root URL (`/`) displays "Hello World."
   - Add a visible semantic version (e.g., "v1.0.0") to the application. This can:
     - Be initially hardcoded as `1.0.0`.
     - Appear at the bottom of the `index.html`.
     - Or be accessible via a `/version` endpoint.

2. **Set Up GitHub Repository**
   - Create a public GitHub repository.
   - Frequently commit and push code changes (at least daily).
   - Use `.gitignore` to exclude sensitive files and unnecessary clutter.

3. **GitHub Actions: Build**
   - Set up a GitHub Actions workflow that automatically builds the application upon every commit to the `master` branch.
   - Use GitHub environment variables (e.g., build number) to assist with tasks like semantic versioning.

4. **Add Semantic Versioning**
   - Implement a build script to generate a semantic version (e.g., `v1.0.1`).
   - Increment the version automatically with each new commit.
     - **Hint:** Look into GitHub environment variables (including the build number) to help with versioning.

5. **Manual Deployment to AWS Elastic Beanstalk**
   - Deploy the application manually to Elastic Beanstalk using the AWS Management Console or Elastic Beanstalk CLI (`eb` command).
   - Verify the application is running by accessing the deployed URL.

6. **GitHub Actions: Deploy**
   - Set up a GitHub Actions workflow that deploys the application to Elastic Beanstalk upon every commit to the `master` branch.
   - **Hint:**  Use GitHub Secrets to store sensitive credentials (e.g., AWS keys).

7. **Logging with AWS CloudWatch**
   - Add somet logging to your application. 
   - Ensure your application sends application logs to AWS CloudWatch (and that you can view and search for them). 

8. **Error Handling and Alerting**
   - Add an endpoint (e.g., `/cause_error`) that triggers an error log.
   - Set up a CloudWatch alarm for `Error` level logs.
   - Configure the alarm to send notifications via:
     - **MS Teams Incoming Webhook**.
     - **Bonus**: AWS SNS for text message notifications.
   - **Tip:** Research and understand the concepts of MTTR (Mean Time to Recovery) and MTTD (Mean Time to Detection) and how alerting impacts these metrics.

9. **AWS Secrets Manager or Parameter Store**
   - Store some application settings (e.g., API keys, configuration variables) in AWS Secrets Manager or Parameter Store.
   - Update your application to fetch these settings dynamically.
   - Display one of the settings (e.g., a configuration value) on the `index.html` to confirm it works.

---

### Bonus Steps

1. **Scaling**
   - Configure your Elastic Beanstalk environment to scale to two instances.
   - Experiment with autoscaling settings.
   - **Question:** How does scaling up or down impact applications that are stateful vs. stateless?
   - **Tip:** Understand the benefits of stateless applications and how storing state elsewhere (e.g., in a database or distributed cache) can improve scalability and resilience.

2. **Health Checks**
   - Add a dedicated `/health` endpoint to your application.
   - Configure Beanstalk to use this endpoint for health monitoring.
   - Understand what happens if the hardware, JDK, OS, or the application itself fails (i.e., the health check fails).
   - Investigate Elastic Beanstalk's self-healing capabilities and how it replaces unhealthy instances to maintain availability.

3. **Blue/Green Deployment**
   - Enable and test Blue/Green Zero-down time deployment to minimize downtime during updates.
   - **Hint**: See Swap Environment URL functionality. 
   - Understand and configure connection draining. What happens if I do a Blue/Green deploy, and there's an existing longer running connection to the previous version ? 

4. **Elastic Beanstalk Configuration**
   - Create a `.ebextensions` configuration file to customize your environment.
   - Use it to perform an action (e.g., setting environment variables or installing additional dependencies).

5. **AWS Datastore Integration**
   - Connect your application to an AWS datastore:
     - Use S3 for file storage.
     - Use RDS for a relational database.
   - Update your application to interact with the datastore (e.g., displaying data from the database or retrieving files from S3).

6. **Advanced Elastic Beanstalk Features**
   - Access an instance directly using AWS Session Manager to troubleshoot.
   - Enable and use AWS X-Ray for distributed tracing.
   - Experiment with different Elastic Beanstalk deployment types (e.g., rolling, immutable).

7. **Infrastructure as Code**
   - Create and manage your application setup using Terraform.

8. **Static Analysis**
   - Use SonarCloud or a similar tool for Static Application Security Testing (SAST).
   - Integrate it into your CI/CD pipeline.

9. **Unit Tests**
   - Write unit tests for your application.
   - Visualize test results in GitHub using a plugin like [EnricoMi/publish-unit-test-result-action](https://github.com/EnricoMi/publish-unit-test-result-action).

10. **Razzle Dazzle**
    - Add styling and interactive elements to your web application to make it visually appealing.
    - Use a framework or library (e.g., Bootstrap, Tailwind CSS) to enhance the UI.

---

## Recommendations

- Use tools like ChatGPT or GitHub Copilot to:
  - Understand new concepts.
  - Write deployment scripts.
  - Debug issues more efficiently.
