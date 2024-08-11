![image](https://github.com/user-attachments/assets/fbaa9a61-5f8a-4b34-8546-504b61b6b099)# Introduction to CI/CD for ML

## Table of Contents

- [Chapter 1: Introduction to Continuous Integration/Continuous Delivery and YAML](#chapter-1-introduction-to-continuous-integrationcontinuous-delivery-and-yaml)
  - [Introduction to Continuous Integration/Continuous Delivery for ML](#introduction-to-continuous-integrationcontinuous-delivery-for-ml)
  - [Introduction to YAML](#introduction-to-yaml)
  - [Introduction to GitHub Actions](#introduction-to-github-actions)

- [Chapter 2: GitHub Actions](#chapter-2-github-actions)
  - [Intermediate YAML](#intermediate-yaml)
  - [Setting a Basic CI Pipeline](#setting-a-basic-ci-pipeline)
  - [Running Repository Code](#running-repository-code)
  - [Environment Variables and Secrets](#environment-variables-and-secrets)

- [Chapter 3: Continuous Integration in ML](#chapter-3-continuous-integration-in-ml)
  - [Model Training with GitHub Actions](#model-training-with-github-actions)
  - [Versioning Datasets with Data Version Control](#versioning-datasets-with-data-version-control)
  - [Interacting with DVC Remotes](#interacting-with-dvc-remotes)
  - [DVC Pipelines](#dvc-pipelines)

- [Chapter 4: Comparing Training Runs and Hyperparameter (HP) Tuning](#chapter-4-comparing-training-runs-and-hyperparameter-hp-tuning)
  - [Comparing Metrics and Plots in DVC](#comparing-metrics-and-plots-in-dvc)
  - [Hyperparameter Tuning with DVC](#hyperparameter-tuning-with-dvc)
  - [GitHub Actions Workflow for Hyperparameter Tuning](#github-actions-workflow-for-hyperparameter-tuning)

---

## Chapter 1: Introduction to Continuous Integration/Continuous Delivery and YAML

### Introduction to Continuous Integration/Continuous Delivery for ML
Continuous Integration (CI) and Continuous Delivery (CD) are practices designed to automate the software development lifecycle. For Machine Learning (ML), these practices involve automating the process of integrating code changes, running tests, and deploying models. CI/CD helps ensure that ML models are consistently tested and deployed, reducing manual effort and improving reliability. CI/CD for ML also includes steps like automated model training, validation, and deployment, facilitating more efficient development and collaboration.<br><br>

1. **SLDC Overview**<br><br>
The Software Development Life Cycle (SDLC) is a systematic approach and process that encompasses all the stages involved in the development, deployment, and maintenance of software applications. Workflow in SDLC refers to the sequence of steps and activities that are followed to complete a specific task or achieve a particular goal. Examples of these steps include building, testing, and deploying code. "Build" involves transforming source code into an executable form. "Test" encompasses activities to validate the software's functionality and quality. "Deploy" involves making the software available for use in a specific environment.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/e8c517e9-59b2-434c-9f9d-41db63d8cc0c" width="700"></p>


2. **SLDC in machine learning**<br><br>
Developing machine learning (ML) applications is a complex task that requires addressing unique challenges alongside conventional software expectations. Unlike fixed algorithms, ML models continuously learn and adapt to new data. Data engineering plays a crucial role in ML projects, consuming a significant portion of the development budget and necessitating skilled engineers for tasks such as data collection, extraction, transformation, storage, and serving. However, integrating ML with the software development life cycle (SDLC) and adopting automation, such as Continuous Integration/Continuous Delivery, streamlines the process, enabling faster delivery of high-quality ML software. Continuous Integration/Continuous Delivery also facilitates efficient iteration and exploration of algorithms, hyperparameters, and data configurations. It allows for rapid prototyping and testing, leading to quicker insights and informed decision-making.<br><br>

[Link](https://cloud.google.com/blog/products/ai-machine-learning/making-the-machine-the-machine-learning-lifecycle)

<p align="center"><img src="https://github.com/user-attachments/assets/d56d2757-60cd-4863-bc99-ef332ba1a52c" width="700"></p>



3. **What is CI/CD?**<br><br>
Continuous Integration is a software development practice that involves automatically building and testing code changes as they are integrated into a shared repository, ensuring the code remains functional and free of integration issues throughout the development process. The acronym CD can mean either Continuous Delivery or Continuous Deployment depending upon the context. Continuous Delivery is a software development approach that aims to automate the entire process of delivering software changes to production or a production-like environment. Continuous Deployment takes the principles of Continuous Delivery a step further by automating the entire release process with automated deployments.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/463ced25-5361-44d9-a5d3-4f8cd9daed61" width="700"></p>



4. **CI/CD in machine learning**<br><br>
Machine Learning (ML) application workflows differ from conventional software development in a few key aspects. First, a model should be interpreted as a combination of certain algorithms and data, so it is important to version and manage datasets used in model training in addition to the models and the code. Second, experimentation with different model architectures and hyperparameters requires extensive bookkeeping of model performance that can benefit from automation. Next, there are challenges around versioning models, data, and code to ensure reproducibility, experiment tracking, and deployment rollbacks. Traditional software testing often focuses on functional and unit testing, while ML systems require additional testing techniques. CI for ML should involve testing the entire ML pipeline, including data preprocessing, model training, and evaluation, to ensure the quality and reliability of the system. Deploying ML models is often more complex compared to deploying traditional software. CI for ML requires careful consideration of model serving infrastructure, monitoring model performance in production, and managing model updates in real-world scenarios.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/0a90635d-39d0-4491-bc71-9e7763d52c49" width="700"></p>


5. **Scope of this course**<br><br>
In this course, we will focus on data preparation and versioning, model development and evaluation, and hyperparameter tuning steps using CI/CD.**<br><br>
<p align="center"><img src="https://github.com/user-attachments/assets/02596778-6ea1-4a31-8fb2-4383e04267df" width="700"></p>



6. **Summary**<br><br>
The Software Development Life Cycle workflow encompasses building, testing, and deploying code. Continuous Integration (CI) facilitates frequent code merging and early issue detection. Continuous Delivery (CD) enables manual approval for code changes before deployment. Continuous Deployment (CD) automates code deployment without manual intervention. In Machine Learning, CI/CD brings additional benefits like data and model versioning, model building, automation of experiments, comprehensive testing, and efficient deployment. Data and model versioning ensure reproducibility. Automation streamlines iterative experimentation. Testing encompasses the entire ML pipeline, and deployment is made more efficient, rapid, and reliable.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/b3d9a5d0-6e0d-485d-b73d-71a2a8c346ae" width="700"></p>




### Introduction to YAML
YAML (YAML Ain't Markup Language) is a human-readable data serialization format often used for configuration files. In the context of CI/CD, YAML is commonly used to define workflows and pipelines. Its simplicity and readability make it a popular choice for configuring automation tools and pipelines, such as those used in GitHub Actions. YAML files typically include key-value pairs, lists, and nested structures, allowing for clear and organized configuration.<br><br>

1. **What is YAML?**<br><br>
YAML, which stands for "YAML Ain't Markup Language," is a widely used language for organizing data in a readable format. It is employed for configuration files, data exchange, and structured data representation in different applications. It serves as an alternative to languages like XML and is comparable to JSON in terms of functionality. YAML aims to provide a standard format for transferring data between different programming languages or applications, facilitating interoperability and seamless communication. One of YAML's key strengths lies in its simplicity and clean syntax. The format is designed to be easily readable by humans, making it straightforward to write and comprehend. YAML files typically use the file extensions dot yaml or dot yml. YAML finds extensive usage in writing configurations for various CI/CD tools. For instance, popular tools like GitHub Actions and Data Version Control, which we will cover later in the course, rely on YAML configuration files to define workflows, specify tasks, and orchestrate the build, test, and deployment processes.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/aa98fa97-b3c6-4c37-867f-0dc87f869f3b" width="700"></p>


2. **YAML Syntax**<br><br>
In YAML, there is an emphasis on indentation and line separation to denote levels and structure in data. The indentation system is quite similar to the one Python uses. However, tabs are not allowed in YAML, so we have to use spaces for indentation. Incorrect or inconsistent indentation in YAML can lead to syntax errors, misinterpretation of the document's structure, or unexpected behavior during parsing. For this reason, it is a good practice to use YAML validation tools that most modern IDEs are equipped with. Finally, the text after the pound or the hash symbol is treated as a comment in YAML.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/14b86331-48a1-45c3-b3ae-22a14c4ba117" width="700"></p>


3. **YAML Scalars**<br><br>
YAML supports a range of data types for representing different values. These types include scalars representing fundamental values like strings, numbers, booleans, and null. Numbers can be represented as integers or floating points. Like in other programming languages, Boolean values in YAML have two possible states: true or false. In YAML, true and false are keywords and should not be enclosed in quotation marks to be interpreted as booleans. Similarly, null values in YAML are represented by the keyword null or the tilde character. In YAML, strings, in some cases, can be left unquoted, but you can also wrap them in single or double quotes. There are other important styles for writing strings, which we will cover in the next chapter.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/84dfcaea-8ade-49b3-a680-0a06a5aa8f90" width="700"></p>


4. **YAML Collections**<br><br>
Collections are another data type that include both sequences and mappings, making it easier to organize ordered data and key-value pairs in a structured manner. Sequences, also known as lists, arrays, or vectors, allow for an ordered collection of elements. They can be written in block style using hyphens or in flow style using square brackets. The examples demonstrate the block and flow styles of representing a sequence with three elements. Mappings, also known as dictionaries, key-value pairs, hashes, or objects, consist of unique keys and corresponding values that are separated by a colon. The examples display string keys mapped to different data types like string, a nested block list, and a compact flow list consisting of heterogeneous data.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/4841caef-1c02-47ea-9ee0-56592afb62c4" width="700"></p>


5. **Summary**<br><br>
YAML is a data formatting language commonly used for writing CI/CD configurations for Machine Learning applications. Indentation is vital in maintaining the structure, though tabs are prohibited. YAML consists of mappings, sequences, and scalars serving as the foundational elements. Understanding these concepts enables organized and readable YAML files.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/e4190359-2b23-4a51-aaf5-692cfcf18cbe" width="700"></p>



<p align="center"><img src="https://github.com/user-attachments/assets/ca048220-70e7-46a2-be53-9e9529683679" width="700"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/5c886fed-2370-41ed-b90a-b72e52f6b9fc" width="700"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/ccdae361-fc7c-4708-a3a6-47951e11af0c" width="700"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/8bf9b4d5-730c-4b18-8991-d558f0868db1" width="700"></p>




### Introduction to GitHub Actions
GitHub Actions is a CI/CD tool integrated with GitHub that allows you to automate workflows directly within your GitHub repository. With GitHub Actions, you can create custom workflows for building, testing, and deploying your code. Workflows are defined in YAML files and can be triggered by various GitHub events such as push, pull request, or on a schedule. GitHub Actions provides a flexible and powerful way to implement CI/CD pipelines, enabling automation for tasks such as model training and deployment.<br><br>

1. **What is GitHub Actions?**<br><br>
GitHub Actions, abbreviated as GHA, is a built-in automation and CI/CD system provided by GitHub that allows us to automate your build, test, and deployment pipeline directly within our GitHub repositories. Pipeline refers to a sequence of interconnected steps or stages that represent the flow of work and data in a software development or deployment process [1]. Developers create automated steps for tasks like code building, testing, and deployment in GitHub Actions. These actions follow an order, mirroring an assembly line, for smooth software development progress [2].<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/a9464f4f-a9c1-482f-a6a1-a27d2f23916e" width="700"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/92d54e05-5e27-4ac4-926e-bfc85dc0f15f" width="700"></p>


2. **GHA Components: Event**<br><br>
Now, we'll look at the different components of GitHub Actions. An event is a particular action within a repository that initiates the execution of a workflow. These actions can originate from GitHub when someone opens a pull request, creates an issue, or pushes a commit to the repository.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/e4aedbe1-addc-4d63-9753-63759067a551" width="700"></p>


3. **GHA Components: Workflow**<br><br>
A workflow is a customizable automated process that executes one or multiple jobs. These workflows are specified in a YAML file stored in your repository and can be triggered by events within the repository, manually initiated, or scheduled to run at specific intervals. In a repository, workflows are specified within the dot github slash workflows directory. Multiple workflows can exist, each performing a distinct set of tasks. For instance, one workflow can be dedicated to building and testing pull requests, another to deploy the application upon each release, and yet another to add labels when new issues are opened.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/083e2654-b0c9-43b0-8709-24a604b4aa7d" width="700"></p>



4. **GHA Components: Steps and Actions**<br><br>
Steps in the GitHub Actions Platform are individual units of work, executed in order and dependent on the previous step. Each step is executed on the same compute machine, and we can share data from one step to another. For example, we can have a step that builds our application followed by a step that tests the application that was built. Examples of work that can be performed in steps are running applications like compiled code and shell scripts. We can also combine complex but frequently repeated tasks specific to the GitHub Actions platform in a custom application called Action. Examples of actions could be checking out a repository, automatically commenting on a pull request, etc.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/cb60a4fe-b21c-4275-b7bb-657106f75040" width="700"></p>


5. **GHA Components: Jobs and Runners**<br><br>
A job is a set of steps in a workflow. Unlike steps, each job is independent of other jobs - so we can run multiple jobs in parallel. It is possible, however, to configure a job dependent on another job. All the steps in a single job are executed on the same compute machine called runners.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/f9a783ef-7f2d-4b68-8fe6-a516bfa18e7e" width="700"></p>


6. **A simple GHA workflow**<br><br>
For example, a push event in a repository can trigger a workflow where a single job runs on an Ubuntu Linux runner machine. The job contains two steps that are run in order. Checking out the repository, which is an Action. Running the Python code, which is a simple python application.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/fdf3d697-5b52-4533-959f-f33c181b48d8" width="700"></p>


7. **Putting it all together**<br><br>
This graph provides an overview of how the different components, jobs, and steps are interconnected in a GitHub Actions workflow. A GitHub repository houses a workflow file in the dot github slash workflows directory. This file defines the workflow that gets triggered by events such as push or pull requests. The workflow can run multiple jobs in parallel that are constituted by steps. Steps can be shell scripts, programs, or actions that run on the same runner machine. They can optionally produce an artifact as an output.<br><br>

<p align="center"><img src="https://github.com/user-attachments/assets/28e84d72-9561-45e6-8926-38335eda4ebf" width="700"></p>


### Exercises
<p align="center"><img src="https://github.com/user-attachments/assets/11bd5eb7-08f3-4201-9955-3e0f2022de0b" width="700"></p>
<p align="center"><img src="https://github.com/user-attachments/assets/93bb660c-97bc-4113-bac0-3fd0bdf74ee9" width="700"></p>




## Chapter 2: GitHub Actions

### Intermediate YAML
Intermediate YAML involves using more advanced features of YAML for configuring GitHub Actions workflows. This includes defining jobs, steps, and workflows, using conditionals and matrix builds, and managing dependencies between jobs. Understanding these features allows for more complex and efficient CI/CD pipelines, enabling automation of intricate workflows and customization of actions based on various criteria.



### Setting a Basic CI Pipeline
A basic CI pipeline in GitHub Actions involves creating a workflow file that defines the steps for building and testing code. This typically includes setting up the environment, installing dependencies, running tests, and reporting results. A basic CI pipeline helps ensure that code changes are automatically validated and verified before being merged into the main branch, providing immediate feedback to developers.

### Running Repository Code
Running repository code involves executing scripts or commands as part of a GitHub Actions workflow. This can include running unit tests, linting code, or building artifacts. By configuring the workflow file to include these tasks, you can automate the process of running repository code and ensure that it meets the specified quality standards. This step is crucial for maintaining code quality and detecting issues early in the development process.

### Environment Variables and Secrets
Environment variables and secrets in GitHub Actions are used to store sensitive information and configuration settings securely. Environment variables are used to pass data between jobs and steps, while secrets are used to store sensitive information such as API keys and credentials. Proper management of environment variables and secrets is essential for maintaining the security and integrity of your CI/CD pipeline.

## Chapter 3: Continuous Integration in ML

### Model Training with GitHub Actions
Model training with GitHub Actions involves automating the process of training machine learning models as part of your CI/CD pipeline. This includes defining steps to set up the training environment, execute training scripts, and evaluate model performance. By integrating model training into your CI pipeline, you can ensure that your models are consistently updated and validated with each code change.

### Versioning Datasets with Data Version Control
Data Version Control (DVC) is a tool for managing and versioning datasets used in machine learning projects. DVC helps track changes to datasets, ensuring that different versions of data can be reproduced and shared. Integrating DVC with GitHub Actions allows you to automate dataset versioning and ensure that the correct data versions are used during model training and evaluation.

### Interacting with DVC Remotes
DVC remotes are storage locations where datasets and models are stored. Interacting with DVC remotes involves configuring and managing these storage locations to ensure that data is accessible and properly versioned. This includes tasks such as pushing and pulling data from remotes, configuring remote storage settings, and ensuring that the correct versions of data are used in your CI/CD pipeline.

### DVC Pipelines
DVC pipelines allow you to define and manage the sequence of steps required for your machine learning workflow. This includes data preprocessing, model training, and evaluation. By defining DVC pipelines, you can automate the execution of these steps and ensure that your ML workflows are reproducible and consistent. DVC pipelines integrate with GitHub Actions to provide a seamless CI/CD experience for machine learning projects.

## Chapter 4: Comparing Training Runs and Hyperparameter (HP) Tuning

### Comparing Metrics and Plots in DVC
Comparing metrics and plots in DVC involves analyzing the performance of different model runs to determine the best configuration. DVC provides tools for tracking and visualizing metrics such as accuracy, precision, and recall, as well as plotting results to compare different runs. This helps in evaluating model performance and selecting the best model based on empirical evidence.

### Hyperparameter Tuning with DVC
Hyperparameter tuning with DVC involves optimizing the parameters of your machine learning model to improve its performance. DVC supports hyperparameter tuning by allowing you to define and manage different hyperparameter configurations and track their impact on model performance. Integrating hyperparameter tuning with GitHub Actions helps automate the tuning process and ensures that the best hyperparameters are used in your models.

### GitHub Actions Workflow for Hyperparameter Tuning
A GitHub Actions workflow for hyperparameter tuning involves defining a pipeline that automates the process of experimenting with different hyperparameter settings. This includes running training jobs with various hyperparameter configurations, evaluating model performance, and selecting the best configuration. By automating hyperparameter tuning with GitHub Actions, you can efficiently explore and optimize model parameters as part of your CI/CD pipeline.
