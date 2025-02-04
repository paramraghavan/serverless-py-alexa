# Alexa python sdk
- https://developer.amazon.com/en-US/docs/alexa/alexa-skills-kit-sdk-for-python/set-up-the-sdk.html
- https://medium.com/analytics-vidhya/basics-for-developing-a-custom-alexa-skill-with-aws-lambda-as-backend-5ac115c2919
- https://dzone.com/articles/alexa-skill-with-python
# Alexa json request/response
- https://developer.amazon.com/en-US/docs/alexa/custom-skills/request-and-response-json-reference.html#response-format


# Reference
## https://www.serverless.com/blog/how-to-manage-your-alexa-skills-with-serverless - original
## https://rupakganguly.com/posts/how-to-build-a-serverless-alexa-skill/

# Pre-requisites:
## 1. aws.amazon.com --> amazon aws account - to deploy aws lambda - all the logic goes in the lambda
## 2. developer.amazon.com account
### Developer Console
#### Dashboard
##### Alexa Skills Kit

## 3. Install Serverless
### install *serverless framework* - https://www.serverless.com/framework/docs/providers/aws/guide/quick-start/
### Install *node*, my node version v14.15.5. https://nodejs.org/dist/v14.17.0/node-v14.17.0-x64.msi
### npm install -g serverless

# The following is needed when pull the project from git repo the very first time. Creates the node modules for alexa calls 
### sls plugin install -n serverless-alexa-skills 
### pycharm community edition or visual source code or spyder
### git bash
### Download backup and sync, https://www.google.com/drive/download/
### install aws cli --> https://awscli.amazonaws.com/AWSCLIV2.msi
### mac https://awscli.amazonaws.com/AWSCLIV2.pkg

### Install python 3.8
### Virtual Env
#### Virtual env --> https://uoa-eresearch.github.io/eresearch-cookbook/recipe/2014/11/26/python-virtual-env/
    py -m pip install virtualenv or python -m pip install virtualenv
#### create venv --> virtualenv venv --python=python3

### pip install -r requirements.txt

# Create requirements.txt
- pip freeze > requirements.txt


# login into developer.amazon.com - needed to create and sync-up the skill, the models and intents - updated
# once the models are updated perform the build
# u can view the models by using --> sls alex models
# in the serverless.yml
cd alexa\pp-aws-python-alexa-skill\auth-yml
sls alexa auth
## Note
- The security token expires in 1 hour. Therefore, if an authentication error occurs, please re-execute the command

# cd alexa\pp-aws-python-alexa-skill
# Create SKill and Interaction Model, creation of the skil is done hte very first time only.
- sls alexa create --name LuckyNumber --locale en-US --type custom
# create manifests and update with skill
- sls alexa manifests

# set the environment variables, once u login into developer.amazon.com, set the following details
# in file config/env_dev.json
AMAZON_VENDOR_ID=XXXXXXXXXXXXXXXXXX
AMAZON_CLIENT_ID=amzn1.application-oa2-client.ewewew22324343ml343r33535
AMAZON_CLIENT_SECRET=23232333333333333333333333333333333333333333333333333333333333
ALEXA_SKILL_ID=amzn1.ask.skill.sewewewe-2222-2345-34356-2323222321
AWS_ACCOUNT=XXXXXXXXXXXXXX

# Add intents to the model. Update(save the model) and build the model
sls alexa update
# --dryrun, use this to check your intent syntax
sls alexa --dryrun
sls alexa update

#build model
sls alexa build

#see the model created
sls alexa models 

# Create Endpoint, this has all our logic what to do when a invocation and intents  calls are made 
# deploys lambda endpoint
# to deploy and remove lambda you need to setup credentials token
# configure credentials token, make sure u have an aws user created with appropriate permissions 
# on aws
aws configure list
https://www.serverless.com/framework/docs/providers/aws/guide/credentials/
aws configure --profile slsflaskapp
aws configure list-profiles
serverless deploy -v --stage dev
# removes the deployed lambda endpoint
serverless remove -v --stage dev

# Ask alexa
Alexa ask good ducky whats my lucky number
Alexa ask good ducky whats my lucky number lower than 10
Alexa ask good ducky whats my lucky number under 10
## Next intent 
- hack for today
- share a hack
- today's hack

#testing lambda

## serverless invoke --function lucky_number_handler.lucky_number --path C:\Users\padma\serverless\alexa\pp-aws-python-alexa-skill\help\sample_inut.json
## pip install pytest

#You can view the AWS CloudWatch logs from the terminal by running:
# did not work for me.
sls logs -f luckyNumber

#delete alexa skill
 sls alexa delete --id <skill_id>
 sls alexa delete --id amzn1.ask.skill.8e995b14-65b9-4691-965d-1a7a0231944d


Notes to discuss:
Life cycle of a skill
https://stackoverflow.com/questions/5578270/fully-backup-a-git-repo#:~:text=Option%201%3A%20use%20git%20bundle,full%20file%20backup%20of%20mirror.

#Git
## Git (/ɡɪt/)[7] is software for tracking changes in any set of files, usually used for coordinating 
## work among programmers collaboratively developing source code during software development. 
## Its goals include speed, data integrity, and support for distributed, non-linear workflows 
## (thousands of parallel branches running on different systems). -- see web for more details


# Install google drive for windows  or mac - this is to map google drive as you local drive on laptop or pc.
# make mirror copy of git from onedrive to google drive
https://stackoverflow.com/questions/5578270/fully-backup-a-git-repo#:~:text=Option%201%3A%20use%20git%20bundle,full%20file%20backup%20of%20mirror
Git clone mirror will clone the entire repository, notes, heads, refs, etc. and is typically used to copy an entire repository to a new git server. 
This will pull down an all branches and everything, the entire repository.
# git clone --mirror git@example.com/your-repo.git

$ cd /c/Users/padma/Google Drive/git-repo
$ git clone --mirror ~/OneDrive/git_repo/pp-aws-python-alexa-skill
Cloning into bare repository 'pp-aws-python-alexa-skill.git'...
done.

# We will clone from  google drive
git clone ~/Google\ Drive/git-repo/pp-aws-python-alexa-skill.git/
git clone ~/Google\ Drive/git-repo/py-learn.git/

#ALEXA-REPO
git clone --mirror ~/Google\ Drive/git-repo/pp-aws-python-alexa-skill.git/
git clone --mirror ~/Google\ Drive/git-repo/py-learn.git/

# We will clone from  google drive
git clone ~/OneDrive/ALEXA-REPO/pp-aws-python-alexa-skill.git/
git clone ~/OneDrive/ALEXA-REPO/py-learn.git/

# Note
Repo's on Ondrive and Google drive cannot be shared with others, hence checking into to github

# how to find git repository url for my current project
git remote show origin

# ASK-CLI
# ASK SDK python
# Sample skill code
https://developer.amazon.com/en-US/docs/alexa/alexa-skills-kit-sdk-for-python/sample-skills.html
https://developer.amazon.com/en-US/docs/alexa/smapi/quick-start-alexa-skills-kit-command-line-interface.html
npm install -g ask-cli
ask configure

#Add more users developer.amazon.com
Login and navigate to Settings and then User Permissions. 
There click 'Add New' and add the email address of a registered user 
and assign them to a role: Developer, Administrator, Marketer, Analyst. 
Administrator has full access, while other roles are more restricted 
(developer can upload binaries, analyst can view reports,

Rest API Click if Sick
-------------------------
https://awscli.amazonaws.com/AWSCLIV2.pkg