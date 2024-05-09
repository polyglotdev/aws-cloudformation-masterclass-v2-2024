# AWS CloudFormation Masterclass v2 2024

[AWS CloudFormation Masterclass v2 2024](https://www.udemy.com/course/aws-cloudformation-master-class)


## Course Objectives

- Learn CloudFormation and master all its concepts
- Go through hands on examples to practice what we learned
- Learn how to use `YAML` to write CloudFormation templates
- Learn how to write infrastructure as code
- Launch several templates
- Advanced topics like Nested Stacks, Cross Stack References, Macros, StackSets, Drift Detection, Change Sets, etc

## Prerequisites

- Basic knowledge of AWS
  - AWS IAM
  - AWS S3
  - AWS EC2, Security Groups, Autoscaling Groups, etc
  - AWS Lambda
  - A few other services
- Basic knowledge of `YAML` or `JSON` is preferred
- Recent macOS/Linux/Windows machine
- Motivation to learn 🧠

## What is CloudFormation?

- CloudFormation is a declarative way of outlining your AWS Infrastructure
- For example, within a CloudFormation template, you say:
  - I want a security group
  - I want two EC2 instances with this configuration
  - I want an S3 bucket
  - I want a Lambda function
- Then CloudFormation creates those for you, in the right order, with the exact configuration that you specify

Here is an example of a CloudFormation template in `YAML`:

```yaml
Resources:
  MyEC2Instance:
    Type: AWS::EC2::Instance
    Properties:
      AvailabilityZone: us-east-1a
      ImageId: ami-0ff8a91507f77f867
      InstanceType: t2.micro
```

Above is a simple example of a CloudFormation template that creates an EC2 instance. Let me explain what you are 👀 at:

1. `Resources`: This is the section where you define the AWS resources you want to create.
2. `MyEC2Instance`: This is the logical name of the resource. You can use this name to reference this resource in other parts of the template.
3. `Type`: This is the type of AWS resource you want to create. In this case, it's an EC2 instance.
4. `Properties`: These are the properties of the resource. In this case, we are specifying the Availability Zone, the AMI ID, and the Instance Type.
5. `AvailabilityZone`, `ImageId`, `InstanceType`: These are the properties of the EC2 instance that we are creating.

## What are the Benefits of CloudFormation?

- **Infrastructure as Code**
  - No resources are manually created, which is excellent for control.
  - The code can be version controlled for example using Git.
  - Changes to the infrastructure are reviewed through code as pull requests/merge requests.
- **Cost**
  - Each resource within the stack is tagged with an identifier so you can easily see how much a stack costs you.
  - You can estimate the costs of your resources using the CloudFormation template.
  - Savings strategy: In Dev, you could automate the deletion of templates at 5 PM and recreate them at 8 AM, safely.
- **Productivity**
  - Ability to destroy and re-create an infrastructure on the fly.
  - Automate generation of Diagram for your templates!
  - Declarative programming (no need to figure out ordering and orchestration).
- **Separation of concern**: create many stacks for many apps, and many layers. Ex:
  - VPC stacks
  - Network stacks
  - App stacks
- **Don't reinvent the wheel**
  - Leverage existing templates on the web!
  - Leverage the documentation.
