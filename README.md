# COMP3010-BOTSv3

## Table of contents
1. [Introduction](#introduction)
2. [Installation and data preparation](#installation-and-data-preparation)
3. [Question 1](#question-1)

## Introduction
In this report i analyse secuirty incidents using the BOTSv3 dataset. The goal of this report is to show how an SOC (Security Operations Centre) can use tools such as splunk to detect, analyse and respond to incidents in an effective and timely manner. These indicents include examples of compromised IAM users, misconfigurations and API activity. The SOC plays a vital role in identifying incidents such as the ones found in the BotsV3 dataset. This report will highlight the following SOC responsibilities and handling methodlogies will be highlighted in this report.
  - **Prevention**: Measures to avoid incidents such as securing aws credentials or configuring proper access control for S3 Buckets.
  - **Detection**: Identifying and alerting of suspicious activity.
  - **Response**: How incidents are investigated and mitigated, such as analysing logs and isolating compromised systems.
  - **Recovery**: Completing steps during the recovery phase, restoring access and stregthening security protocols.

## Installation and data preparation
Initially, Splunk was installed onto a ubuntu virtual machine to analyse the BOTSv3 dataset. Here is the installation process:
  1. Download VMWare and installed a suitible Ububntu ISO
  2. Next, Splunk was installed on Ubuntu, downloading from the official Spunk website
  3. Downloaded the BOTSv3 dataset from the official GitHub repository (https://github.com/splunk/botsv3)
  4. Followed instructions to injest data and installed all relevent and required apps.

## Question 1 
IAM users accessing AWS Services

**Objective:**
The goal of this query is to identify the IAM users who have accessed the AWS services using the AWS CloudTrail logs.

**Method:**
AWS CloudTrail logs were analysed using Splunk queries to identify usernames with AWS API activity.

**Query:**
```spl
index=botsv3 sourcetype=aws:cloudtrail
| stats count by userIdentity.userName
```
<p align="center">
  <img src="screenshots/Question_1_Query_Result.png" width="700" alt="IAM users accessing AWS services">
</p>

**Findings:**
The results show multiple IAM users accessing AWS services, identified by the ```sple userIdentity.userName``` field which records the IAM username associated with each event. Revealing the usernames: **bstoll, btun, splunk_access, web_admin.**

**SOC Relevance**
Identifying IAM user users that access AWS services is a fundimental core for SOCs. This information ensures accountability, aids with anomoly detection and helps to identify potentially compromised or misused user credentials.



