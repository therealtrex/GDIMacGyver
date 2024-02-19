![](https://lh7-us.googleusercontent.com/MnWSy-fjYkeY8OktC4WBFt6mWEbmsXvkfjcfbg8CwRmkjkqQHwQxJ7eqUsUeJWSRuo7XH48kZ3fdBERwRgEPxSLEkHtMFx3aRy57cxBiHFG58Tyhpj7IqNrWUNMYsWSkPTUo8U8C9BCburNHjjtRqzc)

![](https://lh7-us.googleusercontent.com/gfAH7xSdi_Q7xnKV8zQlPpnfJqIHLl8Ut933f8WeUmfqNpLgwOIJ3Q3fQ3vF7wAUC4P5DGsdLGhtwePltL22lOmVJwDzo_2ZLM5iPvfEsawviNXymuTFRa-XAxDp8metUmilrOHi24XV5bxtXY8b2vI)AWS Getting Data In Lab Guide: SQS Based S3 PULL

How to _PULL_ data from Amazon S3 into Splunk using the Splunk Add-on for AWS

LAB 1: SQS based S3 PULL Method

- In this lab we will configure AWS CloudTrail to log AWS API calls to an S3 bucket. 

- Create relevant users and authentication policies in AWS required for this lab

- Configure Amazon SQS queue so we know when there is new data in S3 from CloudTrail

- Install our AWS Add-on inside of Splunk and configure it

- Setup Splunk to poll the SQS queue and PULL the data out of S3 directly when new data exists

Time to Complete: **30 Minutes**

Author: **Trav (T-REX) Kane**

![](https://lh7-us.googleusercontent.com/SNld325wbPMQHN2i-oBuzF1TkyC4YpV2W_e5VilL4vEToM7aB-UP934b4symSJRfBxUhyel4hz4YJ6soaTY1W7xC-qQeYaxLInRUA1rx4Kxnf0kUVt3K8P_BbPzFJQiSzKL1sZf1JzpQgl0XS_iXRoE)

**Steps To Set Up**![](https://lh7-us.googleusercontent.com/L2AyqAoJwVYpCs3ASBZH9WDBNJ_nVFfqgwwIHpxmn6N5RDj2nZHX0C2e-kRys21b4MdAE_DihJKHgT1pqYj8I1cKQnRbbKVHukZovduTpX7qOYy2vX3Ip8C-5UJ_UKk8DU7WCytsnTqSgGGDULplqvI)

1. Create S3 bucket for Cloudtrail![](https://lh7-us.googleusercontent.com/L2AyqAoJwVYpCs3ASBZH9WDBNJ_nVFfqgwwIHpxmn6N5RDj2nZHX0C2e-kRys21b4MdAE_DihJKHgT1pqYj8I1cKQnRbbKVHukZovduTpX7qOYy2vX3Ip8C-5UJ_UKk8DU7WCytsnTqSgGGDULplqvI)

2. Configure CloudTrail Trail![](https://lh7-us.googleusercontent.com/L2AyqAoJwVYpCs3ASBZH9WDBNJ_nVFfqgwwIHpxmn6N5RDj2nZHX0C2e-kRys21b4MdAE_DihJKHgT1pqYj8I1cKQnRbbKVHukZovduTpX7qOYy2vX3Ip8C-5UJ_UKk8DU7WCytsnTqSgGGDULplqvI)

3. Setup SQS queues ![](https://lh7-us.googleusercontent.com/L2AyqAoJwVYpCs3ASBZH9WDBNJ_nVFfqgwwIHpxmn6N5RDj2nZHX0C2e-kRys21b4MdAE_DihJKHgT1pqYj8I1cKQnRbbKVHukZovduTpX7qOYy2vX3Ip8C-5UJ_UKk8DU7WCytsnTqSgGGDULplqvI)

4. Setup IAM policy![](https://lh7-us.googleusercontent.com/L2AyqAoJwVYpCs3ASBZH9WDBNJ_nVFfqgwwIHpxmn6N5RDj2nZHX0C2e-kRys21b4MdAE_DihJKHgT1pqYj8I1cKQnRbbKVHukZovduTpX7qOYy2vX3Ip8C-5UJ_UKk8DU7WCytsnTqSgGGDULplqvI)

5. Setup IAM user![](https://lh7-us.googleusercontent.com/L2AyqAoJwVYpCs3ASBZH9WDBNJ_nVFfqgwwIHpxmn6N5RDj2nZHX0C2e-kRys21b4MdAE_DihJKHgT1pqYj8I1cKQnRbbKVHukZovduTpX7qOYy2vX3Ip8C-5UJ_UKk8DU7WCytsnTqSgGGDULplqvI)

6. Create S3 event notification![](https://lh7-us.googleusercontent.com/r8rREfV48IHHGcfU1gNaIvaIC50TdrDDQQw0e-wRa-0WzghAnGRtjgIl7809eFmcdKDLytHExIvzPumswVQ-1vmcoVW5dl9SiCENQNOXgZAXhNWQz_z3SJYwy5ewwFzZncVwPoOLNoMn3aQXj8FNf88)

7. Install AWS Add-on![](https://lh7-us.googleusercontent.com/r8rREfV48IHHGcfU1gNaIvaIC50TdrDDQQw0e-wRa-0WzghAnGRtjgIl7809eFmcdKDLytHExIvzPumswVQ-1vmcoVW5dl9SiCENQNOXgZAXhNWQz_z3SJYwy5ewwFzZncVwPoOLNoMn3aQXj8FNf88)

8. Create Index![](https://lh7-us.googleusercontent.com/r8rREfV48IHHGcfU1gNaIvaIC50TdrDDQQw0e-wRa-0WzghAnGRtjgIl7809eFmcdKDLytHExIvzPumswVQ-1vmcoVW5dl9SiCENQNOXgZAXhNWQz_z3SJYwy5ewwFzZncVwPoOLNoMn3aQXj8FNf88)

9. Configure IAM user in AWS add-on![](https://lh7-us.googleusercontent.com/r8rREfV48IHHGcfU1gNaIvaIC50TdrDDQQw0e-wRa-0WzghAnGRtjgIl7809eFmcdKDLytHExIvzPumswVQ-1vmcoVW5dl9SiCENQNOXgZAXhNWQz_z3SJYwy5ewwFzZncVwPoOLNoMn3aQXj8FNf88)

10. Create Input in AWS add-on![](https://lh7-us.googleusercontent.com/L2AyqAoJwVYpCs3ASBZH9WDBNJ_nVFfqgwwIHpxmn6N5RDj2nZHX0C2e-kRys21b4MdAE_DihJKHgT1pqYj8I1cKQnRbbKVHukZovduTpX7qOYy2vX3Ip8C-5UJ_UKk8DU7WCytsnTqSgGGDULplqvI)

11. Generate data and see results

\
![](https://lh7-us.googleusercontent.com/xbieM6j1usZCDyVAWsQajisVLSIzOAQOZpVK4re0i-VRkGWRl3A6VWn8aUMgAAtvPLHVqbXXPUdT82etnVWr6SO8Asiv5fepNzDstT6jBIKTZjILm4LVAgtYvVxzFi9_XM-XYJKK5m7qlamTE6PMYDM)


# AWS Steps

### Step 1: Create an S3 bucket for CloudTrail

1. From the AWS console search for and **select S3**

\
![](https://lh7-us.googleusercontent.com/EpUBm94SPL9hGSwZ_VMZBfr4Mel3dJUgOVs9oOpPClCM4mFXTEOYXUpvpUepYgaSpKn31HHzws72n7oXuiGYU7tPb279FsNNpw6q-mUpuyAe-H0Q_w7xsBCpnRCEcBwu5CUgPVgAz6on2hKodL54UdE)

2. From the S3 menu select **Create Bucket**

3. Select your **region**

4. **Enter unique bucket name** - eg my-logging-bucket-\<region>-\<name>

\
![](https://lh7-us.googleusercontent.com/UInBqsJ2DVm0S63Z7MCK92YJK8kQ6CLeIZ4WEWifc2znjlEggZBnv30RXk5F5jxUfAeisvYm5kDd-NLPAlmsFMBeRGTb_jSGLwmwR0OEXkE-o0tZUJ7a2cm2JMrpHW1g1dPRZRthYqBAAtXHZnVCx9U)

5. Leave remaining defaults and click **Create Bucket**

6. Before you go **select** the **radio button** for your bucket and choose **Copy ARN**. 

7. **Save this somewhere** eg notepad as you will need it later!


### ![](https://lh7-us.googleusercontent.com/a8amgYRWzRdCebfOkh90f42R5llKtbsF08QiZFWvFUs6qcyqTwGM5I40zG7Ob4ksZgnbLmEHaM7_SXbBVwrQt-PKpWgHMEks8gmb2RU4BeMChMWi_8HQLzSAkJwxTWkLrdiuje6iCVNgUBjoF4UQmKM)

### STEP 1: Done, Congratulations!

\
![](https://lh7-us.googleusercontent.com/7UU05IAANgsr5fQQDxeFKV3wCPM9QWSOecxEv4JGg_a4WXp4YAvWdbMG3h-4D_pFl60aob9WuBer8BtaIOdwpI8HeuuhKnlUfbX35RdFB5205MzdTX9Ws6Yb6L8uZxF0FdUuPAPnyU2EK9JuU_dpaIk)


### Step 2: Setup CloudTrail

1. From the AWS console search for and **select CloudTrail**

![](https://lh7-us.googleusercontent.com/DSqDuGT-SynQ5gsHY5VmXHirR9iqGPCLOU0Wf4WyUah0NiV0zXX3LYJEQ1gsR42DEfJohlcwwkzLP0X33JaRXhgQHCOQKVhR24X7MQRgFgicO8auA2Sy8FHucL8b0-2jxqFTOCD5YSk89H3uTsEtjxo)

2. From the CloudTrail menu select **Create trail**

3. **Name your trail** eg management-events-\<account-number>-\<name>

4. **Select** the **Use existing S3 bucket** radio button

5. **Click browse** and **select the bucket you created above**

![](https://lh7-us.googleusercontent.com/_r70o_ZJ_3ThuiHAF76gWUlmi2-9CDKod7vHDMR8OMe61m_axfLjGSqSXIzGK1l-SV3g1skZsWNelcU-lpTmv1MIcRFtvlyCKaZR49o01Ap8Td8lVobo7zfaqin7ZHq34i_L-sgwP8vgA6eqV3a3yME)

6. Leave **prefix empty**

7. Leave **Enabled ticked** for **SSE-KMS encryption** 

8. Leave **New selected** for KMS

9. **Enter** in a **AWS KMS Alias** eg cloudtrail\_management\_kms\_\<name>

![](https://lh7-us.googleusercontent.com/tD79fpxae469gVL1db3ez3dslHA230Do56_2VC9TD2UBgkHwlaCWZa6yLT4GceecI4BDC0TyX1pWef8nCINCpAbK3SSGqJEq4a0YNGKtX4xgSptlKScjJT_vDZD337sTApWIeHGwrUO1o5VTG3gvjEQ)

10. Leave remaining defaults and **click Next**

11. **Leave defaults** for Choose Log Events (Management events only) and **click Next**

12. Review and **click Create Trail**


### STEP 2: Done, Congratulations!

\
![](https://lh7-us.googleusercontent.com/hoaFchZ-_iCk7ijMAXb_uzqcwh0YqP6fGNkVjD0srzkrIfV5rdZ1w0XsVf595oearps6jK-JnZ0RA5X6_aCdv4K5SYlniaJ_SB-LuZ_yjnqdY15LGjoIHJnPXVG2c7Eki96S-QfW_p-N3pK4hT5SlgI)


### Step 3: Create SQS Queues

1. From the AWS console search for **SQS** and **select Simple Queue Service**

![](https://lh7-us.googleusercontent.com/_hdMNeBAyXYoPAMvvkX0VK-zX-seByZusDaBxzGbk0tNEm9p_TZg1ZcOt4WlJ4_L9m52ngMKzKJBEiOnols4a19pTHWm8zr_MykFLbpQFVB-Vm2wOIFD_4ttGJenswNQVHUdw5OGit7kk1rLnXvf3lI)

2. Click **create queue** 

3. Leave **standard queue** selected

4. Enter in a **queue name with DL on the end** eg cloudtrail-sqs-\<name>-DL![](https://lh7-us.googleusercontent.com/ggs7XkuNSlX6uCPeVcJEEllYe0IIA5ymNQsmo6RfpXcTkPwrsE5DqGil9xZpOFd91jamnrDVp88_5JiTsU1wYghej8JH-wXJR0Fjqjomv2BvKjshyZ4sD-jMUseJpIk4xxNqu5GDEEzBVZ0u5j4Avsk)

**_Note: This is the Dead Letter (DL) Queue we are creating first_**

5. **Set** visibility timeout to **5 minutes**

****![](https://lh7-us.googleusercontent.com/dh8yvQPTc3x4AYyP9BQn84Rpgv56ztb__BWc2IUDQqwPoWGXyE_DvjYbxxnF8vLSm8m2jsUohwJB7Y25qr_sZAU7kUlo8Pf_VJaPW9GVlJwtOXhVoQjfGWvO9lDU-wFZSuE1_VwuOHCoOueDe_EgvXQ)****

6. Leave remaining settings and click **Create queue** 

7. **Go back to SQS** and click **Create queue**

8. Again Leave **Standard queue selected**

9. Enter in a **name with NO DL** eg cloudtrail-sqs-\<name>

10. **Set** visibility timeout to **5 minutes**

![](https://lh7-us.googleusercontent.com/9-KShG8bLmINNWQ9QJXzgRcd8DDsTO_VGNDdXblBT9KK-q3AdrWf5yFiYHBB8a4TEJsbz4sGaXE8ia4pQggig86GrZAJqpqXZk01-aTUxPZC8nktAm2BLVmTFXAuiAkuCFRCMQxTAVgiyNDA7OXP4m8)

11. Scroll down and **set Deal-letter queue to enabled** 

12. Select the **Dead letter queue (DL)** you **created above**

![](https://lh7-us.googleusercontent.com/4JxeilIVIFs4_GBXhzddqzpiwx1I78H2ZjnhBe71DGjalMKk03v_RUiKcZ4CFO2X_6QeRLSxcyNoWJsVrrmPrsusTmiooVHZia_IMrmTdcCzbLwggtrA6F2JEE5bXw0G0MffGqzVQVsbpIDxe2PT3bo)

13. Leave **remaining defaults** and select **Create queue**

14. **Copy** the **SQS ARN** somewhere to use in this next section

15. From your SQS page, **select** the **Access Policy Tab**

****![](https://lh7-us.googleusercontent.com/zR7IunWxGYomEndHsLMS3U7ARV-2yFBTnSGKOmYe6Lc1fta_-R5SUQ6msoj4TPko_n_sFDYFb9bXuHBx2ErWRildfgUF4PQXPO9YTViDOEK9e50ptCxKfvpQ5JVJN5eVrRtZ-PSL_smUfhhN3KFutpo)****

16. **Click Edit within the Access policy (Permissions)**

17. **Replace** the entire existing policy **with the one below** making sure you also add the additional information described in notes below as well. 

\_\_\_\_ ![](https://lh7-us.googleusercontent.com/u-gA0-WI_EfWPKhZRFvI9019L1r31dp-pwtpSKFOKB6XGdbVY7ToKTrLgDSsbRK2VR0eQ0AJeIH5dRp70PNe6FrguspIC3d10eCVZ5lCi_PMNPf02VCGcKYQwlP2jGzU_QbxvEb0bIZ10Y5VuXDDur0) COPY BELOW THIS LINE ![](https://lh7-us.googleusercontent.com/u-gA0-WI_EfWPKhZRFvI9019L1r31dp-pwtpSKFOKB6XGdbVY7ToKTrLgDSsbRK2VR0eQ0AJeIH5dRp70PNe6FrguspIC3d10eCVZ5lCi_PMNPf02VCGcKYQwlP2jGzU_QbxvEb0bIZ10Y5VuXDDur0) \_\_\_\_

{

  "Version": "2012-10-17",

  "Id": "SQS Policy to allow S3 access to post messages",

  "Statement": \[

    {

      "Sid": "s3-principal",

      "Effect": "Allow",

      "Principal": {

        "Service": "s3.amazonaws.com"

      },

      "Action": "SQS:SendMessage",

      "Resource": "**\<SQS ARN>**",

      "Condition": {

        "StringEquals": {

          "aws:SourceAccount": "**\<AWS ACCOUNT NUMBER>**"

        },

        "ArnLike": {

          "aws:SourceArn": "**\<S3 Bucket ARN>**"

        }

      }

    }

  ]

}

\_\_\_\_ ![](https://lh7-us.googleusercontent.com/u-gA0-WI_EfWPKhZRFvI9019L1r31dp-pwtpSKFOKB6XGdbVY7ToKTrLgDSsbRK2VR0eQ0AJeIH5dRp70PNe6FrguspIC3d10eCVZ5lCi_PMNPf02VCGcKYQwlP2jGzU_QbxvEb0bIZ10Y5VuXDDur0) COPY ABOVE THIS LINE ![](https://lh7-us.googleusercontent.com/u-gA0-WI_EfWPKhZRFvI9019L1r31dp-pwtpSKFOKB6XGdbVY7ToKTrLgDSsbRK2VR0eQ0AJeIH5dRp70PNe6FrguspIC3d10eCVZ5lCi_PMNPf02VCGcKYQwlP2jGzU_QbxvEb0bIZ10Y5VuXDDur0) \_\_\_\_

\
![](https://lh7-us.googleusercontent.com/ggs7XkuNSlX6uCPeVcJEEllYe0IIA5ymNQsmo6RfpXcTkPwrsE5DqGil9xZpOFd91jamnrDVp88_5JiTsU1wYghej8JH-wXJR0Fjqjomv2BvKjshyZ4sD-jMUseJpIk4xxNqu5GDEEzBVZ0u5j4Avsk)

**Note: The policy above will allow AWS S3 to Send SQS messages from a particular S3 bucket**

18. In the policy, Replace the correct sections below

    1. **\<AWS ACCOUNT NUMBER>** with your AWS account number 

(located top right corner of AWS console, select drop down and copy it)

![](https://lh7-us.googleusercontent.com/mrWiUf62AoYiRa_4eIZCD9vL65ybsQ725VCL4gjvpWffntjK51mW_UtXaXlY_nBlTBeDTglTrWla4rBISd3woagRgW2QgspQr9PL8SnTMCGlauOa2VgKR0Ujk-sUB21Mg6VR4pYEPt7Swd0LLH_gf0g)

2. **\<SQS ARN>** with the SQS ARN you copied earlier (Non DL one)

3. **\<S3 Bucket ARN>** with the S3 ARN you copied earlier at the start of this lab

19) **Click save** once policy has been edited

**STEP 3: Done, Congratulations!******


### Step 4: Create IAM policy 

1. From the AWS console search for and **select IAM**

![](https://lh7-us.googleusercontent.com/I7xdq3Tcq9qF-HsDqbOM-_Wp75_rEB8gMblQ7uKZmJRoqoJIHFD_7WQLQcZjHNC72cxIbNUYpNlXjJEDH8IGH1KgmxjUo_JIfiMTcGC3HbNsVuGNoHfm0pDHvWv6xnhc094ndgT1DMfydmTKciSwt38)

2. **Select policies** from the left hand side

3. **Click Create Policy**

4. **Select JSON** and **paste** the policy below into the policy section

\_\_\_\_ ![](https://lh7-us.googleusercontent.com/u-gA0-WI_EfWPKhZRFvI9019L1r31dp-pwtpSKFOKB6XGdbVY7ToKTrLgDSsbRK2VR0eQ0AJeIH5dRp70PNe6FrguspIC3d10eCVZ5lCi_PMNPf02VCGcKYQwlP2jGzU_QbxvEb0bIZ10Y5VuXDDur0) COPY BELOW THIS LINE ![](https://lh7-us.googleusercontent.com/u-gA0-WI_EfWPKhZRFvI9019L1r31dp-pwtpSKFOKB6XGdbVY7ToKTrLgDSsbRK2VR0eQ0AJeIH5dRp70PNe6FrguspIC3d10eCVZ5lCi_PMNPf02VCGcKYQwlP2jGzU_QbxvEb0bIZ10Y5VuXDDur0) \_\_\_\_

{

  "Version": "2012-10-17",

  "Statement": \[

    {

      "Effect": "Allow",

      "Action": \[

        "sqs:GetQueueUrl",

        "sqs:ReceiveMessage",

        "sqs:SendMessage",

        "sqs:DeleteMessage",

        "sqs:ChangeMessageVisibility",

        "sqs:GetQueueAttributes",

        "sqs:ListQueues",

        "s3:GetObject",

        "s3:GetObjectVersion",

        "kms:Decrypt"

      ],

      "Resource": "\*"

    }

  ]

}

\_\_\_\_ ![](https://lh7-us.googleusercontent.com/u-gA0-WI_EfWPKhZRFvI9019L1r31dp-pwtpSKFOKB6XGdbVY7ToKTrLgDSsbRK2VR0eQ0AJeIH5dRp70PNe6FrguspIC3d10eCVZ5lCi_PMNPf02VCGcKYQwlP2jGzU_QbxvEb0bIZ10Y5VuXDDur0) COPY ABOVE THIS LINE ![](https://lh7-us.googleusercontent.com/u-gA0-WI_EfWPKhZRFvI9019L1r31dp-pwtpSKFOKB6XGdbVY7ToKTrLgDSsbRK2VR0eQ0AJeIH5dRp70PNe6FrguspIC3d10eCVZ5lCi_PMNPf02VCGcKYQwlP2jGzU_QbxvEb0bIZ10Y5VuXDDur0) \_\_\_\_

\
![](https://lh7-us.googleusercontent.com/ggs7XkuNSlX6uCPeVcJEEllYe0IIA5ymNQsmo6RfpXcTkPwrsE5DqGil9xZpOFd91jamnrDVp88_5JiTsU1wYghej8JH-wXJR0Fjqjomv2BvKjshyZ4sD-jMUseJpIk4xxNqu5GDEEzBVZ0u5j4Avsk)

**Note: This will allow management of  SQS queues, basic S3 operations and KMS decryption.** 

5. Click **Next**

6. **Name the policy** eg a\_splunk\_input\_sqs\_based\_s3\_\<NAME>

![](https://lh7-us.googleusercontent.com/hmSj0F2SwFPMr-dck6058nhWqNzEbfpMUsbBe2EL4_TN3aa6-Enr6T7jFh1_oko80mHisPoDG9U7ZMVU7_WNUciuAEHfmpiG8Q0UGvqjuKnNN7Kv_WkQYzMhUSXBJIeS8VeoeLnFxVmsc56MfQEfoUM)

7. Click **Create Policy**


### STEP 4: Done, Congratulations!

### Step 5: Create IAM user

1. While still in the IAM section, **select users** from left hand side panel

2. **Click Create user**

3. Enter in a **User Name** eg splunk-inputs-user-\<NAME>

4. Leave **console access UNTICKED** and **click Next**

![](https://lh7-us.googleusercontent.com/Ji81opwdD5UjIO5jNQSTU-f7B6bKSn89E_FKDV9pAjbm45xzgBSH7KV4McsDKHfGtbkP5ulVRV4mp0ZZMGbYMnLooZ_O_4wpDqFTkbL7sTB5HGAL_4bb4sA1bHvqLTih7Xv7tcQmMgfov5OypgPoqRc)

5. **Select Attach Policies directly** 

6. **Select** the **policy we created earlier** 

7. **Click Next**

8. Review and **Click Create user**

9. **Select your newly created user** to open up the details

10. **Select** the **security credentials tab**

![](https://lh7-us.googleusercontent.com/_lUIFFvXS9Aj4o9Regn4xrsXkwpgUpSiVTSptrXUgJp4movKUGQqYXnxLo2v3etFHzByaTbD31t3ZIbmkNZ5R4BDn5q5UTFsuVWtQ0K_-x3l7oQNo1MndgLNgwWZTm5X7GuHgHQ80gRVa0SVcvZgkbU)

11. Click **Create access key** under Access Keys section

12. **Select Command Line Interface (CLI)**

13. **Tick I understand…** check box and **click Next**

14. Enter in a description if you like and **click Create access key**

15. **Download CSV** and **click Done**

![](https://lh7-us.googleusercontent.com/IfLxn-If43hvtzWjNuyukRRw5CJPHxXocZxcY0UAtavAvxKjQhHL8peigQuC3dLX5ifpXICo6fhwr-rBwtdLcJSYBQdrhgGtP3FH1GIXnXfE78aTZ-MP2Eqn2S3qrWTJGqbR0SbuVBDYlPvYWqqXI24)


### STEP 5: Done, Congratulations!

### Step 6: Configure Notification on S3

1. From your AWS console search for and **select S3**

![](https://lh7-us.googleusercontent.com/EpUBm94SPL9hGSwZ_VMZBfr4Mel3dJUgOVs9oOpPClCM4mFXTEOYXUpvpUepYgaSpKn31HHzws72n7oXuiGYU7tPb279FsNNpw6q-mUpuyAe-H0Q_w7xsBCpnRCEcBwu5CUgPVgAz6on2hKodL54UdE)

2. **Select** the **S3 bucket** you created earlier

3. **Select properties**

![](https://lh7-us.googleusercontent.com/LcFrfsEwIGR8qhrRasBE5YizIUPCjIiBj1BVSIb7GOZn4YTQRaSYyKqOmIm5nPPk_u1amtIyA66_lgd73UxQH5LEIOYtfUq9tLwVywW_4vSxwXA0VKm2y-lJv2llqlpux6Zc1x-SLGJv6G1nbKsS7gM)

 

4. Scroll down to **event notifications** section **select Create event notification**

![](https://lh7-us.googleusercontent.com/lE-vmlS_8i4U3KPqervf-MOgZkZwKGBGwxMKRwvNplOHtcGm1-veKV8YNHzLF0Av-KzVtPEXF9FcDKmCFhBZ976UPH_VdN09JmCU7g5-ocmtihwdhA88pIDyZsGEAWWvm71StDpVBoynfNgYrSMRZpA)

5. **Enter** an **event name** eg cloudtrail-sqs-splunk-\<NAME>

6. Select **All object create events** under Event types

![](https://lh7-us.googleusercontent.com/fHNzWXC4bbGdI-zLIT2srUoYHj3nXBv40gssf43rum5AU0SU88EErwEB0xAv-ATfaxFnh-vwX6hGERvJZ3EyCAYmJx4X8jr203vNIdxvW5zuVbS_y9ICMATLAYtInhlcRCq5dA9KnL1fIPJcfjMW1i8)

7. Scroll down and under destination **select SQS queue** 

8. **Select** your **SQS queue you created earlier** (NON DL one) 

9. Click **Save changes**

****![](https://lh7-us.googleusercontent.com/D8xK7gknmO-Ssci3gnC8_FKt06WEI6ic0DGTskUW2Juc4tucLBv17eRzmiO2TUYXOBbyg_yB-gR9C7MCOqcha8PzFyHLkEdtAIC5niIsCUXhQqFP3e30Qx6ScwJIci7YotxufA6ItOGNLhUFAlJxTtk)****


### STEP 6: Done, Congratulations!

# Splunk Setup 

### Step 7: Install AWS Add-on on Splunk Cloud 

\
![](https://lh7-us.googleusercontent.com/ggs7XkuNSlX6uCPeVcJEEllYe0IIA5ymNQsmo6RfpXcTkPwrsE5DqGil9xZpOFd91jamnrDVp88_5JiTsU1wYghej8JH-wXJR0Fjqjomv2BvKjshyZ4sD-jMUseJpIk4xxNqu5GDEEzBVZ0u5j4Avsk)

**Note: This step is optional depending if your AWS Add-On has already been installed. Check with instructor**

1. **Login** to your **Splunk Cloud Instance**

2. From the main Splunk page **select Apps**, then **click** on the **Find more apps**

![](https://lh7-us.googleusercontent.com/5YJbRECSEOWpUW7h6ziwWDn6OrZ57PC_0QGgpPlKvjVFVOVynsBKGD_apECJ4WScL9o5y86OpJudStOUqdLVoUvu4Qs51igHi1bdqHJTUrEeCe3dsYPuUzCQyN7Z3jiMIRzGEggbs4NJWr37Cpx3eU8)

3. In the Browse More Apps, **tick** the **box** for **Add-on** under the **APP-TYPE**

![](https://lh7-us.googleusercontent.com/A_8e3U28uxPTtqWWHq-iJwhfWdWveZgdPR-O6Lu42Xwh7wmjZlq8-LiYxBlTHws6YPUPdMf4Z9Itmy663HUPB4gZITNJCzOyh6oqK0Fere-DQ4twktRCduyLGpz0oyrXPR-liWNT-9h7HBo0RKHYAbs)

4. In the **search box** **Find apps by keyword, technology**… **search for Amazon**

5. Look for and **find** the **Splunk Add-on for Amazon Web Services (AWS)**

6. **Click Install** 

![](https://lh7-us.googleusercontent.com/aSKAu0RD-F48ANR_92w1unISR4kyjeryyPofQUZh0-d9-RJlHH-2ZAprQMQ5FVDWLTwsJVcKn-I0fHDoeP1RKR31apSoYUh7K37KK3JiVbjLPE4sutYj8fJRFMusu3ct-wvsQxBe9zLGpLnJ3a72njI)

7. **Enter your Splunk credentials** 

\
![](https://lh7-us.googleusercontent.com/ggs7XkuNSlX6uCPeVcJEEllYe0IIA5ymNQsmo6RfpXcTkPwrsE5DqGil9xZpOFd91jamnrDVp88_5JiTsU1wYghej8JH-wXJR0Fjqjomv2BvKjshyZ4sD-jMUseJpIk4xxNqu5GDEEzBVZ0u5j4Avsk)

**Note: These are your Splunk credentials not your Splunk Cloud instance credentials)**

**Don’t have one? Go →** [**here**](https://www.splunk.com/en_us/sign-up.html?redirecturl=https://www.splunk.com/)

8. Click **Agree** and **Install**

9. Once completed **click done**


### STEP 7: Done, Congratulations!

### Step 8: Create Index for Ingestion

1. From your Splunk Cloud screen, **click Settings**, then **click Indexes**

2. **Click New Index**

3. **Enter index name** eg aws-data-\<name>

4. Set **Max raw data size** to be **0**

5. Set **Searchable retention** (days) to be **100**

6. **Select No Additional Storage** 

7. **Click Save**

8. **Click Continue** when done.

![](https://lh7-us.googleusercontent.com/LpJZhUtEJOagJKCrwsafky_Us9sB8e2SGvKqh8W9jQAZVrI1MkFt9theg-pzp9AKOLVFeDSJJOYq_EHLQYV8M_2Dzmp2KH9XqWR5Pkv3AtK0tPZMRiAow8Ta1pbI-4IBL_BLxehw7SmZwqd1vTX1Lac)


### STEP 8: Done, Congratulations!

### Step 9: Configure Splunk AWS Add-on user account

1. **Click** the **Splunk Cloud logo** top left hand side

2. **Select** the **Splunk Add-on for AWS**

3. **Select configuration** tab

![](https://lh7-us.googleusercontent.com/y0s7knYU3I9iO9dCsH1nSV4j3ozmhbOGXzSdENrjTxuUag4pR1jN4koa1HbBRQJwGmv8N2OITdOulfxZ4ee6eNLG_4suxtSU9C5wZ9iR-an5tUqzsGwjyFhhM7zKIDvQO7QTvyDQTY8cxhUtXWKjuyc)

4. Under **account** tab **click Add**

5. **Enter in a** **name** for your user account eg aws-splunk-user-\<NAME>

6. From your downloaded IAM user csv file **enter** in the **Key ID** and **Secret Key**

7. **Click Add**

![](https://lh7-us.googleusercontent.com/z5D4V5NXlD856BFg8OE2sGfehbkRLeUgH9Q9nKpB2Hcl3AaUKZUMGSqHQlDd9i4xLGQLmRw6bKFwbO5ze04mhDfFa9depz6dHL5Dlx1trLWwuVqz_UOp2LTMQWXacEG4TCjXTD2iBBxr2X4QxJKg0S0)


### STEP 9: Done, Congratulations!

### Step 10: Setup AWS Add-on Input

1. Select **Inputs Tab**

****![](https://lh7-us.googleusercontent.com/RjI7A8AUWvOBHpG8Ej6lPBaPdUhzHDnF3-TFQUAw7Goq7I-RK_7k7dbDSlOhch3tqpCDYGivrMVhLCw2RJ9nIx7kqnlRD_RMmTcXIGZSpbjnI7sCogDxDFM0eN92-TnjhkzMld3_7sU62wWjTzgH-zc)****

2. Select **Create New Input** 

3. **Select CloudTrail**

4. **Select SQS-Based S3 (recommended)**

![](https://lh7-us.googleusercontent.com/ZFXY6vcD0LfMZ8KyN7ehR6LmR4PrDg70VPCxSKsxzYzxCJ6ala21-wFUJ17LRQMhQwOWKc1VGhqzbhkFojvtySshVp6hU2oLSmzbW6bIyVs0HciusvJfOzGX24WZyMfTA_--2qIpTjRal2tbcR5rKwA)

5. **Enter** in a **name** eg cloudtrail-management-\<name>

6. **Select** the **AWS account** you entered earlier 

7. **Select** the **region** where your lab configured

8. From the **SQS queue name** **select** your **SQS queue** (NOT THE DL ONE)

9. **Untick** the **Signature Validate All Events**

10. In **Index section cross** out **default** and **click** the **drop down** to **select** your **index** created earlier

11. Leave remaining defaults and **click Add**

![](https://lh7-us.googleusercontent.com/PBX1ls9YrTANA4P8Hzbwj5VP0iokYB5XbjDYxI5rTxTYEc0S0mchIjYCHaWEKMOR4yWrthGrc4CYAajy6figFdsHzuenpe8AZwTgvpZGSMet-d36KsNaFR0iw_fpXPg6Tey5LrkKnABbTdtJ7RqNQ20)


### STEP 10: Done, Congratulations!

### Step 11: Final Step, view your data!

1. **Click** the **Splunk Cloud logo** top left hand side

2. **Select Search and Reporting**

3. Enter in the search bar 

index=”**\<your index name>”**

![](https://lh7-us.googleusercontent.com/n70OEnDnogav90uYaxwqzFvFxYNC57lnkNsAF6Mgbl2F2r7XTyog_adGnA9uRuMNYy4Y8iPaZhGvr4IRHtIgJViH4wOC6FUz16a5MmRMDB6kzPMHNK4G13iz4fcPPFvjTDDSESRgGKkdyZu0Gg0ZDy4)

![](https://lh7-us.googleusercontent.com/DivQtBXA3z96eIUSNFH7AN1pGXrRe8qnEAD-9JMLbbCieIFNsCBQ3MwdehLh1MD_Hx5EXChDj7ItoxW7KuWJNNKvuA04XsWRREuMEpn4hI1IaVYBbPgBYViIOlJZxReXR8VPOFXq9a3WJ6RQccaGGW0)

No data yet? 

Wait a few minutes, try again, if nothing still. Try generating some fresh data below. 


# Summary: What have we just done

- We created an s3 bucket for our cloud trail logs

- We created a cloud trail log trail to log to that S3

- We setup the required SQS queues and required permission for S3 and SQS to interact with each other

- We then setup an IAM user for Splunk to use as part of the Add-on

- We then went to Splunk and setup the AWS Add-on

- Created a Splunk index to store the data

- Added the security credentials for the Splunk AWS Add-on

- Configured our first input for CloudTrail SQS Based S3 inside the AWS Add-on

- Generated some management APi calls 

- Saw the data fly into Splunk for further processing!


### Done, in fact you have done the entire Lab 1! 

### You only need to go on past here if you are having trouble viewing data or diagnosing issues. 

### Congratulations!!

# Generating Data and Debug

### Step 12: How to generate some data if you have none

1. From your **AWS Console**. 

2. **Search** for **IAM**

![](https://lh7-us.googleusercontent.com/I7xdq3Tcq9qF-HsDqbOM-_Wp75_rEB8gMblQ7uKZmJRoqoJIHFD_7WQLQcZjHNC72cxIbNUYpNlXjJEDH8IGH1KgmxjUo_JIfiMTcGC3HbNsVuGNoHfm0pDHvWv6xnhc094ndgT1DMfydmTKciSwt38)

3. **Select Users**

4. **Select** our **user** we **created earlier**

5. **Select Security credentials**

6. **Select Create access key** 

7. **Select Command Line Interface** and **tick I understand…** 

![](https://lh7-us.googleusercontent.com/T0zljpY6o7CiI156deswZTwOWLGh4xDaOdvJNnTnRCVQqiL7zApEtFq40jwvQHlHXefqwDrV7vGfm57LQkRDj4wU5hcCauREAGy-nuOL_xpjf-MzyQ8nbxD5IaVCVGnYeYtqXnXhywar2ySqsEDA-a8)

8. **Click Next**

9. Optionally enter a description and **Click Create access key**

10. No need to download this time. Just **click done**

11. **Click Continue** on the **without viewing or** **downloading** 

****![](https://lh7-us.googleusercontent.com/bSeUDLlnWddxnUsdlPvbwDD8ideUe-qSRurJ0col9z2kTZEvepVBjIQm9m9cP-qgxXcELbytGLg9AsTsYlSOk7E7_uw7B3Z4bPMx0pTue3hasNX0IwH4ozs3JVMk_ilkXF0eoADMOqfR_mT4YdmIsoc)****

12. Look at your access keys. You should have two now. 

13. Find the newly created one (timestamp of created NOW) select Actions Delete

![](https://lh7-us.googleusercontent.com/YntMoh_H10aYWI6qw3WqCuMzQ7bk43tEq2qa2M5yshMmqYiVZ-wDavq80j5lF5DdWiDsLShHKWSin52FbZYuEEhfMClkTqPVdwSe-oI02l-C_UHho35oQXLIU4Oe3C42RqjRpDTkUZnJZmf0999XPNc)

14. **Click Deactivate**

![](https://lh7-us.googleusercontent.com/VYjDNzrA9UTeoxtjs2iFx91PXdlWZys0TIsBVLiQahTrWMp05Fy5tekGnI0ZC7RRnryPsS6NHNJg7IuzZRfKe4tHu8xrmVT6qQUWto1qAm-P5G3wttxKCMlyuMhYvAZ4Ljnem40E8AnCA6BpqWSv4Vc)

 

15. **Paste** in the **required field** and **select delete** (MAKE sure you are deleting the right one!!)![](https://lh7-us.googleusercontent.com/ggs7XkuNSlX6uCPeVcJEEllYe0IIA5ymNQsmo6RfpXcTkPwrsE5DqGil9xZpOFd91jamnrDVp88_5JiTsU1wYghej8JH-wXJR0Fjqjomv2BvKjshyZ4sD-jMUseJpIk4xxNqu5GDEEzBVZ0u5j4Avsk)

**Note: This should generate some management API traffic for cloudtrail data to S3**

16. From your Splunk console wait about 2 or 3 minutes and then re-run your search from before

 index=”\<your index name>” 

Not seeing anything like this still after a few minutes? Try the next section on debug. 

![](https://lh7-us.googleusercontent.com/DivQtBXA3z96eIUSNFH7AN1pGXrRe8qnEAD-9JMLbbCieIFNsCBQ3MwdehLh1MD_Hx5EXChDj7ItoxW7KuWJNNKvuA04XsWRREuMEpn4hI1IaVYBbPgBYViIOlJZxReXR8VPOFXq9a3WJ6RQccaGGW0)


## Tips and Tricks to Debug

Starting back in reverse, let's check AWS first! 


### AWS

Check 1: S3 bucket has data

1. From your AWS Console **Search** for and **select S3**

2. **Select** the **S3 bucket** you created for your lab

3. **Check inside the bucket** that there is **fresh data going inside** the **bucket**

4. If no data at all then there is a problem with your CloudTrail data not sending events to S3

![](https://lh7-us.googleusercontent.com/0DSSEl9OSDRQt6wD-u7t1nMcHOW91zqwVoxXstJ_81qbMrAM97XZ5RFY72G--5NFqPU7dwbAX6n46uzlADp-hyJeYZxvLchquqUgUnmrSn6aby3Xl2H9D18sfY-k3k2WzFDSaxS5lHZ3oyrw_msC1zE)

Check 2: SQS queue

1. From your AWS Console **search** for and **select SQS**

2. Have a look at the **main SQS screen** to see if there are messages **in flight** or **available**

**Note: messages in flight means someone (ie Splunk) has read a message but hasn’t deleted it from the queue yet. So it’s marked temporarily invisible until the timer expires or the message is deleted. If it expires then it goes back into the available queue**![](https://lh7-us.googleusercontent.com/ggs7XkuNSlX6uCPeVcJEEllYe0IIA5ymNQsmo6RfpXcTkPwrsE5DqGil9xZpOFd91jamnrDVp88_5JiTsU1wYghej8JH-wXJR0Fjqjomv2BvKjshyZ4sD-jMUseJpIk4xxNqu5GDEEzBVZ0u5j4Avsk)

3. If **nothing** in the **queue** at all then perhaps **S3** is **not loading data** or not **able to write to SQS**

4. **Re-check** the **access policy tab** for **your SQS queue** that it looks correct. If this is not correct then your S3 bucket won’t be able to write messages to it. 


### Splunk

Check 1

1. **Login** to **Splunk**

2. **Click** the **Splunk Cloud logo**

3. **Click** the **Search and Reporting App**

4. Try the following SPL in the search box to see the input in action 

index=\_internal aws  sourcetype="aws:sqsbaseds3:log"

Check 2

1. **Select** your **Splunk Cloud Logo**

2. **Select** the **AWS add-on** from the list

3. **Select** the **debug tab** and **enable debug** for **SQS based S3**

4. **Click save**

5. **Retry** the **search above** to see if more **detailed logging** helps
