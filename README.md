# aws_ec2_unused_resources
Simple python script that finds unused EC2 resources and sends email via SES

Resources checked:
- Disassociated Elastic Ip Addresses (Costs)

- Unattached Volumes (Costs)

- Unused snapshots (Snapshots that are not associated with AMI, Costs)

- Security Groups (SGs that are not associated with any EC2, Doesn’t cost)

- Elastic Load Balancers (ELBs with no instances, Costs)

- Launch Configurations (LCs that are not associated with a ASG, Doesn’t cost)

- Auto Scaling Groups (ASGs that Desired Capacity set to 0, Doesn’t cost)

Of course script can be changed according to your environment, for instance you can use ASG to use later.

To configure script, you need your account-id (owner-id parameter is used to find the snapshots that you own). You can also limit the region_list according to your demand. You should also verify your email address to get email. To fetch data from AWS and send email, you need an IAM user with the permissions below. When the script runs, it fetches all the resources and find the unused ones, then create the report.html file and sends it via SES.

Reference link: http://www.wekanban.com/amazon-web-services-unused-ec2-resources-checker/
