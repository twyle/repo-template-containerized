# A Template For Deploying Flask app to EC2 Using Docker.

> This flask application enables an admin to register then authorizes them to create new users.

<p align="center">
  <img title="Bandit badge" alt="Bandit badge" src="https://github.com/twyle/repo-template-containerized/actions/workflows/feature-development-workflow.yml/badge.svg" />
  <img title="Bandit badge" alt="Bandit badge" src="https://github.com/twyle/repo-template-containerized/actions/workflows/development-workflow.yml/badge.svg" />
  <img title="Bandit badge" alt="Bandit badge" src="https://github.com/twyle/repo-template-containerized/actions/workflows/staging-workflow.yml/badge.svg" />
  <img title="Bandit badge" alt="Bandit badge" src="https://github.com/twyle/repo-template-containerized/actions/workflows/release-workflow.yml/badge.svg" />
  <img title="Bandit badge" alt="Bandit badge" src="https://github.com/twyle/repo-template-containerized/actions/workflows/production-workflow.yml/badge.svg" />
  <img title="Bandit badge" alt="Bandit badge" src="https://img.shields.io/badge/security-bandit-yellow.svg" />
  <img title="Bandit badge" alt="Bandit badge" src="https://img.shields.io/badge/%20imports-isort-%231674b1?style=flat&labelColor=ef8336" />
  <img title="Bandit badge" alt="Bandit badge" src="https://img.shields.io/badge/Made%20with- Python-1f425f.svg" />
  <img title="Bandit badge" alt="Bandit badge" src="https://img.shields.io/github/license/Naereen/StrapDown.js.svg" />
  <img title="Bandit badge" alt="Bandit badge" src="https://img.shields.io/badge/Medium-12100E?style=flat&logo=medium&logoColor=white" />
  <img title="Bandit badge" alt="Bandit badge" src="https://img.shields.io/badge/github%20actions-%232671E5.svg?style=flat&logo=githubactions&logoColor=white" />
  <img title="Bandit badge" alt="Bandit badge" src="https://img.shields.io/badge/flask-%23000.svg?style=flat&logo=flask&logoColor=white" />
  <img title="Bandit badge" alt="Bandit badge" src="https://img.shields.io/badge/Visual%20Studio%20Code-0078d7.svg?style=flat&logo=visual-studio-code&logoColor=white" />
  <img title="Bandit badge" alt="Bandit badge" src="https://img.shields.io/badge/Ubuntu-E95420?style=flat&logo=ubuntu&logoColor=white" />
  <img title="Bandit badge" alt="Bandit badge" src="https://img.shields.io/badge/gunicorn-%298729.svg?style=flat&logo=gunicorn&logoColor=white" />
</p>

![](resources/images/header.jpg)

## Project Overview

This is a User managementsystem that enables an admin user to register and then authorizes them to create other non-admin users. The admin registers using a unique email address and user then has to confirm their account via a link sent to their email. Once their account is confirmed,they can then log into the application, upon which they receive an authorization token. Using this token, the admin can then create other non-admin users.

## Working

It's pretty easy to use the application. On the home page (http://localhost:5000/apidocs):

 1. Register as an admin, using a unique email address, unique name and a password.
 2. Head over to the email address that you provided and click on the confirmation link.
 3. At the application home page, log in with the email address and password, to get back a token.
 4. Use the token, to authorize the user.
 5. Make requests to the user routes to create, update, view or delete a user.

Here's a video showing how to use the application:

<p align=center>
  <img width=400 src="resources/videos/register-admin.gif" />
  <img width=400 src="resources/videos/login-admin.gif" />
</p>

<p align=center>
  <img width=400 src="resources/videos/authorize-admin.gif" />
  <img width=400 src="resources/videos/create-user.gif" />
</p>

## Features

This application has several features including:
 1. Deployed to an AWS Instance using docker and a custom domain name.
 2. Versioned using Git and Hosted on GitHub.
 3. Auto-deployed to AWS using GitHub Actions.
 4. Uses gunicorn as the application server and traefik as the proxy.
 5. Uses AWS SES to send emails.
 6. Uses AWS Opensearch and Firehose for logging as well as filebeats.
 7. Uses AWS Secrets manager to manage the application secrets and AWS KMS for key management.
 8. Uses a containerized PostgreSQL instnace for data storage.
 9. Uses JSON Web Tokens to authorize users.
 10. Uses AWS Route53 to route traffic to the application.
 11. Built using flask, flask-mail, flask-jwt
 12. Documented using swagger

## Application Structure

```sh
repo-template-containerized/
???
????????????.github/
???     ???
???     ????????????workflows/
|             |
|             ????????????feature-development-workflow.yml
|             |
|             ????????????development-workflow.yml
|             |
|             ????????????staging-workflow.yml
|             |
|             ????????????release-workflow.yml
|             |
|             ????????????production-workflow.yml
???
????????????resources/
???     |
???     ????????????images/
???     |     |
|     |     ????????????header.jpg
|     ????????????videos/
|           |
|           ????????????header.gif
|
????????????services/
???     |
???     ????????????database/
???     |     |
|     |     ????????????.env
|     |     |
|     |     ????????????database-compose.yml
|     |
???     ????????????traefik/
???     |     |
|     |     ????????????Dockerfile.traefik.dev
|     |     |
|     |     ????????????Dockerfile.traefik.prod
|     |     |
|     |     ????????????traefik.dev.toml
|     |     |
|     |     ????????????traefik.prod.toml
|     |
|     ????????????web/
|           |
|           ????????????api/
|           |    |
|           |    ????????????blueprints/
|           |    |
|           |    ????????????config
|           |
|           ????????????tests/
|           |
|           ????????????.env
|           |
|           ????????????Dockerfile.dev
|           |
|           ????????????Dockerfile.prod
|           |
|           ????????????manage.py
|           |
|           ????????????requirements.txt
|
????????????.gitignore
|
????????????.pre-commit-config.yaml
|
????????????.pylintrc
|
????????????docker-compose-dev.yml
|
????????????docker-compose-prod.yml
|
????????????LICENSE
|
????????????Makefile
|
????????????pytest.ini
|
????????????README.md
|
????????????requirements-dev.txt
|
????????????setup.cfg
```

* **repo-template/.github/workflows** </br>
  *Holds the GitHub Action workflow files.*

* **repo-template/resources** </br>
  *Holds the resources used to describe this project.*

* **repo-template/services/database** </br>
  *Holds the database compose file and the database environment variables.*

* **repo-template/services/web** </br>
  *Holds the web application.*

* **repo-template/services/web/api** </br>
  *Holds the api code*

* **repo-template/services/web/api/config** </br>
  *Holds the application configuration.*

* **repo-template/services/web/api/blueprints** </br>
  *Holds the flask blueprints.*

* **repo-template/services/web/api/blueprints/default** </br>
  *Holds the default blueprint.*

* **repo-template/services/web/tests** </br>
  *Holds the api tests.*

## Local Setup

Here is how to set up the application locally:

  1. Clone the application repo:</br>

      ```sh
      git clone https://github.com/twyle/repo-template-containerized.git
      ```

  2. Navigate into the cloned repo:

      ```sh
      cd repo-template-containerized
      ```

  3. Create a Virtual environment:

      ```sh
      python3 -m venv venv
      ```

  4. Activate the virtual environmnet:

      ```sh
      source venv/bin/activate
      ```

  5. Install the project dependancies:

      ```sh
      make update # update the package manager
      make install-dev  # install the development requirements
      make install  # install the runtime requirements
      make pre-commit # initialize pre-commit
      ```

  6. Create the environment variables:

      ```sh
      cd services/web
      touch .env
      ```

      Then paste the following into the file:

      ```sh
        SECRET_KEY=supersecretkey

        POSTGRES_HOST=<YOUR-IP-ADDRESS>
        POSTGRES_DB=lyle
        POSTGRES_PORT=5432
        POSTGRES_USER=postgres
        POSTGRES_PASSWORD=lyle

        MAIL_HOST=<YOUR-MAIL-HOST>
        MAIL_PORT=<YOUR-MAIL-PORT>
        MAIL_USERNAME=<YOUR-USER-NAME>
        MAIL_PASSWORD=<YOUR-PASSWORD>

        FIREHOSE_DELIVERY_STREAM=flask-logging-firehose-stream

        AWS_KEY=<YOUR-AWS-KEY>
        AWS_SECRET=<YOUR-AWS-SECRET>
        AWS_REGION=<YOUR-AWS-REGION>
      ```

      Then create the database secrets:

      ```sh
      cd services/database
      touch .env
      ```

      Then paste the following into the file:

      ```sh
        POSTGRES_DB=lyle
        POSTGRES_PORT=5432
        POSTGRES_USER=postgres
        POSTGRES_PASSWORD=lyle
      ```

  7. Start the database containers:

      ```sh
      make start-db-containers
      make create-db
      make seed-db
      ```

  8. Start the application:

      ```sh
      make run-dev
      ```

  9. View the running application

      Head over to flask.localhost/apidocs

## Development

 #### 1. Application Design

  1. **Database**

      The database was designed to store the Admin details as well as the users details. These are stored in the tables admin and users.

  2. **Routes**

      Here are the application routes:

      | Route       | Method      | Description      |
      | ----------- | ----------- |----------------- |
      | '/'         | GET         | Get the home page |
      | '/user'     | GET         | Get a single user by supplying an ID |
      | '/user'     | POST        | Create a new user by supplying the email address |
      | '/user'     | PUT         | Update a single user's data by supplying the user ID and email address |
      | '/user'     | DELETE      | Delete a single user by supplying the users ID |
      | '/users'    | GET         | Get the list of all created users |
      | '/auth/register'     | POST         | Register a new admin. |
      | '/auth/login'     | POST         | Login a registered admin to get an access token. |
      | '/auth/me'     | GET         | Get a logged in admins data. |
      | '/auth/me'     | PUT         | Update a logged in admins data. |
      | '/auth/me'     | DELETE      | Delete a logged in admins data. |
      | '/auth/admins'     | GET         | Get all logged in admins data. |

  3. **Logging**

      The application logs to the standard output as well as to AWS OpnSearch using AWS Firehose. Both logging options use custom loggers.

  4. **Security**

      The application uses JSON Web Tokens to authorize access to protected routes. The passwords are also encrypted.

 #### 2. Project Management

   1. **Coding standards** </br>

      The application had to adhere to the following coding standards:
      1. Variable names
      2. Function names
      3. Test driven development
      4. Individual modules need 60% coverage and an overall coverage of 60%.
      5. CI/CD pipeline has to pass before deployments.
      6. Commit messages format has to be adhered to.
      7. Only push code to github using development branches.
      8. Releases have to be tagged.
      9. Use pre-commit to run code quality checks
      10. Use comitizen to format commit messages

   2. **Application development process management** </br>

      The project uses JIRA for management.

 #### 3. Development Workflow

 The application uses atleast 5 branches:

  1. Features branch used to develop new features.
  2. Development branch used to hold the most upto date features that are yet to be deployed.
  3. Staging branch holds the code that is currently being tested for production.
  4. The release branch holds all the assets used when creating a release.
  5. The production branch holds the code for the currently deployed application.

The development workflow follows the following steps:

  1. A feature branch is created for the development of a new feature.
  2. The code is then pushed to GitHub, triggering the feature-development-workflow.yml workflow. If all the tests pass, the feature is reviewde and merged into the development branch.
  3. The code in the development branch is then deployed to the development environment. If the deployment is succesful, the development branch is merged into the staging branch.
  4. This triggers the staging workflow. If all the tests are succesful, this branch is reviewed and deployed to a staging environment.
  5. For creatinga release, the staging branch is merged into the release branch. This happens when a tag is pushed to GitHub.
  6. Once a release is created, the release branch is merged into the production branch, which is deployed into production.

The workflows require a couple of secrets to work:

      ```sh
        FLASK_APP=api/__init__.py
        FLASK_ENV=development

        SECRET_KEY=supersecretkey

        POSTGRES_HOST=<YOUR-IP-ADDRESS>
        POSTGRES_DB=lyle
        POSTGRES_PORT=5432
        POSTGRES_USER=postgres
        POSTGRES_PASSWORD=lyle

        MAIL_HOST=<YOUR-MAIL-HOST>
        MAIL_PORT=<YOUR-MAIL-PORT>
        MAIL_USERNAME=<YOUR-USER-NAME>
        MAIL_PASSWORD=<YOUR-PASSWORD>

        FIREHOSE_DELIVERY_STREAM=flask-logging-firehose-stream

        AWS_KEY=<YOUR-AWS-KEY>
        AWS_SECRET=<YOUR-AWS-SECRET>
        AWS_REGION=<YOUR-AWS-REGION>

        HOST_IP=<AWS-EC2-STATIC-IP>
        AWS_PRIVATE_KEY=<AWS-PRIVATE-KEY>
        APP_DIR=/home/user/repo-template
        USER_NAME=user
        USER_PASSWORD=userpassword
        SERVICE_NAME=gunicorn
      ```

The workflows also require the followingenvironments to work:

  1. Test
  2. Staging
  3. Development
  4. Production

And within each environment, create a secret that indicates the environment type i.e

  1. Test -> ```FLASK_ENV=test```
  2. Staging -> ```FLASK_ENV=stage```
  3. Development -> ```FLASK_ENV=development```
  4. Production -> ```FLASK_ENV=production```

## Deployment

The deployemt process for this application can be divided into two groups:

 * Initial Deployment
 * Incremental deployment

The initial deployment describes the first dployment to the AWS EC2 instance. The process involves the following steps:

 1. **Setting up an AWS EC2 instance**

    This involves the following steps:

      1. Provide an AWS EC2 instance, with latest Ubuntu version and ssh into then instance

          ```sh
          ssh -i "ec2.pem" ubuntu@ec2-xx-206-xx-100.compute-1.amazonaws.com
          ```

      2. Update and upgrade the packages

          ```sh
          sudo apt update && sudo apt upgrade -y
          ```

      3. Install docker and docker compose

          Follow these instaructions from Digital Ocean on [How To Install and Use Docker on Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-22-04)

          Then install docker compose:

          ```sh
          sudo apt install docker-compose -y
          ```

      4. Create a new user, and give them admin access and enable them to use docker.

          ```sh
          sudo adduser lyle
          sudo usermod -aG sudo ${USER}
          sudo usermod -aG docker ${USER}
          ```

      5. Enable ssh into the created user account

          ```sh
           sudo su - lyle
           mkdir .ssh
           chmod 700 .ssh
           touch .ssh/authorized_keys
           chmod 600 .ssh/authorized_keys
          ```

          Retrieve the public key from the private key:

          ```sh
          ssh-keygen -y -f ec2.pem
          ```

          copy and paste into the .ssh/authorized_keys file

      6. Create an elastic IP for the EC2 instance.

 2. **Cloning the project**

      Clone the development branch of the project into the server. Make sure that you are logged in as the created user.

      ```sh
      ssh -i "ec2.pem" lyle@ec2-xx-206-xx-100.compute-1.amazonaws.com
      git clone repo-template-containerized
      ```

 3. **Setting up the application**

      This involves the following steps:

      1. Navigate into the cloned application folder

        ```sh
        cd repo-template-ec2/services/web
        ```

      2. Create the project secrets

        ```sh
        touch services/database/.env
        nano services/database/.env
        ```

        Then add the database secrets.

        Then create the apps secrets:

        ```sh
        touch services/web/.env
        nano services/web/.env
        ```

      3. Start the database containers.

        ```sh
        sudo docker-compose -f services/database/database-compose.yml up --build -d
        ```

      4. Create the database tables

        ```sh
        cd services/web
        sudo apt install python3-pip python3-venv -y
        python3 -m venv venv
        source venv/bin/activate
        pip install -r requirements.txt
        python manage.py create_db
        python manage.py seed_db

 4. **Setting up the application domain**

      Purchase a domain name then use Route53 to create a hosted zone.

 5. **Setting up the application server with the domain**

      This is done for you by traefik.

 6. **Launching the application**

      Restart the application container:

      ```sh
      sudo docker-compose -f docker-compose-prod.yml up -d
      ```

 7. **Setting up Logging**

      This involves creating a FirehoseDeliveryStream as well as AWS OpenSearch.

      Once the application is up and running, you can view the logs by heading over to the OpenSearch dashboard. Here is a video showing some logs:

      ![](resources/videos/logging.gif)

The incremental deployment describes the process of deploying new changes to the already deployed application. It involves the following steps:

 1. Tunelling into the deployment server
 2. Pulling the latest changes
 3. Running database migrations
 4. Restarting the application

This is handled using GitHub Actions:

```sh
  DeployDev:
    name: Deploy to Dev
    # if: github.event_name == 'pull_request'
    needs: [Test-Local]
    runs-on: ubuntu-latest
    environment:
      name: Development

    steps:

      - name: Deploy
        run: echo I am deploying the api to AWS

      - name: Deploy in EC2
        env:
          PRIVATE_KEY: ${{ secrets.AWS_PRIVATE_KEY  }}
          HOST_NAME : ${{ secrets.HOST_NAME  }}
          USER_NAME : ${{ secrets.USER_NAME  }}
          USER_PASSWORD: ${{ secrets.USER_PASSWORD }}
          APP_DIR: ${{secrets.APP_DIR}}

        run: |
          echo "$PRIVATE_KEY" > private_key && chmod 600 private_key
          ssh -o StrictHostKeyChecking=no -i private_key ${USER_NAME}@${HOST_NAME} "
            cd ${APP_DIR} &&
            git pull &&
            echo ${USER_PASSWORD} | sudo -S docker-compose -f docker-compose-prod.yml up --build -d "
```

## Releases

## v0.1.0 (2022-07-14)

### Fix

- fixes the release badge url.
- updates the dockerfile path.
- only restarts the container.
- uses the right docker compose file.

### Feat

- auto-deploy to AWS.
- adds the traefik config.
- creates the initial project layout.

## v0.0.1 (2022-07-14)

## Contribution

1. Fork it https://github.com/twyle/repo-template/fork
2. Create your feature branch (`git checkout -b feature/fooBar`)
3. Commit your changes (`git commit -am 'Add some fooBar'`)
4. Push to the branch (`git push origin feature/fooBar`)
5. Create a new Pull Request

## Developer

Lyle Okoth ??? [@lylethedesigner](https://twitter.com/lylethedesigner) on twitter </br>

[lyle okoth](https://medium.com/@lyle-okoth) on medium </br>

My email is lyceokoth@gmail.com </br>

Here is my [GitHub Profile](https://github.com/twyle/)

You can also find me on [LinkedIN](https://www.linkedin.com/feed/)

## License

Distributed under the MIT license. See ``LICENSE`` for more information.
