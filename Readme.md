# AWS Command Line Interface
## AWS - Install and Configure CLI using permanent IAM user access keys
The AWS Command Line Interface (AWS CLI) is a command-line tool that allows you to interact with AWS services using commands in your terminal/command prompt.  


It enables you to run commands to provision, configure, list, delete resources in the AWS cloud. Before you run any of the aws commands, you need to follow three steps:  
Install AWS CLI  
Create an IAM user with Administrator permissions  
Configure the AWS CLI  

## Step 1. Install AWS CLI v2
Verify the installation using the following command in your terminal (macOS)/cmd (Windows).
### Display the folder that contains the symlink to the aws cli tool
`which aws`
### See the current version
`aws --version`

<a href="https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html" target="_blank">Install AWS</a>

**Download the installation file in one of the following ways:**  
`curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"`  

**Unzip the installer**  
`unzip awscliv2.zip`  

**Run the install program**  
`sudo ./aws/install`  
`which aws`  

**Confirm the installation with the following command.**  
`aws --version`  

## Step 2. Create an IAM user
Create an IAM user with Administrator permissions who is allowed to perform any action in your AWS account, only through CLI. After creating such an IAM user, we will use its Access key (long-term credentials) to configure the AWS CLI locally.  

*AWS Identity and Access Management (IAM) service allows you to authorize users / applications (such as AWS CLI) to access AWS resources.*  

The Access key is a combination of an Access Key ID and a Secret Access Key.  

<a href="https://github.com/arabog/IAM-Policy" target="_blank">How to create IAM user</a>

## Step 3. Configure the AWS CLI
You will need to configure the following four items on your local machine before you can interact with any of the AWS services:  
1. Access key - It is a combination of an Access Key ID and a Secret Access Key. Together, they are referred to as Access key. You can generate an Access key from the AWS IAM service, and specify the level of permissions (authorization) with the help of IAM Roles.  
2. Default AWS Region - It specifies the AWS Region where you want to send your requests by default.  
3. Default output format - It specifies how the results are formatted. It can either be a json, yaml, text, or a table.  
4. Profile - A collection of settings is called a profile. The default profile name is default, however, you can create a new profile using the aws configure --profile new_name command.  

**Here are the steps to configure the AWS CLI in your terminal:**  
`aws configure `  

*If you already have a profile set locally, you can use --profile <profile-name> option with any of the AWS commands above. This will resolve the conflict with the existing profiles set up locally.*  

The command above will store the access key in a default file ~/.aws/credentials and store the profile in the ~/.aws/config file. You can verify the saved config using:  
  
View the current configuration  
`aws configure list`  
View all existing profile names  
`aws configure list-profiles`
In case, you want to change the region in a given profile  
`aws configure set <parameter> <value>  --profile <profile-name>`
`aws configure set region us-east-1`  

*Let the system know that your sensitive information is residing in the .aws folder*  
`export AWS_CONFIG_FILE=~/.aws/config`  
`export AWS_SHARED_CREDENTIALS_FILE=~/.aws/credentials`  

## Step 4. Run your first AWS CLI command
Check the successful configuration of the AWS CLI, by running either of the following AWS command:  
If you've just one profile set locally
`aws iam list-users`  
If you've multiple profiles set locally
`aws iam list-users --profile <profile-name>`  

![cli1](cli1.png?raw=true "cli1")



