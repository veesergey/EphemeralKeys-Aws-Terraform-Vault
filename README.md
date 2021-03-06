# EphemeralKeys-Aws-Terraform-Vault

## Table of contents
* [General info](#general-info)
* [Technologies](#technologies)
* [Setup](#setup)
* [Contact](#contact)

## General info
The purpose of this repo is to serve as an example of how easy it is to use Hashicorps tools to great effect. Using just a small amount of code you can store your long lived keys from AWS (such as an admin keypair) in Hashicorp Vault securely, and then use that keypair to generate keys with a predefined role and time to live. Terraform will use the ephemeral keys to actually deploy the infrastructure (in this case an EC2 instance) and then the keypair will automatically be revoked. This fulfills the moving target concept,
so even in if those ephemeral keys are somehow comprimised, they have already been revoked and can no longer be used to modify your infrastructure.

## Technologies
* AWS
* Hashicorp Terraform
* Hashicorp Vault

## Setup
In order for this to run, you do have to have terraform and vault installed. If you have used the AWS console before, terraform will automatically use your AWS keys that are stored on your pc. However the goal here is to store those keys securely in Vault, and then use those stored keys to generate the ephemeral keypair on demand. In this use case, Vault is run locally on your machine and the keys are saved in that local version of vault. 

## What This Code Does
First in the code we define the provider vault. This is the secrets management tool that we use to store our long lived keys in. We define a secret engine and a role called EC2 Creator, and allow it to create and destroy EC2 instances. This is the template used for the temporary iam that is created and then revoked using those long lived keys. We then define the secret engine and the role we want to use, along with the type of EC2 instance we want created and the security groups we use with that EC2 instance. All of this can be changed as needed.

## Contact
Created by me! Veesergey. Feel free to contact me through my github or my [linkedIn!](http://www.linkedin.com/in/veesergey)
