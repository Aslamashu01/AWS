## Domain: AWS Provisioning Services

### Topic: SSM Parameter Store

### Task 1: Create App parameters in SSM Parameter Store (AWS console)

### Problem to Be Solved 

We should create the following parameters for dev and prod environments of the test app:

- /my-app/dev/db-url
- /my-app/dev/db-password
- /my-app/prod/db-url
- /my-app/prod/db-password 

### Implementation Details 

1. Go to **Systems Manager** console and open **Parameter Store**. You can find it in **Application Management** section at the left panel menu.
2. Click on **Create parameter** in the right panel
3. Fill in **Parameter details**
    - **Name** - /my-app/dev/db-url
    - **Description** – Database URL for my app in Dev
    - **Tier** - Standard
    - **Type** – String
    - **Data type** – text
    - **Value** – dev.database.dreamdb.org:3306

1. Click on **Create Parameter**
2. Now when the parameter has been created click on the parameter name. You can see Overview, History and Tags tabs that contain useful information about the parameter including parameter versions and their values.
3. Get back to **Parameter store**. Just click on the **Parameter Store** hyperlink at the top of the page.
4. Click on **Create parameter** and fill in Parameter details for the second parameter of the Dev environment:

      - **Name** - /my-app/dev/db-password
      - **Description** – Database password for my app in Dev
      - **Tier** - Standard
      - **Type** – SecureString
      - **KMS key source** – My current account
      - **KMS key ID** – alias/aws/ssm
      - **Value** – DevPassword

1. Click on **Create parameter**
2. Create parameters for Prod env:
    - Database URL

        - **Name** - /my-app/prod/db-url
        - **Description** – Database URL for my app in Prod
        - **Tier** - Standard
        - **Type** – String
        - **Data type** – text
        - **Value** – prod.database.dreamdb.org:3306


    - Database password

        - **Name** - /my-app/prod/db-password
        - **Description** – Database password for my app in prod
        - **Tier** - Standard
        - **Type** – SecureString
        - **KMS key source** – My current account
        - **KMS key ID** – alias/aws/ssm
        - **Value** – ProdPassword

    We will use all these parameters in the next tasks

### Task 2: Work with App parameters stored in SSM Parameter Store (AWS CLI)

1. Open **AWS CloudShell** window. You can find the **CloudShell** icon at the top of AWS console and click on it.
2. It can take some minutes until **CloudShell** is completely running and you can see Linux console.
3. In order to get Dev parameter type the following command in **CloudShell** :<br>
    `aws ssm get-parameters --names /my-app/dev/db-url /my-app/dev/db-password`<br> and press **Enter**.
    <details>
    <summary><strong>Output</strong></summary>
    
    ```
    [cloudshell-user@ip-10-0-96-85 ~]$ aws ssm get-parameters --names /my-app/dev/db-url /my-app/dev/db-password
    {
        "Parameters": [
            {
                "Name": "/my-app/dev/db-password",
                "Type": "SecureString",
                "Value": "AQICAHg+FTl98gCPPnQzZ1Wh7V4QicQkAHXb0BUlA8kH3q8uWgFo6a4ZaZD9jxRhbeXYFlkxAAAAaTBnBgkqhkiG9w0BBwagWjBYAgEAMFMGCSqGSIb3DQEHATAeBglghkgBZQMEAS4wEQQMWOHH/y24z9qoC8nGAgEQgCZUo0lWOqeiTuejwQuh/K2N9iIAc5nLmGAnz6S3TAB223HYA6Utvw==",
                "Version": 1,
                "LastModifiedDate": "2021-12-17T07:51:25.954000+00:00",
                "ARN": "arn:aws:ssm:us-east-1:111111111111:parameter/my-app/dev/db-password",
                "DataType": "text"
            },
            {
                "Name": "/my-app/dev/db-url",
                "Type": "String",
                "Value": "dev.database.dreamdb.org:3306",
                "Version": 1,
                "LastModifiedDate": "2021-12-17T07:49:51.907000+00:00",
                "ARN": "arn:aws:ssm:us-east-1:111111111111:parameter/my-app/dev/db-url",
                "DataType": "text"
            }
        ],
        "InvalidParameters": []
    }
    ```
    </details>
    As you can see in the command output the db-password value is encrypted as we has use **SecureString** type for it.
1. In order to decrypt the db-password value use additional parameter `--with-decryption`:<br>
    `aws ssm get-parameters --names /my-app/dev/db-url /my-app/dev/db-password --with-decryption`
    
    <details>
    <summary><strong>Output</strong></summary>

    ```
    [cloudshell-user@ip-10-0-96-85 ~]$ aws ssm get-parameters --names /my-app/dev/db-url /my-app/dev/db-password --with-decryption
    {
        "Parameters": [
            {
                "Name": "/my-app/dev/db-password",
                "Type": "SecureString",
                "Value": "DevPassword",
                "Version": 1,
                "LastModifiedDate": "2021-12-17T07:51:25.954000+00:00",
                "ARN": "arn:aws:ssm:us-east-1:111111111111:parameter/my-app/dev/db-password",
                "DataType": "text"
            },
            {
                "Name": "/my-app/dev/db-url",
                "Type": "String",
                "Value": "dev.database.dreamdb.org:3306",
                "Version": 1,
                "LastModifiedDate": "2021-12-17T07:49:51.907000+00:00",
                "ARN": "arn:aws:ssm:us-east-1:111111111111:parameter/my-app/dev/db-url",
                "DataType": "text"
            }
        ],
        "InvalidParameters": []
    }
    ```
    </details>

2. Another option to get all parameters under the path is to use the following command:<br>
    `aws ssm get-parameters-by-path --path /my-app/dev`
    
    <details>
    <summary><strong>Output</strong></summary>
        
    ```
    [cloudshell-user@ip-10-0-96-85 ~]$ aws ssm get-parameters-by-path --path /my-app/dev
    {
        "Parameters": [
            {
                "Name": "/my-app/dev/db-password",
                "Type": "SecureString",
                "Value": "AQICAHg+FTl98gCPPnQzZ1Wh7V4QicQkAHXb0BUlA8kH3q8uWgFo6a4ZaZD9jxRhbeXYFlkxAAAAaTBnBgkqhkiG9w0BBwagWjBYAgEAMFMGCSqGSIb3DQEHATAeBglghkgBZQMEAS4wEQQMWOHH/y24z9qoC8nGAgEQgCZUo0lWOqeiTuejwQuh/K2N9iIAc5nLmGAnz6S3TAB223HYA6Utvw==",
                "Version": 1,
                "LastModifiedDate": "2021-12-17T07:51:25.954000+00:00",
                "ARN": "arn:aws:ssm:us-east-1:111111111111:parameter/my-app/dev/db-password",
                "DataType": "text"
            },
            {
                "Name": "/my-app/dev/db-url",
                "Type": "String",
                "Value": "dev.database.dreamdb.org:3306",
                "Version": 1,
                "LastModifiedDate": "2021-12-17T07:49:51.907000+00:00",
                "ARN": "arn:aws:ssm:us-east-1:111111111111:parameter/my-app/dev/db-url",
                "DataType": "text"
            }
        ]
    }
    ```
    </details>

    So you can see both db-url and db-password values in output

1. In order to get parameters recursively from several folders nested from the single path you can use the following command:<br>
    `aws ssm get-parameters-by-path --path /my-app/ --recursive`
    <details>
    <summary><strong>Output</strong></summary>

    ```
    [cloudshell-user@ip-10-0-96-85 ~]$ aws ssm get-parameters-by-path --path /my-app/ --recursive
    {
        "Parameters": [
            {
                "Name": "/my-app/dev/db-password",
                "Type": "SecureString",
                "Value": "AQICAHg+FTl98gCPPnQzZ1Wh7V4QicQkAHXb0BUlA8kH3q8uWgFo6a4ZaZD9jxRhbeXYFlkxAAAAaTBnBgkqhkiG9w0BBwagWjBYAgEAMFMGCSqGSIb3DQEHATAeBglghkgBZQMEAS4wEQQMWOHH/y24z9qoC8nGAgEQgCZUo0lWOqeiTuejwQuh/K2N9iIAc5nLmGAnz6S3TAB223HYA6Utvw==",
                "Version": 1,
                "LastModifiedDate": "2021-12-17T07:51:25.954000+00:00",
                "ARN": "arn:aws:ssm:us-east-1:111111111111:parameter/my-app/dev/db-password",
                 "DataType": "text"
            },
            {
                "Name": "/my-app/dev/db-url",
                "Type": "String",
                "Value": "dev.database.dreamdb.org:3306",
                "Version": 1,
                "LastModifiedDate": "2021-12-17T07:49:51.907000+00:00",
                "ARN": "arn:aws:ssm:us-east-1:111111111111:parameter/my-app/dev/db-url",
                "DataType": "text"
            },
            {
                "Name": "/my-app/prod/db-password",
                "Type": "SecureString",
                "Value": "AQICAHg+FTl98gCPPnQzZ1Wh7V4QicQkAHXb0BUlA8kH3q8uWgGBS2xPeFaetQfUfis5GptJAAAAajBoBgkqhkiG9w0BBwagWzBZAgEAMFQGCSqGSIb3DQEHATAeBglghkgBZQMEAS4wEQQMpLEtvQUvOjvSPIvkAgEQgCcOcuj1tPvbZObaF9Wz/8SK/4oT0X36pPL/OPAUzvLIcDz5ZuemJ58=",
                "Version": 1,
                "LastModifiedDate": "2021-12-17T07:52:55.048000+00:00",
                "ARN": "arn:aws:ssm:us-east-1:111111111111:parameter/my-app/prod/db-password",
                "DataType": "text"
            },
            {
                "Name": "/my-app/prod/db-url",
                "Type": "String",
                "Value": "prod.database.dreamdb.org:3306",
                "Version": 1,
                "LastModifiedDate": "2021-12-17T07:52:27.481000+00:00",
                "ARN": "arn:aws:ssm:us-east-1:111111111111:parameter/my-app/prod/db-url",
                "DataType": "text"
            }
        ]
    }    
    ```
    </details>
    
    In output you should be able to see all parameters for both Dev and Prod envs
    
### Task 3: Use App parameters stored in SSM Parameter Store with AWS Lambda

1. Open AWS **Lambda** consolein and click on **Create function**
2. Fill in **Function name** , e.g. test-parameter-store
3. For Runtime choose **Python 3.8**
1. Expand **Change default execution role**
4. For Permissions choose **Create a new role with basic Lambda permissions**. At the bottom of this section you can find the AIM role name. Write down it as we will use it later in this task for giving additional permissions to Lambda for access to Parameter Store
1. **Advanced settings** leave with default values.
5. Click on **Create function**
6. In the left panel of **Code source** find **lambda\_function.py** and click on it with the right button and then click on Open in the context menu.
7. Replace the default script with the following python script
    ```python
    import json
    import boto3
    region_name = "<current_region_name>"
    ssm = boto3.client("ssm", region_name)
    def lambda_handler(event, context):
          db_url = ssm.get_parameters(Names=["/my-app/dev/db-url"])
          print(db_url)
          db_password = ssm.get_parameters(Names=["/my-app/dev/db-password"])
          print(db_password)
          return "worked!"
    ```
1. Find your current AWS region (e.g. region=us-east-1) in the page URL and update **region\_name** variable in the pyton code with the real region value
2. Click on **Deploy**
3. Click on **Test** and select Create new test event
4. Fill in **Event name** , e.g. **mytest** and click on **Create**
5. Click on **Test**
6. You should see an error **&quot;AccessDeniedException when calling the GetParameter operation&quot; because your Lambda is not authorized to perform this operation**. You need to fix this
7. Open **AWS IAM** console in a new tab of your browser.
8. Click on **Roles** in the left panel and enter the name of Lambda IAM role (created in 4-th step) in the Search field. Then open it.
9. Open **Permissions** tab and click on **Add inline policy**
10. Fill in policy parameters:

    - Service=Systems Manager
    - Action=Read: GetParameters, GetParameterbyPath
    - Resources:(Add ARN) Region=Any, Account=Any, Parameter name= my-app/\*

1. Click on Review policy and check that everything looks good
2. Fill in the policy name – SSMAccessForMyApp and Then click on **Create Policy**
3. Get back to the browser tab with where you have Lambda console opened and Refresh the page
4. Click on **Test**
5. If everything is fine you can see **Response**&quot;worked!&quot; in **Execution results**
    <details>
    <summary><strong>Execution results</strong></summary>

    ```
    Test Event Name
    mytest

    Response
    "worked!"

    Function Logs
    START RequestId: 5d11ee1d-f0e4-438b-8af0-1d7af9f6be21 Version: $LATEST
    {'Parameters': [{'Name': '/my-app/dev/db-url', 'Type': 'String', 'Value': 'dev.database.dreamdb.org:3306', 'Version': 1, 'LastModifiedDate': datetime.datetime(2021, 12, 17, 7, 49, 51, 907000, tzinfo=tzlocal()), 'ARN': 'arn:aws:ssm:us-east-1:111111111111:parameter/my-app/dev/db-url', 'DataType': 'text'}], 'InvalidParameters': [], 'ResponseMetadata': {'RequestId': 'dfe298b1-57ad-485d-954b-ac64355c60ce', 'HTTPStatusCode': 200, 'HTTPHeaders': {'server': 'Server', 'date': 'Fri, 17 Dec 2021 11:26:51 GMT', 'content-type': 'application/x-amz-json-1.1', 'content-length': '262', 'connection': 'keep-alive', 'x-amzn-requestid': 'dfe298b1-57ad-485d-954b-ac64355c60ce'}, 'RetryAttempts': 0}}
    {'Parameters': [{'Name': '/my-app/dev/db-password', 'Type': 'SecureString', 'Value': 'AQICAHg+FTl98gCPPnQzZ1Wh7V4QicQkAHXb0BUlA8kH3q8uWgFo6a4ZaZD9jxRhbeXYFlkxAAAAaTBnBgkqhkiG9w0BBwagWjBYAgEAMFMGCSqGSIb3DQEHATAeBglghkgBZQMEAS4wEQQMWOHH/y24z9qoC8nGAgEQgCZUo0lWOqeiTuejwQuh/K2N9iIAc5nLmGAnz6S3TAB223HYA6Utvw==', 'Version': 1, 'LastModifiedDate': datetime.datetime(2021, 12, 17, 7, 51, 25, 954000, tzinfo=tzlocal()), 'ARN': 'arn:aws:ssm:us-east-1:111111111111:parameter/my-app/dev/db-password', 'DataType': 'text'}], 'InvalidParameters': [], 'ResponseMetadata': {'RequestId': 'fb05b173-8955-4895-a8fe-4d95755db5ce', 'HTTPStatusCode': 200, 'HTTPHeaders': {'server': 'Server', 'date': 'Fri, 17 Dec 2021 11:26:51 GMT', 'content-type': 'application/x-amz-json-1.1', 'content-length': '469', 'connection': 'keep-alive', 'x-amzn-requestid': 'fb05b173-8955-4895-a8fe-4d95755db5ce'}, 'RetryAttempts': 0}}
    END RequestId: 5d11ee1d-f0e4-438b-8af0-1d7af9f6be21
    REPORT RequestId: 5d11ee1d-f0e4-438b-8af0-1d7af9f6be21	Duration: 277.97 ms	Billed Duration: 278 ms	Memory Size: 128 MB	Max Memory Used: 66 MB	Init Duration: 335.32 ms

    Request ID
    5d11ee1d-f0e4-438b-8af0-1d7af9f6be21
    </details>

6. In **Function logs** you can see parameters with their values there. By the way &quot;/my-app/dev/db-password&quot; value is encrypted.
7. If you want to decrypt it, you should change the following line in the python script:
    ```
    db_password = ssm.get_parameters(name=["/my-app/dev/db-password"], WithDecryption=True)
    ```
1. Click on **Deploy**
2. Click on **Test** and you can see &quot;worked!&quot; message in **Execution results**
3. In **Function logs** section you can find that /my-app/dev/db-password value is decrypted now.


### Benefits / Outcomes / Pros and Cons / Summary 

Now you know how to create Parameters Store records and example of how to work with it.

### Pricing 

Free 

### Tearing down 

1. Delete parameters
1. Delete lambda function
1. Delete Role
