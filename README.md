# DevOps Test Case

Based on the application source code provided, prepare a scalable solution based on deploying the application to a kubernetes cluster.

## What should be part of the prepared solution?
* CI action building an application using GitHub workflows
  * Use Docker to build the application
  * The application should be versioned semantically
  * Notification of success should be sent to https://webhook.site/cdfb064f-0b1a-4017-b9ce-ba9fa412c8aa using JSON format, example:
    ```json
    {
      "testCase": "success"
    }
    ```
* Build a Kubernetes-based implementation
  *  It is necessary to prepare a web server that can handle the traffic
  *  Application also communicates internally, which means that its design must be able to be accessed via a network based on VPC peering
  *  It also contains 3 super secret environment variables in the form of:
    ```
      SECRET1=ULTRASUPERSECRET_1
      SECRET2=SECONDSECRETDATA!@#$%
      DB_URI=mysql://localhost:3306
    ```
  * From outside, the application can only be connected from an IP address with a number: `1.1.1.1`
  * The assumption is that the system is autoscalable in relation to resources
  * Available system resources: 64 CPU / 256 GB RAM
* Developers need help with the local environment for the application, and therefore need to be prepared:
  *  Local environment based on `docker-compose`
  *  The system locally should only operate using the https protocol
  *  The local environment should also include a database in the form of a mysql server
* For both local and Kubernetes-based environments, there is a need to perform tasks via scripts, tasks include:
  * Applying the changes to the kubernetes cluster
  * Local dockerfile build and image publishing with latest tag
  * Retrieving information about the deployed tag on the kubernetes cluster
  * Forward port 8080 directly from a Kubernetes-based application deployment
  * Complete local environment building
