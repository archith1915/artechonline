---
{"dg-publish":true,"permalink":"/content-folders/devops/jenkins-basics/","title":"Jenkins basics","tags":["devops","jenkins"]}
---

# Jenkins

Jenkins is an open-source automation server that helps automate the building, testing and deployment of software projects. It allows developers to integrate changes to the project continuously, making it easier to detect and fix errors early in the development process.


###### Where to use jenkins

1. Continuous integration and delivery of web applications.
2. Automated testing and deployment of mobile apps.
3. Building and deploying containerized applications with Docker and Kubernetes.
4. Integrating with version control systems like Git for automatic build triggering.
5. Automating infrastructure provisioning and configuration management.


**Pipelines**

In jenkins, a pipeline is a set of automated steps that defines the process of building, testing and deploying software. This allows developers to define the entire workflow as code, making version control, sharing and reuse easier.

**CI/CD Pipeline**

The CI/CD pipeline is a process for automating the software delivery process, from code changes to production deployment. It includes continuous integration, where code changes are automatically built and tested, and continuous delivery, where verified changes are automatically deployed to production or staging environments[^1].


**Continuous Integration (CI)**

Continuous integration is a software development process where developers frequently integrate their code changes into a shared repository. Each integration triggers an automated build and testing process, ensuring that changes are compatible with the existing codebase.

**Continuous Delivery (CD)**

Continuous delivery is a software engineering approach where code changes are automatically built, tested and prepared for release into a production environment. This ensures that software can be released reliably and quickly at any time to market and increasing customer satisfaction.

**Continuous Deployment (CD)**

Continuous deployment is the process of automatically deploying code changes to production environments after they have passed through automated tests and quality checks. This allows organizations to quickly and consistently deliver new features and updates to customers, with minimal manual intervention.



# Creating a pipeline

Jenkins provides several ways to create pipelines, allowing users to choose the method that best suits their workflow and needs:

1. **Jenkinsfile:** A text file that defines an entire pipeline using Groovy syntax. It allows users to define the pipeline's steps, stages and configuration in a single file stores in the source code repository. Whenever changes are pushed to the repository, Jenkins automatically detects and executes the pipeline defined in the Jenkinsfile.
2. **Jenkins pipeline script**: In addition to the jenkinsfile, users can create pipelines directly in jenkins pipeline script convenience. This approach allows users to define pipeline steps, stages and configurations directly within the jenkins interface using Groovy syntax. Pipeline scripts are typically stored and executed within jenkins and are suitable for simple or ad-hoc pipelines.
3. **Blue ocean editor:** The jenkins plugin Blue Ocean is a plugin that provides a visual pipeline editor for creating and managing pipelines. The blue ocean editor provides an intuitive interface for designing pipelines, allowing users to drag and drop pipeline steps, add stages, and configure pipeline settings without writing code. This simplifies the creation and visualization of pipeline, making it ideal for users who prefer a graphical approach.
4. **Pipeline libraries:** Jenkins supports it use pipeline libraries to define reusable pipeline components and functions. Users can create custom pipeline libraries containing shared pipeline code, such as common steps, utilities, or custom functions and then import and use these libraries in their Jenkins pipelines. Pipeline libraries promote code reuse, maintainability, and consistency across pipelines.
5. **Integrated development environments (IDE)**: Some developers prefer to use integrated development environments. Use softwares like intellij IDEA or visual studio code to write and manage jenkins pipelines. These IDEs provide features like syntax highlighting, code completion and debugging capabilities, making it easier to write and maintain complex pipeline scripts. Users can install plugins or extensions to integrate jenkins pipeline development directly into their preferred IDE.

	Depending upon the complexity of the pipeline, the development workflow, and user preferences, Jenkins offers a range of options for creating pipelines. Users can choose the method that best suits their needs and leverage the flexibility and extensibility of jenkins to automate their software delivery processes efficiently.


# Pipeline as code

Pipeline as code is an approach to defining and managing jenkins pipelines using code. It allows developers to describe their entire software delivery process as code, stored alongside their application code in version control repositories. This approach provides several benefits, including versioning, code reuse, and easier collaboration.

## Creating a pipeline with script

To create a pipeline in jenkins using script, you can use the pipeline script syntax, which based on the groovy programming language. Here's a step-by-step guide on how to create a basic pipeline:

1. *Navigate to jenkins* - Access the jenkins web interface and navigate to the desired job or create a new one.
2. *Select pipeline* - Select "Pipeline" as the job type when creating a new job or configuring an existing one.
3. *Define pipeline script* - Enter the pipeline script in the "Pipeline Script" section. The script defines the stages, steps, and configurations of the pipeline.
4. *Save and run* - Save your pipeline script and run the job. Jenkins will execute the pipeline according to the defined script.




[^1]: A staging environment is essentially a pre-production environment that closely mimics the production environment.




