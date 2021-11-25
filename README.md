Chaos Engineering with AWS Fault Injection Simulator (FIS) 
==========================================================

![Issues](https://img.shields.io/github/issues/adhorn/aws-fis-experiment-templates)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://gitHub.com/adhorn/aws-fis-experiment-templates/graphs/commit-activity)
[![Twitter](https://img.shields.io/twitter/url/https/github.com/adhorn/aws-fis-experiment-templates?style=social)](https://twitter.com/intent/tweet?text=Wow:&url=https%3A%2F%2Fgithub.com%2Fadhorn%2Faws-fis-experiment-templates)

Collection of [FIS Experiment Templates.](https://docs.aws.amazon.com/fis/latest/userguide/experiment-templates.html)
========================================

These templates let you perform fault injection experiments on resources (applications, network, and infrastructure) in the [AWS Cloud](https://aws.amazon.com).


Currently available
-------------------

-   Support for [**Network Access Control List**](https://github.com/adhorn/aws-fis-experiment-templates/tree/main/network-access-control-list) fault injection using custom embedded scripts via SSM Automation
-   Support for [**Network Access Control List**](https://github.com/adhorn/aws-fis-experiment-templates/tree/main/network-access-control-list) fault injection using custom lambda functions via SSM Automation
-   Support for [**Stopping EC2 Instances in a particular AZ**](https://github.com/adhorn/aws-fis-experiment-templates/blob/main/stop-instances/fis-stop-instance-AZ.json)
-   Support for [**Randomly Stopping EC2 Instances**](https://github.com/adhorn/aws-fis-experiment-templates/blob/main/stop-instances/fis-stop-instance-random.json)
-   Support for [**EC2 API Throttling Error**](https://github.com/adhorn/aws-fis-experiment-templates/blob/main/ec2-control-plane/fis-throttle-error.json)
-   Support for [**EC2 API Internal Error**](https://github.com/adhorn/aws-fis-experiment-templates/blob/main/ec2-control-plane/fis-internal-error.json)
-   Support for [**EC2 API Unavailable Error**](https://github.com/adhorn/aws-fis-experiment-templates/blob/main/ec2-control-plane/fis-unavailable-error.json)
-   Support for [**EC2 Spot Interruption**](https://github.com/adhorn/aws-fis-experiment-templates/blob/main/spot-interruption/fis-spot-interruption.json)
-   Support for [**Terminating instances in Auto Scaling Group in particular AZ**](https://github.com/adhorn/aws-fis-experiment-templates/tree/main/auto-scaling-group-faults)



Prerequisites:
--------------

-   [What is AWS Fault Injection Simulator?](https://docs.aws.amazon.com/fis/latest/userguide/what-is.html)
-   [Experiment templates for AWS FIS](https://docs.aws.amazon.com/fis/latest/userguide/experiment-templates.html)
-   [How AWS Fault Injection Simulator works with IAM](https://docs.aws.amazon.com/fis/latest/userguide/security_iam_service-with-iam.html)


Important:
----------

Before using these templates, replace all occurences of **<ACCOUNT_ID>**, **<INSTANCE_ID>**, **<IAM_ROLE>**, **<CLOUDWATCH_ALARM>**, **<IAM_ROLE_SSM>** with your own particular ones.



Upload an FIS experiment template to your AWS Account:
-----------------------------------------------------

``` {.sourceCode .shell}
➜ aws fis create-experiment-template --cli-input-json fileb://fis-template.json --query experimentTemplate.id

"EXTQGczsC6CZPmHa"
```

Start an FIS experiment:
------------------------

``` {.sourceCode .shell}
➜ aws fis start-experiment --experiment-template-id EXTQGczsC6CZPmHa --query experiment.id

"EXPNK1ynt3PRLCf9LN"
```

Stop an FIS experiment:
-----------------------

``` {.sourceCode .shell}
➜ aws fis stop-experiment --id EXPNK1ynt3PRLCf9LN
```


SOME WORDS OF CAUTION BEFORE YOU START USING THESE TEMPLATES:
-------------------------------------------------------------

-   To begin with, DO NOT use these fault injection templates in
    production blindly!!
-   Always review the FIS templates and the actions in them.
-   Make sure your first fault injections are done in a test environment
    and on test instances where no real and paying customer can
    be affected.
-   Test, test, and test more. Remember that chaos engineering is about
    breaking things in a controlled environment and through well-planned
    experiments to build confidence in your application — and you own
    tools — to withstand turbulent conditions.
