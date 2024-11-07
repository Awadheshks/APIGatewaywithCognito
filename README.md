# Secure your API Gateway with Amazon Cognito User Pools
![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/Splashscreen.png)

## AWS Cognito User pools

An Amazon Cognito user pool is a user directory. With a user pool, your users can sign in to your web or mobile app through Amazon Cognito, or federate through a third-party IdP.
Federated and local users have a user profile in your user pool.Local users are those who signed up or you created directly in your user pool. You can manage and customize these 
user profiles in the AWS Management Console, an AWS SDK, or the AWS Command Line Interface (AWS CLI).

Amazon Cognito user pools accept tokens and assertions from third-party IdPs, and collect the user attributes into a JWT that it issues to your app. You can standardize your app
on one set of JWTs while Amazon Cognito handles the interactions with IdPs, mapping their claims to a central token format.

An Amazon Cognito user pool can be a standalone IdP. Amazon Cognito draws from the OpenID Connect (OIDC) standard to generate JWTs for authentication and authorization. When you sign in local users, your user pool is authoritative for those users. You have access to the following features when you authenticate local users.
  1. Implement your own web front-end that calls the Amazon Cognito user pools API to authenticate, authorize, and manage your users.
  2. Set up multi-factor authentication (MFA) for your users. Amazon Cognito supports time-based one-time password (TOTP) and SMS message MFA.
  3. Secure against access from user accounts that are under malicious control.
  4. Create your own custom multi-step authentication flows.
  5. Look up users in another directory and migrate them to Amazon Cognito.

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/fc3e58ae650551edcd85b559fbacb02ebf5bd5e0/asset/CogUserPool1.png)

With Cognito User Pools, you can provide sign-up and sign-in functionality for your mobile or web app users. You don’t have to build or maintain any server infrastructure on which users will authenticate. 
This diagram shows how authentication is handled with Cognito User Pools:

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/fc3e58ae650551edcd85b559fbacb02ebf5bd5e0/asset/CogUserPool2.png)

1.	Users send authentication requests to Cognito User Pools. 
2.	The Cognito user pool verifies the identity of the user.
3.	The Cognito User Pool Token is sent back to the user. 
4.	The person can then use this token to access your backend APIs hosted on your EC2 clusters or in API Gateway and Lambda.

On the Amazon Cognito User Pool page, you can also manage users to reset the password, disable/enable users, and enroll/delete users or other actions needed for User Management. 

## Let’s start with step by step actions:
### Step1:
Open AWS Management Console, Goto Cognito and create Cognito user pool

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/Userpool.png)


### Step2:
Configure sign-in experience, check Email for Cognito user pool sign-in options and click Next

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/Userpool-Sign-In.png)


### Step3:
Configure security requirements, select “No MFA” , choose all default settings and click Next

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/Userpool-Security.png)


### Step4:
Configure sign-up experience, don’t change anything and go with default selections and Click Next

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/Userpool-Sign-Up.png)


### Step5:
Configure message delivery, select “send email with Cognito” for Email configuration and click Next

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/Userpool-MessageDelivery.png)


### Step6:
Integrate your app- enter User pool name as “MyFirstDemoPool”, for Domain - check for “Use a Cognito domain” as “simplifieddemodomain”, Initial app client as “DemoClient” 

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/Userpool-Domain-Appclient.png)


### Step7:
Fill Allowed callback URL as below and click Next

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/Userpool-Callback.png)
![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/Userpool-AppPool.png)


### Step8:
Let's Review and create

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/Userpool-Review1.png)
![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/Userpool-Review2.png)


### Step9:
And Click “Create user pool”

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/Userpool-CreatePool.png)


### Step10:
Now Go to AppClient and scroll down to app client name

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/AppClient1.png)

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/AppClient2.png)


App client details:

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/AppClient3.png)

### Step11:
Scroll down to Hosted UI tab window and click “View Hosted UI” top open it in browser
![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/Hosted_UI.png)


That brings to basic login page

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/BasicLoginPage.png)


### Step12:
If you are first time user,Sign up be entering your details.
Now Open API Gateway service and create new API through “Create API” , select REST API and build

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/RestAPI1.png)


### Step13:
Create REST APT as “DemoAPI” 

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/CreateRESTAPI.png)


### Step14:
In API Gateway, create resource by entering “Transactions” as resource name

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/RestAPI-CreateResource.png)


### Step15:
Let’s create Lambda function by visiting Lambda Service. Create function as “DemoAppLambda” and leave runtime as “Node.js 20x” and leave the code as it is.

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/CreateFunction.png)
![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/Lambda.png)
![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/Lambda-Code.png)


### Step16:
Now go back to API Gateway and create method by selecting method type as “GET” and integration type as “Lambda function”. Select Lambda function that have created just now

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/APIGateway-ConfigureLambda.png)


### Step17:
Deploy API to be visible for public by creating new stage 

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/DeployAPI.png)


### Step18:
Copy 'Invoke URL' and execute in browser https://syhxhdufb5.execute-api.us-east-1.amazonaws.com/Test 

 ![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/API-Response1.png)
 
 
Add method name like https://syhxhdufb5.execute-api.us-east-1.amazonaws.com/Test/Transactions, you will get successful response

 ![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/API-Response2.png)
 
 
### Step19:
Lets configure 'Authorizers' to API gateway by creating an authorizer

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/Create-Authorizer.png)


### Step20:
Lets go back to app client and update few details of Hosted UI

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/Configure-HostedUI.png)
![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/Configure-HostedUI-1.png)


### Step21:
Now lets click 'view Hosted UI' and open it in any browser.Before filling the credentials,change response_type=’code’ to ‘token’ in URL and extract id_token and access_token from URL
id_token=<xxxxxxxxxxxxxxxxxxxxxxxxxx…..>
access_token=<xxxxxxxxxxxxxxxxxxxxxxxxxx…..>

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/LoginPageURL-Token.png)

Once we have id_token ,lets test Authorizer by entering this value

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/Test-Authorizer.png)


### Step22:
Its time to restrict API to use the user pool yet,go to API Gateway->resources and select GET method and edit the “Method request”

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/IntegrateAuthorizer-API.png)


### Step23:
Now deploy API for new authorizer version.Now if you hit this URL https://syhxhdufb5.execute-api.us-east-1.amazonaws.com/Test/Transactions you can see message as “Unauthorized”

 ![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/Postman-ErrorMessage.png)


### Step24:
We can test API through Postman by using token as 'id_token' and receive successful response.

![image](https://github.com/Awadheshks/APIGatewaywithCognito/blob/c7765e56bfe7848f3c9a12d2b2e04e06cddc3b85/asset/Postman.png)









