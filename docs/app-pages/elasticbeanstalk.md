### Getting started with AWS Elastic Beanstalk using Batchly

**Step 1:** Login to your Batchly Console Application (your-domain.batchly.net) using registered Email Id and Password.

**Step 2:** You will be redirected to Batchly Dashboard. Next, click on the App Store located in the header.

![EB](../img/jmeter1.png)

**Step 3:** You will be redirected to the **App store** which has the apps supported on Batchly. To run Elastic Beanstalk app, click the **Get Started** button.

![EB](../img/beanstalk1.png)

**Step 4:** Now, to run Elastic Beanstalk job, fill all the required given text fields. There are following text fields to be filled:

**Job Name:** You can give any desired name to your job.

**Account:** Select your AWS Account where you want to run the job.

**Cloud Region:**  The Cloud region will be selected automatically. 

**VPC Information:** If the Account has VPC associated with it, then it will get selected automatically.You can also select the desired VPC.

**Subnet Information:** If the Account has VPC associated with it, then it will get selected automatically.You can also select the desired number of subnet out of all. 
*Note:* By-default, all the subnet will be taken.

**Elastic Beanstalk Applications:**  Select the AWS Elastic Beanstalk group from the drop down.

**Elastic Beanstalk Environment:** Specify the minimum number of on-demand instances that should run as part of the Elastic Beanstalk environment.

**Min On-demand Instance Count:**  Specify the minimum number of on-demand instances that should run as part of the Auto Scaling group.

**Max Instance Count:** Specify the maximum number of instances that should run as part of the Auto Scaling group.

**Desired Count:** Specify the desired number of instances. Auto Scaling ensures that your group has this many instances.

![EB](../img/beanstalk2.png)

**Step 5:** Click on the **Add Job** button once you are done with filling all the details. This action will save your job and is available to see later on the ‘Jobs’ page.

**Step 6:** On successful job addition, you would get a popup from where you can start your job immediately (by clicking ‘Execute the Job’).

![EB](../img/popup.png)

**Step 7:** You can monitor the job progress using the Job Run Details page.
