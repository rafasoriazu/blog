---
layout: post
title: Elastic IPs from EC2-Classic to EC2-VPC
lang: en
country: ES
description: "Amazon AWS. Elastic IP from EC2-Classic to EC2-VPC"
modified: 2015-05-13
tags: [Amazon AWS, Elastic IP, EC2-classic, EC2-VPC]
image:
  feature: abstract-8.jpg
  credit: 
  creditlink: 
---


### Amazon AWS

There are some amazon instances that can be launched only in an EC2-VPC.
If you want to attach one of your new EC2-VPC instances to an elastic IP that has already been attached to an EC2-classic instance, you will have to move the Elastic IP from EC2-Classic to EC2-VPC.

<img src="{{ site.url }}/images/20160513-Elastic/VPC_logo.png" alt="Amazon AWS, VPC logo">

## Instance Types Available Only in a VPC

There are some instances that are only available in a VPC

* C4
* M4
* T2

[List of instances](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-vpc.html#vpc-only-instance-types)


<img src="{{ site.url }}/images/20160513-Elastic/vpc.png" alt="Available Instances in a VPC">

## Elastic IPs are different for EC2-Classic and EC2-VPC

You can't associate directly an Elastic IP address that you allocated for use with a VPC with an instance in EC2-Classic, and vice-versa. 

[More info...](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html#VPC_EIP_EC2_Differences)


## Moving elastic IPs from EC2-Classic to EC2-VPC

* Only in the same region
* You can’t migrate an Elastic IP initially reserved for EC2-VPC
* The Elastic IP must be detached from any instance
* This migration has to be carried out from the [CLI](https://aws.amazon.com/es/cli)

## move-address-to-vpc command

[move-address-to-vpc](http://docs.aws.amazon.com/cli/latest/reference/ec2/move-address-to-vpc.html)

{% highlight sh %}
aws ec2 move-address-to-vpc --public-ip 54.123.4.56
Output:

{
  "Status": "MoveInProgress"
}

{% endhighlight %}
