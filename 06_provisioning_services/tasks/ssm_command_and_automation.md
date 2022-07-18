## Domain: AWS Provisioning Services

### Topic: SSM Run Command and Automation

### Task 1: Create Systems Manager IAM role

### Implementation Details 

1. Go to **Identity Access Management (IAM)** and click on **Roles**.
2. Click on **Create Role** , and choose the service that will use this role, it should be **EC2**. Click **Next**.
3. Attach a predefined policy **AmazonEC2RoleforSSM** directly to this role and click on **Next**.
4. Create Tag **Name** = **MySystemsManagerRole** and click on **Next**.
5. Give a name to the role, e.g. **MySystemsManagerRole** and click on **Create Role**.

### Task 2 – Create EC2 instance(s) with SSM IAM role

### Implementation Details 

1. Go to **EC2** console and click on **Launch Instance**.
2. Step 1: Choose an Amazon Machine Image (AMI)
    Select the **Amazon Linux 2 AMI**.
3. Step 2: Choose an Instance Type
    Select the **t2.micro** and click on **Next:Configure Instance Details**.
4. Step 3: Configure Instance Details
    Change **IAM role** only and select **MySystemsManagerRole (_created in Task 1_)** in the list. 
    Click **Next: Add Storag**.
1. Step 4: Add Storage
    Click on **Next: Add Tags** without changes.
6. Step 5: Add Tags
    Add **Tags: Name = MyTest1**, **Application** = **TestApp**. It will be used for identifying our system in Systems Manager. 
    Click **Next: Configure Security Group**.
7. Step 6: Configure Security Group
    Click **Review and Launch**.
1. Step 7: Review Instance Launch
    Click **Launch**.
8. In pop-up windown select **Proceed without a key pair** as we don&#39;t plan to log in to the instance by SSH, check _**"I acknowledge that without a key pair, I can ..."**_ and click on **Launch Instances**
9. You are redirected to **Launch Status** page. To see actual status of instances click **View Instances**.
10. If you want to create additional instances just repeat 5-11 steps and change Tag **Name = MyTest2** , **Name=MyTest3** and etc.

### Task 3 – Systems Manager Run Command

### Implementation Details 

1. Open **Systems manager** and click on **Run Command** in **Node Management** section
2. Click on **Run Command** in the right panel
3. In the Search field insert **AWS-RunShell** and press **Enter** key
4. Select **AWS-RunShellScript** and this allows you to either specify a shell script or you can just type the command that you want to run.
5. Let&#39;s type `ifconfig -a` in **Command parameter** section
6. And in the **Targets** section select **Choose Instances manually**
7. In the **Instances Search** field apply a filter **Ping status** = **Online**
8. Select your instances and click on **Run**
9. Click on **Refresh** to see the status and it should be successful.
    Let&#39;s take a look at the output of that command click on one of the instances and click on **Output**. There is the output of the `ifconfig -a` command that we&#39;ve just run.

### Task 4 – Systems Manager Automation

### Implementation Details 

1. Open **Systems manager** and click on **Automation** in **Change management** section
2. Click on **Execute Automation** in the right panel
3. In the **Search** field insert **AWS-StopEC2Instance** and press **Enter** key
4. Select **AWS-StopEC2Instance** automation document and click on **Next**
5. Select **Simple execution** _(selected by default)_. In the **Input parameters** section Enable **Show Interactive Instances Picker** _(enabled by default)_.
6. Select instances that you created in the **Task 2** and click on **Execute**.
7. If task is successful that will stop those EC2 instances automatically. It can sometimes take a few minutes to complete executing. But if it has been successful, you should see the green tick and success.
8. Check it by going to **Services -> EC2** management console.
9. Click on **Instances** and you should see that the instance or instances that you chose have stopped.

### Benefits / Outcomes / Pros and Cons / Summary 

Now you know how to create run commands with EC2 instance and use Automation with AWS SSM.

### Pricing 

Free

### Tearing down 

1. Terminate EC2 instance
2. Delete Role

