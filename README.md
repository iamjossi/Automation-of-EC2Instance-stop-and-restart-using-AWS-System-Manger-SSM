# Automation-of-EC2Instance-stop-and-restart-using-AWS-System-Manger-SSM

To demonstrate this project, I used an EC2 instance, IAM, AWS Resources and Tag Editor and AWS System Manager SSM.

In the AWS management console, I created an IAM role for system manager with 'SSMautomationrule' policy attached

I created an EC2 instance with a tag

Navigated to Resources and Tag Editor to create a Resource Group.
I created an AWS Resource Group based on the tag I assigned to the target EC2 instance. 

Navigated to the AWS Systems Manager console to create a maintenace window with Allow all unregistered targets unchecked and to run on a daily schedule in my time zone.

Registered a target based on the resource group I created and resource type to be EC2 instance.

To register task, I selected register automation task. For this project, I will register 2 tasks; Stop and Restart tasks
For Instance Stop, AWS-Stopinstance was selected as automation document. Document version will be latest.
Window target Id checked as it is selecting target group
In input parameter, Instance ID pasted. For multiple instances, I used pseudo parameter {{RESOURCE_ID}}. 
I copied and pasted the ARN of IAM role I created into the automationassumerole
Checked rate control to be 100 percentage in concunrrency and error threshold. 

For Instance Start, AWS-Startinstance was selected as the automation document. Document version will be latest.
Window target Id checked as it is selecting target group
In input parameter, Instance ID pasted. For multiple instances, I can use pseudo parameter {{RESOURCE_ID}}. 
I copied and pasted the ARN of IAM role I created into the automationassumerole
Checked rate control to be 100 percentage in concunrrency and error threshold. 

To test this project, in the maintenance window accordingly(Start/Stop), I edited the cron expression and saved. 
Then I checked my EC2 Instance to see it shutting/restarting.
