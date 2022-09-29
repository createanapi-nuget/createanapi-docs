New B2B Portal
==============

This section of the documentation details the public API
usable to get details of projects, builds, versions and other details
from Read the Docs.

Template
------------------------------


Pull latest master template
------------------------------

* https://github.com/createanapi-clients/createanapi-template
* Pull the repository to local
* Switch to master branch

![1](https://user-images.githubusercontent.com/6174749/172218418-18d89a35-abcd-4072-af77-76ab05c6dff1.png)



Export projects as a new template
---------------------------------

* Create template from .Net Projects
* https://github.com/createanapi-clients/createanapi-template/tree/master/src/CreateAnAPI.Customer/CreateAnAPI.Portal

![2](https://user-images.githubusercontent.com/6174749/172218438-367549a9-1e64-44dd-8527-92e315150c6b.png)


Local
------------------------------

Create portal solution & project
---------------------------------

* Create a new GitHub repository for customer if does not exist
* Create a new solution for customer if does not exist -> src/{{SOLUTION_NAME}}
* Create a new project from template -> src/{{SOLUTION_NAME}}/{{PROJECT_NAME}}

![3](https://user-images.githubusercontent.com/6174749/172218456-a809847f-8ed1-4f70-946e-d441eff711ef.png)

Create Platform in CreateAnAPI Admin (Production and Staging)
-------------------------------------------------------------

* Create platforms with
* ShortCode
* Solution Name
* Project Name
* Dockerfile Name
* App urls

![4](https://user-images.githubusercontent.com/6174749/172236095-b7d7c2c7-b96d-4648-a325-4e38e7d195ab.png)



Initialize credentials
------------------------------

* Update appconfig with credentials and platform id

![5](https://user-images.githubusercontent.com/6174749/172238753-79e3857e-8c94-4f91-ade7-a4a7e729c36b.png)


Create initial config
------------------------------


![6](https://user-images.githubusercontent.com/6174749/172238773-28b28a0c-961c-44c6-bf4f-279040656d48.png)


Build & Start Project
------------------------------

* Environment should be 'LocalStaging' or 'LocalProduction'
* src/{{SOLUTION_NAME}}/{{PROJECT_NAME}}/Properties/launchSettings.json
* Always use {{PROJECT_NAME}} launch profile, not IISExpress
* Always use https://localhost:5004/

`yarn install`
`yarn start`
`dotnet run`

![7](https://user-images.githubusercontent.com/6174749/172241414-6eaf01b7-ac8e-4a26-b8bc-4c646f4355da.png)


Publish
------------------------------


Initialize AWS
------------------------------


![8](https://user-images.githubusercontent.com/6174749/172241629-74e913c4-a39b-4641-82f4-e9cc2ac204b6.png)



Download Dockerfile, GitHub Actions and Task Definition
-------------------------------------------------------

* /{{DOCKERFILE_NAME}}
* /src/{{SOLUTION_NAME}}/{{PROJECT_NAME}}
* /.github/workflows/{{SHORTCODE}}-github-action-backend.yml
* /.github/workflows/{{SHORTCODE}}-github-action-frontend.yml

Create Staging and Production Route53 Records
-------------------------------------------------------

https://us-east-1.console.aws.amazon.com/route53/home?region=us-east-2#

Publish Staging and Production
------------------------------

https://github.com/createanapi-clients/createanapi-template/actions

![9](https://user-images.githubusercontent.com/6174749/172242575-df7635f6-ab52-4447-a822-aa288c6f5730.png)