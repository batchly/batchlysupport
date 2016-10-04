### Getting started with AWS Elastic Beanstalk using Batchly

**Step 1:** Login to your Batchly Console Application (your-domain.batchly.net) using registered Email Id and Password.

**Step 2:** You will be redirected to Batchly Dashboard. Next, click on the App Store located in the header.

![EB](../img/jmeter1.png)

**Step 3:** You will be redirected to the **App store** which has the apps supported on Batchly. To run Elastic Beanstalk app, click the **Get Started** button.

![EB](../img/beanstalk1.png)

**Step 4:** Now, to run Elastic Beanstalk job, fill all the required given text fields. There are following text fields to be filled:

**Job Name:** You can give any desired name to your job.

**Project:** Select the associated project to run the job. The project is associated with VPC and Region in which the job has to run.

**Elastic Beanstalk Applications:**  Select the AWS Elastic Beanstalk group from the drop down.

**Elastic Beanstalk Environment:** Specify the minimum number of on-demand instances that should run as part of the Elastic Beanstalk environment.

**Min On-demand Instance Count:**  Specify the minimum number of on-demand instances that should run as part of the Elastic Beanstalk environment.

**Max Instance Count:** Specify the maximum number of instances that should run as part of the Elastic Beanstalk environment.

**Desired Count:** Specify the desired number of instances. Auto Scaling ensures that your group has this many instances.

![EB](../img/beanstalk2.png)

**Step 5:** Click on the **Add Job** button once you are done with filling all the details. This action will save your job and is available to see later on the ‘Jobs’ page.

**Step 6:** On successful job addition, you would get a popup where you can either start your job immediately (by clicking ‘Execute the Job’) or schedule your job to run later (by clicking on the button ‘Schedule the Job’).

![EB](../img/popup.png)

**Step 7:** You can monitor the job progress using the Job Run Details page.
