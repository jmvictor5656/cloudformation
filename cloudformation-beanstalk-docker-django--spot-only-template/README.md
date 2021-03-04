# Cloudformation Beanstalk template


## Usage

Current template is for deploying docker based webapp via elastic beanstalk but is configurable for other formats as well like python/go/.net (all those which are supported by elastic beanstalk)

# usage for Django
for Django starter there is a Docker image which can be used as it is and ALLOWED_HOSTS = ["*"] in settings.py.
After creating Docker Image in DockerHub just update `Name` in `Dockerrun.aws.json` with public image.

# For others
run command in terminal `aws elasticbeanstalk list-available-solution-stacks`
and fill `SolutionStackName` based on your application type in `SolutionStackName` in source.yaml(cloudformation) template.

And in the end while deploying template you have to mention bucker & key/path of your application in s3.

# For Deployment
Use either cli/aws ui and pass the required parameters.

# Default Values:
- Current template has been designed for a single spot instance just for cost effective purpose but it's a good habit to use at least one ondemand instance and 
- And currently only t3.small has been added in default values in Allowed type, you can add more based on your requirement.
- EnableSpotParameter: if you pass false then ondemand instance will be launched.
- MaxInstanceParameter value is used by auto scaling group and currently has maximum of 3 instance if you need more just update MaxValue of it.
