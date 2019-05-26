# Prepare your development environment

## 1. Create Cloud9 instance for development

1.1\. Open the AWS Cloud9 console at https://console.aws.amazon.com/cloud9/.

1.2\. Click on **Create environment**.

![Cloud9 Create environment](images/cloud9-create.png)

1.3\. For the **Name** type `MyDevEnv`, and choose **Next step**.

![Cloud9 name environment](images/cloud9-name.png)

1.4\. For the **Environment settings** use the default values and choose **Next step**.

1.5\. Click on **Create environment**.

1.6\. Wait a few seconds until your development environment is ready, you will see the following screen.

![Cloud9 Env](images/cloud9-env.png)

## 2. Install requirements

2.1\. Inside the Cloud9 environment, in the **bash** terminal, execute the following command to clone the project repository.

``` bash
git clone https://github.com/aurbac/nodejs-back-and-angular-front.git
```

2.2\. Update the nodejs to version 8.

``` bash
nvm i v8
```

2.3\. Install the Angular CLI globally.

``` bash
npm install -g @angular/cli
```

2.4\. The execution of the following commands make sure that service linked roles exist for Load Balancers and ECS, if they do not exist they are created.

``` bash
aws iam get-role --role-name "AWSServiceRoleForElasticLoadBalancing" || aws iam create-service-linked-role --aws-service-name "elasticloadbalancing.amazonaws.com"
aws iam get-role --role-name "AWSServiceRoleForECS" || aws iam create-service-linked-role --aws-service-name "ecs.amazonaws.com"
```