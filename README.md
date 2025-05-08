# GenAI Knowledge Center

This repository contains a collection of resources, tools, and examples related to Generative AI (GenAI) and Large Language Models (LLMs). 
The goal is to provide a comprehensive knowledge center for developers, researchers, and enthusiasts interested in exploring the capabilities of GenAI. </br>

Many of the resources are curated as Jupyter Notebooks, which can be easily run in your IDE or in Google Colab.

# Prerequisites
* IntelliJ/VS Code IDE
* Python 3.11 or higher
* AWS account with IAM role that grant access to Bedrock APIs (for AWS Bedrock examples)


## Setup

### Clone the repository

```shell
git clone git@github.com:mistriel/genai-crash-course.git
```

### Install required plugins

Make sure your IntelliJ IDE is set up with the following plugins:
- [Python](https://www.jetbrains.com/help/idea/getting-started-with-python.html)
- [Jupyter](https://www.jetbrains.com/help/idea/jupyter-support.html)

### AWS Access
Make sure you have permissions in your AWS account to `invokeModel`

1.	Open AWS Management Console
2.	Open IAM 
3.	Open Roles
4.  Find the role you are logged in with 
5. Invoke this command on the CLI and make sure "EvalDecision": "allowed"(with my role as example):

```shell
aws iam simulate-principal-policy --action-names bedrock:InvokeModel --resource-arns "*" --policy-source-arn "arn:aws:iam::833463464384:role/AMN_DeveloperRole"
```
