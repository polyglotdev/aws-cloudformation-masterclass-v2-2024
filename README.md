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

## What this course won't do?

- This course won't go over every AWS service because AWS offers around 42.240 products and services.
- Instead we'll go over understanding how to write CF templates in the perfect way
- Then you can apply the same concepts to any AWS service you want

## How does CloudFormation work?

When creating a stack, AWS CloudFormation makes underlying service calls to AWS to provision and configure your resources. CloudFormation can only perform actions that you have permission to do. For example, to create EC2 instances by using CloudFormation, you need permissions to create instances. You'll need similar permissions to terminate instances when you delete stacks with instances. You use AWS Identity and Access Management (IAM) to manage permissions.

The calls that CloudFormation makes are all declared by your template. For example, suppose you have a template that describes an EC2 instance with a t2.micro instance type. When you use that template to create a stack, CloudFormation calls the Amazon EC2 create instance API and specifies the instance type as t2.micro. The following diagram summarizes the CloudFormation workflow for creating stacks.

![cf workflow](image.png)

## Couple of things to keep in mind

1. Key Value Pairs are always capitalized in CloudFormation
2. Any course, and I mean any course that has anything to do with GCP, Azure, or AWS, if the course didn't come out the moment that every single feature you are using in the course did, it's likely that you will have to depend on the documentation, like every good engineer should. Content creators have impossible task of keeping up with the pace of cloud providers. So, if you are following along with this course, and you see that something has changed, please refer to the official documentation. I will do my best to keep the notes up to date, but I can't guarantee that I will be able to do so. DOCS DOCS DOCS!
3. Keep in mind if you are in the CloudFormation UI the events tab shows things in chronological order. So if you are sitting there depending on that to get you by, you will end up mad.

![cf events](./images/cf-ui.png)

## What is  `yaml`

YAML is a human-readable data serialization standard that can be used in conjunction with all programming languages and is often used to write configuration files.

Here is an example of a `YAML` file:

```yaml
Resources:
  MyEC2Instance:
    Type: AWS::EC2::Instance
    Properties:
      AvailabilityZone: us-east-1a
      ImageId: ami-0ff8a91507f77f867
      InstanceType: t2.micro
```

In the above example, we are creating an EC2 instance using `YAML`.

## What is `JSON`

JSON (JavaScript Object Notation) is a lightweight data-interchange format. It is easy for humans to read and write. It is easy for machines to parse and generate.

Here is an example of a `JSON` file:

```json
{
  "Resources": {
    "MyEC2Instance": {
      "Type": "AWS::EC2::Instance",
      "Properties": {
        "AvailabilityZone": "us-east-1a",
        "ImageId": "ami-0ff8a91507f77f867",
        "InstanceType": "t2.micro"
      }
    }

  }
}
```

In the above example, we are creating an EC2 instance using `JSON`.

So yaml has:

- Key Value Pairs
- Nested Objects
- Support Arrays
