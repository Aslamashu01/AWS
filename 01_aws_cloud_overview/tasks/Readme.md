>## ! DISCLAIMER
>Despite the most of the labs in this course can be done using the AWS free tier, i.e. without any charging, there a couple of tasks that require creation of paid resources.
Resources like NAT Gateway, Route53 zone etc., will cost you some money (but not that much, fortunately). Anyway, before creating any type of resources, please be sure you carefully read and understood the appropriate pricing policy. Every type of resource is AWS has its own pricing page, for example [Route53 pricing](https://aws.amazon.com/route53/pricing/). If you cannot find the pricing policy in official AWS documentation, just google it, for example "NAT gateway pricing".
To avoid extra money expenditures, you can [set up a billing alert](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/monitor_estimated_charges_with_cloudwatch.html) that will notify you immediately after you have reached some threshold in your billing.
And of course, do not forget cleaning up all the unnecessary resources after completing the lab.


# AWS Initial setup.

## Agenda.

   1. [AWS Account creation](#1-aws-account-creation)
   2. [Signing in with Root user](#2-signing-in-with-root-user)
   3. [Enabling a virtual multi-factor authentication (MFA) device](#3-enabling-a-virtual-multi-factor-authentication-mfa-device-console)
   4. [Checking your Limits and navigating AWS console](#4-checking-your-limits-and-navigating-aws-console)
   5. [Creating an IAM user in your AWS account](#5-creating-an-iam-user-in-your-aws-account)
   6. [Set Up the AWS Command Line Interface (AWS CLI)](#6-set-up-the-aws-command-line-interface-aws-cli)
   7. [Creating a Billing Alarm to Monitor Your Estimated AWS Charges](#7-creating-a-billing-alarm-to-monitor-your-estimated-aws-charges)
<br><br>

---
## 1. AWS Account creation.

<br>
Please watch the video how to create AWS Account and follow the instructions in it to create your own if you do not have it.

[![](images/create_aws_account_youtube.png)](https://youtu.be/gA9pl-A9gDM?list=RDCMUC1Yf7IBfhSNFTIyb7v83o_g)

or follow the guide below.

To create AWS Account: 

1.1 Go to https://aws.amazon.com/ and click on “Create an AWS Account”

![](images/create_aws_account_button.png)


1.2 On the next screens please fill all requested information.

1.2.1 On the first step please specify: Email address, password, AWS account name. Please pay attention to password requirements
![](images/sign_up_for_aws.png)

1.2.2 Fill personal contact information:
![](images/sign_up_contact_info.png)

1.2.3 Fill Billing information:
![](images/sign_up_billing_info.png)

1.2.4 Confirm your identity
![](images/sign_up_confirm_identity.png)

1.2.5 Click Send SMS 

1.2.6 Confirm and complete Registration with received code.


>## ! NOTES
>If you've not received an SMS message for several times on this step, сontact  AWS support.
![](images/aws_registration_confirm_identity.png)

1. Follow this link [Sign in](https://console.aws.amazon.com/console/home?nc2=h_ct&src=header-signin) and sign in to "Root", using login and password.

2. Open AWS support center

![](images/aws_support_link.png)


3. Create new case and describe your issue. For "Contact options" choose method "Chat"
![](images/aws_registration_support_case.png)

![](images/aws_registration_support_contact_option.png)



---
## 2. Signing in with Root user.

To sign in to the Console:

2.1 Go to https://aws.amazon.com/ and Sign in to the AWS Console

2.2 Select “Root user” option
![](images/sign_in_root_user.png)

2.3 Pass Security check
![](images/sign_in_pass_security_check.png)

2.4 Signing in is completed

---
## 3. Enabling a virtual multi-factor authentication (MFA) device (console).

Source: [Enable Virtual MFA](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable_virtual.html)

### Enable a virtual MFA device for your AWS account root user (console).
You can use the AWS Management Console to configure and enable a virtual MFA device for your root user. 
To enable MFA devices for the AWS account, you must be signed in to AWS using your root user credentials.


Before you enable MFA for your root user, review your account settings and contact information to make sure that you have access to the email and phone number. 
If your MFA device is lost, stolen, or not working, you can still sign in as the root user by verifying your identity using that email and phone number. 
To learn about signing in using these alternative factors of authentication, 
see [What if an MFA device is lost or stops working?](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_lost-or-broken.html).


**To configure and enable a virtual MFA device for use with your root user (console)**

3.1. Sign in to the AWS Management Console.

3.2. On the right side of the navigation bar, choose your account name, and choose **My Security Credentials**. If necessary, 
choose **Continue to Security Credentials**. Then expand the **Multi-Factor Authentication (MFA)** section on the page.<br>
![](images/sign_in_security_credentials.png)

3.3. Choose **Activate MFA**.

3.4. In the wizard, choose **Virtual MFA device**, and then choose **Continue**.
    IAM generates and displays configuration information for the virtual MFA device, including a QR code graphic. The graphic is a representation of the secret configuration key that is available for manual entry on devices that do not support QR codes.

3.5. Open the virtual MFA app on the device.

##### Virtual MFA Applications.
Applications for your smartphone can be installed from the application store that is specific to your phone type. The following table lists some applications for different smartphone types.

- Android: [Authy](https://play.google.com/store/apps/details?id=com.authy.authy), [Duo Mobile](https://play.google.com/store/apps/details?id=com.duosecurity.duomobile), [LastPass Authenticator](https://play.google.com/store/apps/details?id=com.lastpass.authenticator), [Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator), [Google Authenticator](https://play.google.com/store/apps/details?id=com.google.android.apps.authenticator2)
- IOS:     [Authy](https://apps.apple.com/us/app/authy/id494168017), [Duo Mobile](https://apps.apple.com/us/app/duo-mobile/id422663827), [LastPass Authenticator](https://apps.apple.com/us/app/lastpass-authenticator/id1079110004), [Microsoft Authenticator](https://apps.apple.com/us/app/microsoft-authenticator/id983156458), [Google Authenticator](https://apps.apple.com/us/app/google-authenticator/id388497605)

If the virtual MFA app supports multiple virtual MFA devices or accounts, choose the option to create a new virtual MFA device or account.

3.6. The easiest way to configure the app is to use the app to scan the QR code. If you cannot scan the code, you can type the configuration information manually. The QR code and secret configuration key generated by IAM are tied to your AWS account and cannot be used with a different account. They can, however, be reused to configure a new MFA device for your account in case you lose access to the original MFA device.

- To use the QR code to configure the virtual MFA device, from the wizard, choose **Show QR code**. 
    Then follow the app instructions for scanning the code. For example, you might need to choose the camera icon or choose a command like **Scan account barcode**, and then use the device's camera to scan the QR code. 
- In the Manage MFA Device wizard, choose Show secret key, and then type the secret key into your MFA app.


> **Important!**
> Make a secure backup of the QR code or secret configuration key, or make sure that you enable multiple virtual MFA devices for your account. 
> A virtual MFA device might become unavailable, for example, if you lose the smartphone where the virtual MFA device is hosted). 
> If that happens, you will not be able to sign in to your account and you will have to contact customer service to remove MFA protection for the account.

The device starts generating six-digit numbers.
   
3.7. In the **Manage MFA Device wizard**, in the **MFA Code 1 box**, enter the six-digit number that's currently displayed by the MFA device. 
Wait up to 30 seconds for the device to generate a new number, and then type the new six-digit number into the **MFA Code 2** box.
   
> **Important!**
> Submit your request immediately after generating the codes. If you generate the codes and then wait too long to submit the request, the MFA device successfully associates with the user but the MFA device is out of sync. This happens because time-based one-time passwords (TOTP) expire after a short period of time. 
> If this happens, you can [resync the device](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_sync.html).
   
3.8. Choose **Assign MFA**, and then choose Finish.
   
The device is ready for use with AWS. For information about using MFA with the AWS Management Console, see [Using MFA devices with your IAM sign-in page](https://docs.aws.amazon.com/IAM/latest/UserGuide/console_sign-in-mfa.html)
   
---
## 4. Checking your Limits and navigating AWS console
Please watch the video and follow the same steps. <br><br>
[![](images/check_your_limits_youtube.png)](https://youtu.be/hG18UrncJ74?list=RDCMUC1Yf7IBfhSNFTIyb7v83o_g)


---
## 5. Creating an IAM user in your AWS account.

**Please watch the video and follow the guide:** <br><br>
[![](images/create_iam_user_youtube.png)](https://youtu.be/qYelauL9s5Q?list=RDCMUC1Yf7IBfhSNFTIyb7v83o_g)
<br><br><br>
#### ***Text version (can be slightly different because it's different source)***

Source: [Creating an IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html)

You can create one or more IAM users in your AWS account. You might create an IAM user when someone joins your team, or when you create a new application that needs to make API calls to AWS.

The process of creating a user and enabling that user to perform work tasks consists of the following steps:
- Create the user
- Create credentials for the user
- Give the user permissions to perform the required tasks.
- Enable 2FA

### Creating IAM users (console).

5.1. Login AWS Console and open IAM Service

![](images/create_iam_user.png)

5.2. Select “Users” in left menu and click “Add user” button

![](images/create_iam_user_add_user_button.png)

5.3. Select the type of access this set of users will have. You can select programmatic access, access to the AWS Management Console, or both:

- Select **Programmatic access** if the users require access to the API, AWS CLI, or Tools for Windows PowerShell. This creates an access key for each new user. You can view or download the access keys when you get to the **Final** page.
- Select **AWS Management Console access** if the users require access to the AWS Management Console. This creates a password for each new user.

![](images/create_iam_user_add_user_details.png)

In our case please Access type select both. We assume can be used for both cases. 

For Console password, choose one of the following:

- **Autogenerated password**. Each user gets a randomly generated password that meets the [account password policy](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_passwords_account-policy.html). You can view or download the passwords when you get to the **Final** page.
- **Custom password**. Each user is assigned the password that you type in the box.


5.4. Choose **Next: Permissions**

5.5. On the next screen you have 3 options:

- **Add user to group**. Choose this option if you want to assign the users to one or more groups that already have permissions policies. IAM displays a list of the groups in your account, along with their attached policies. You can select one or more existing groups, or choose Create group to create a new group. For more information, see [Changing permissions for an IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_change-permissions.html).

- **Copy permissions from existing user**. Choose this option to copy all of the group memberships, attached managed policies, embedded inline policies, and any existing [permissions boundaries](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_boundaries.html) from an existing user to the new users. IAM displays a list of the users in your account. Select the one whose permissions most closely match the needs of your new users.

- **Attach existing policies directly**. Choose this option to see a list of the AWS managed and customer managed policies in your account. Select the policies that you want to attach to the new users or choose Create policy to open a new browser tab and create a new policy from scratch. For more information, see step 4 in the procedure [Creating IAM policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create-console.html#access_policies_create-start). 

After you create the policy, close that tab and return to your original tab to add the policy to the new user. As a [best practice](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#use-groups-for-permissions), we recommend that you instead attach your policies to a group and then make users members of the appropriate groups.

As in our case we are aiming to create IAM user with Full administrative access, select **Attach existing policies directly** and choose policy **AdministratorAccess**.

![](images/create_iam_user_set_permissions.png)

**Set permissions boundary** is OPTIONAL parameter , used for Advanced configuration of permissions. We can keep it empty or select **AdministratorAccess** as well.

5.6. Choose **Next: Tags**.

5.7. (Optional) Add metadata to the user by attaching tags as key-value pairs. For more information about using tags in IAM, see [Tagging IAM resources](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_tags.html)

![](images/create_iam_user_add_tags.png)


5.8. Choose **Next: Review** to see all of the choices you made up to this point.<br>

![](images/create_iam_user_review.png)

When you are ready to proceed, choose **Create user**.
 
5.9. To view the users' access keys (access key IDs and secret access keys), choose **Show** next to each password and access key that you want to see. To save the access keys, choose **Download .csv** and then save the file to a safe location.
![](images/create_iam_user_success_confirmation.png)

> **Important**
> This is your only opportunity to view or download the secret access keys, and you must provide this information to your users before they can use the AWS API. Save the user's new access key ID and secret access key in a safe and secure place. **You will not have access to the secret keys again after this step**.


5.10. Congratulations! You have created your first **IAM User**<br>

![](images/create_iam_user_dashboard_with_user.png)

5.11. It’s strongly recommended to enable **MFA** for **IAM user**.

5.12. Open it, click on **Manage** link in front of **Assigned MFA Device**  and follow the same instructions like it’s done for **Root user**<br>
![](images/create_iam_user_enable_mfa_for_iam_user.png)

---
## 6. Set Up the AWS Command Line Interface (AWS CLI).

### 6.1. What is the AWS Command Line Interface?
The AWS Command Line Interface (AWS CLI) is an open source tool that enables you to interact with AWS services using commands in your command-line shell. With minimal configuration, the AWS CLI enables you to start running commands that implement functionality equivalent to that provided by the browser-based AWS Management Console from the command prompt in your terminal program:

- **Linux shells** – Use common shell programs such as [bash](https://www.gnu.org/software/bash/), [zsh](http://www.zsh.org/), and [tcsh](https://www.tcsh.org/) to run commands in Linux or macOS.
- **Windows command line** – On Windows, run commands at the Windows command prompt or in PowerShell.
- **Remotely** – Run commands on Amazon Elastic Compute Cloud (Amazon EC2) instances through a remote terminal program such as PuTTY or SSH, or with AWS Systems Manager.

All IaaS (infrastructure as a service) AWS administration, management, and access functions in the AWS Management Console are available in the AWS API and AWS CLI. New AWS IaaS features and services provide full AWS Management Console functionality through the API and CLI at launch or within 180 days of launch.
The AWS CLI provides direct access to the public APIs of AWS services. You can explore a service's capabilities with the AWS CLI, and develop shell scripts to manage your resources. In addition to the low-level, API-equivalent commands, several AWS services provide customizations for the AWS CLI. Customizations can include higher-level commands that simplify using a service with a complex API.

### 6.2. AWS CLI versions.

The AWS CLI is available in two versions and information in this guide applies to both versions unless stated otherwise.
- **Version 2.x** – The current, generally available release of the AWS CLI that is intended for use in production environments.
- **Version 1.x** – The previous version of the AWS CLI that is available for backwards compatibility.

For more information on the different versions, see [About the AWS CLI versions](https://docs.aws.amazon.com/cli/latest/userguide/welcome-versions.html)

### 6.3. Installation.

Please use [official guide](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) for installation depending on your Operation System:
- [Docker](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-docker.html)
- [Linux](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html)
- [macOS](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-mac.html)
- [Windows](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-windows.html)


**Verify the installation after completion**
      
To verify that the shell can find and run the aws command in your $PATH, use the following commands.

```sh
$ which aws
/usr/local/bin/aws

$ aws --version
aws-cli/2.1.29 Python/3.7.4 Darwin/18.7.0 botocore/2.0.0
```

### 6.4. Basic Configuration.

Source: [AWS CLI Quick Start](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html )
<br>

Quick configuration with  ***aws configure*** <br>

For general use, the aws configure command is the fastest way to set up your AWS CLI installation. 
When you enter this command, the AWS CLI prompts you for four pieces of information:
- [Access key ID](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html#cli-configure-quickstart-creds)
- [Secret access key](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html#cli-configure-quickstart-creds)
- [AWS Region](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html#cli-configure-quickstart-region)
- [Output format](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html#cli-configure-quickstart-format)

***Access key ID*** and ***Secret access key*** were generated automatically during IAM user creation and usually AWS propose to download them in *.csv* format. 
But if they are lost or expired you can easily generate them again in IAM service for the specific user. 

The AWS CLI stores this information in a ***profile*** (a collection of settings) named *default* in the *credentials* file. 
By default, the information in this profile is used when you run an AWS CLI command that doesn't explicitly specify a profile to use. 
For more information on the *credentials* file, see [Configuration and credential file settings](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html)

The following example shows sample values. Replace them with your own values as described in the following sections.

<pre><code>
$ aws configure
AWS Access Key ID [None]: <span style="background: yellow;">AKIAIOSFODNN7EXAMPLE</span>
AWS Secret Access Key [None]: <span style="background: yellow;">wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY</span>
Default region name [None]: <span style="background: yellow;">us-west-2</span>
Default output format [None]: json
</sode></pre>


Where are configuration settings stored?<br>
The AWS CLI stores sensitive credential information that you specify with *aws configure* in a local file named credentials, 
in a folder named *.aws* in your home directory. The less sensitive configuration options that you specify with *aws configure* are stored in a local file named config, also stored in the *.aws* folder in your home directory.

> **Storing credentials in the config file** <br>
> You can keep all of your profile settings in a single file as the AWS CLI can read credentials from the config file. If there are credentials in both files for a profile sharing the same name, the keys in the credentials file take precedence. <br>
> These files are also used by the various language software development kits (SDKs). If you use one of the SDKs in addition to the AWS CLI, confirm if the credentials should be stored in their own file.


Where you find your home directory location varies based on the operating system, but is referred to using the environment variables %UserProfile% in Windows and $HOME or ~ (tilde) in Unix-based systems. 
You can specify a non-default location for the config file by setting the AWS_CONFIG_FILE environment variable to another local path. See [Environment variables to configure the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-envvars.html) for details. <br>

***~/.aws/credentials***
```ini
[default]
aws_access_key_id=AKIAIOSFODNN7EXAMPLE
aws_secret_access_key=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
```

***~/.aws/config***
```ini
[default]
region=us-west-2
output=json
```

For file examples with multiple named profiles, see [Named profiles](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-profiles.html) <br

**Verify the configuration after completion**
```sh
# It should give you a list of buckets if available or empty list if no buckets. No any errors should be returned.>
$ aws s3 ls
```

---
## 7. Creating a Billing Alarm to Monitor Your Estimated AWS Charges.

**Please watch the video and follow the guide:**

[![](images/create_billing_alert_youtube.png)](https://youtu.be/p3i4NSCVTT4?list=RDCMUC1Yf7IBfhSNFTIyb7v83o_g)


#### ***Text version (can be slightly different because it's different source)***

Source: [Monitor estimated charges with CloudWatch](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/monitor_estimated_charges_with_cloudwatch.html)

You can monitor your estimated AWS charges by using Amazon CloudWatch. When you enable the monitoring of estimated charges for your AWS account, the estimated charges are calculated and sent several times daily to CloudWatch as metric data.

Billing metric data is stored in the US East (N. Virginia) Region and represents worldwide charges. This data includes the estimated charges for every service in AWS that you use, in addition to the estimated overall total of your AWS charges.

The alarm triggers when your account billing exceeds the threshold you specify. It triggers only when actual billing exceeds the threshold. It doesn't use projections based on your usage so far in the month.

If you create a billing alarm at a time when your charges have already exceeded the threshold, the alarm goes to the ALARM state immediately.

Tasks:
- [Enabling Billing Alerts](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/monitor_estimated_charges_with_cloudwatch.html#turning_on_billing_metrics)
- [Creating a Billing Alarm](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/monitor_estimated_charges_with_cloudwatch.html#creating_billing_alarm_with_wizard)

### 7.1. Enabling Billing Alerts.
Before you can create an alarm for your estimated charges, you must enable billing alerts, so that you can monitor your estimated AWS charges and create an alarm using billing metric data. After you enable billing alerts, you can't disable data collection, but you can delete any billing alarms that you created.

After you enable billing alerts for the first time, it takes about 15 minutes before you can view billing data and set billing alarms.

7.1.1 Login with root account or as an IAM user that has been given permission to view billing information.

7.1.2 Open the Billing and Cost Management console at https://console.aws.amazon.com/billing

7.1.3 In the navigation pane, choose **Billing Preferences**.

![](images/create_billing_alarm_enabling_billing.png)

7.1.4 Choose **Receive Billing Alerts**.
7.1.5 Choose **Save preferences**.


## 7.2 Creating a Billing Alarm.

To create a billing alarm using the CloudWatch console

7.2.1 Open the CloudWatch console at https://console.aws.amazon.com/cloudwatch/

7.2.2 If necessary, change the Region to US East (N. Virginia). Billing metric data is stored in this Region and represents worldwide charges.

![](images/create_billing_alarm_billing_preferences.png)

7.2.3 In the navigation pane, choose **Alarms, Create Alarm**.

![](images/create_billing_alarm_click_button.png)

7.2.4 Choose **Select metric**. In the **All metrics** tab, choose **Billing, Total Estimated Charge**.

If you don't see **Billing** or the **Total Estimated Charge metric**, you may need to enable billing alerts. 
For more information, see [Enabling Billing Alerts](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/monitor_estimated_charges_with_cloudwatch.html#turning_on_billing_metrics).

7.2.5 Select the check box next to **EstimatedCharges**, and choose **Select metric**.

![](images/create_billing_alarm_specify_metrics.png)

7.2.6 Under **Conditions**, choose **Static**.

7.2.7 For **Whenever EstimatedCharges is**, choose **Greater**.

7.2.8 For **than**, enter the monthly amount (for example, ***200***) that must be exceeded to trigger the alarm.

**Note** The preview graph displays your current charges for the month

![](images/create_billing_alarm_conditions.png)

7.2.9 Choose **Next**.

7.2.10 For **Select an SNS topic**, select an SNS topic to notify when the alarm is in ALARM state, 
or create a new topic to be notified.

To have the alarm send multiple notifications for the same alarm state or for different alarm states, 
choose **Add notification**.

![](images/create_billing_alarm_configure_actions.png)
<br><br><br>

7.2.11 When finished, choose **Next**.

7.2.12 Enter a name and description for the alarm. 
The name must contain only ASCII characters. Then choose **Next**.

![](images/create_billing_alarm_add_name.png)

7.2.13 Under **Preview and create**, 
confirm that the information and conditions are what you want, then choose **Create alarm**.

![](images/create_billing_alarm_cpreview.png)

7.2.14 On Dashboard you will find just created Alarm . It will be in “Pending Confirmation” state.

![](images/create_billing_alarm_pending_confirmation.png)

7.2.15 Go to your email box, you should find email to confirm subscription.

![](images/create_billing_alarm_confirmation_email.png)

7.2.16 After confirmation you will see the following picture (state: ok, no “pending confirmation” in Actions):

![](images/create_billing_alarm_final.png)

7.2.17 **Congratulations!** You’ve completed with you budget alarm creation.

