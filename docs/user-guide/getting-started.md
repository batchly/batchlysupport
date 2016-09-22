### Getting Started

To get started with Batchly, go to the [Registration page](https://join.batchly.net) and **create a new Batchly Account**.

To Register for Batchly, enter the following details:

1. Enter your **Full Name**

2. Enter your **Organization Name**

3. Enter your Organization Name or any desired name to set **domain name**

4. Enter your valid **Email Address**

5. Enter your valid **Phone Number**

6. Enter your **Password**

7. Click **Create Account** button.You may be asked to select the Captcha to let us know that you are human.

![Register](../img/register.png)

### First step after signing up - Check your Email

After signing up, you will receive an email on your registered email address for verification. After verification completion, you can successfully sign in to Batchly.

### Sign in Process - Wizard

When you sign up for the very first time from your customized domain (for example : http:// yxz.batchly.net), you will go through the Wizard page. Here you will be asked to follow a few steps in order to set up everything, which you will be required to use on an app later.

**Step 1:** Create an account.

**Step 2:** Create a project.

**Step 3:** Select any app.

![Wizard](../img/wizard.png)

### Add AWS Account

**Important:** 

1. To create an Account, Batchly requires your role *AWS Role ARN*. 

2. In case *AWS Role ARN* already exists then you might not be able to create new *AWS Role ARN*.(You may use the same Role ARN or create a new one)

To use Batchly Apps, Account creation is mandatory. For that, click the **Add AWS Account** and you will be redirected to another page where following details needs to be given to add an account.

**Step 1:** Click on **Launch Stack** to launch the CloudFormation template.
It will redirect you to the AWS website. (Please Log in to your AWS account if you're not logged in. )

![Account](../img/Account.png)

**Step 2:** After login into AWS account, you will be redirected to the CloudFormation page.Click on the **Next** Button in the *Select Template* screen.

![Account](../img/Account1.png)

**Step 3:** Click on the **Next** Button in the *Specify Details* screen. 

![Account](../img/Account2.png)

**Step 4:** Click on the **Next** Button in the *Options* screen.

![Account](../img/Account3.png)

**Step 5:** Select both the checkboxes in the **Review** screen (it would give this CloudFormation template access to create IAM Resources) and Click the **Create** button. A stack gets created.

![Account](../img/Account4.png)

**Step 6:** Once the stack gets created, Go to **Outputs** tab and copy the Role ARN value and paste it in **AWS Role ARN** field in the Batchly's Account screen.

![Account](../img/Account5.png)

**Step 7:** Enter Account Name.

**Step 8:** Select the Region.

![Account](../img/Account6.png)

**Step 9:** Cick on the button **Add Account** button.

**Note:** Before adding an account, the customer needs to have their own AWS account.

### Add Project

**Important:** 

1. Before adding a project, the customer needs to have their own AWS account.
          
2. When you create an account, a default project will be created without VPC. So, creating a project is not mandatory. This can be done later.

The projects section lets you add a project under an AWS account. The following steps will show how to add a new project:

1. Enter Project Name.

2. Select the Account under which you want to add the project.

3. Select the Cloud region.

3. Select the **Virtual Private Cloud**. (This is optional)
**Note:** If you wish to work on **JMeter** app then this VPC will be mandatory.

4. Select the VPC information. (This needs to be done only if you have selected VPC)

5. Select the subnet information. (This needs to be done only if you have selected VPC)

![Project](../img/createproject.png)

### Select App

Once you're done with adding account and project, you can select any app you want to work on.

![Apps](../img/appstore.png)