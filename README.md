# De factOps

Welcome to the De factOps project! Using the provided docker-compose files, you will be able to generate a server to monitor the devops metrics of your development team. 

This project connects to your existing CI/CD platform as well as your bug-tracker and creates a live dashboard for the Dora 4 keys:

* Lead Time for Changes
* Deployment Frequency
* Change Failure Rate
* Time to Restore Service

# Getting started 
## Requirements

Any server with [Docker](https://www.docker.com/) already installed

## Docker compose

1. Copy both files from the ./docker-compose folder to a folder on your server
2. Fill the .env.client file with the values from your system
    * LICENSE_TOKEN: Create an account on defactops.com and follow the instructions to start a free trial or paid subscription. 
    * POSTGRES_PASSWORD: Make sure to change that one to anything else
    * GITLAB_API_TOKEN: In Gitlab, go to your icon > Preferences > Access Tokens. Add a new token and give it the read_api permission. 
    * From the project you wish to monitor in Gitlab, go to Settings > General. The project ID is available at the top of the page
    * GITLAB_ENVIRONMENT_NAME: This is your "production" environment, from the Operate > Environment section in Gitlab
    * JIRA_TOKEN: In Jira, go to your icon > Profile > Manage your account > Security. From there select "Create API token" and follow the instructions
    * JIRA_FAILURE_LABEL: This is a label to indicate that an issue was found after a release was launched in production. Simply add the label you choose to any issue.
3. Launch the server: \
`docker-compose --file docker-compose-defactops.yml --env-file .env.client`

# Supported platforms

For the moment, only Gitlab and Jira are supported as CI/CD and issue trackers. We are working on adding other platforms, please let us know what would suit your needs.

For any question or comments, contact us at info@defactops.com