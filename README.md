# Cal on PipeOps

[![Deploy on PipeOps](https://railway.app/button.svg)](https://railway.app/template/0ELOuE?referralCode=IQhE0B)

The open-source Calendly alternative. 


# Getting Started

To get a local copy up and running, please follow these simple steps.
Prerequisites

Here is what you need to be able to run Cal.

    Node.js (Version: >=15.x <17)
    PostgreSQL
    Yarn (recommended)

    If you want to enable any of the available integrations, you may want to obtain additional credentials for each one. More details on this can be found below under the integrations section.


# Development
Setup

    Clone the repo into a public GitHub repository (or fork https://github.com/calcom/cal.com/fork). If you plan to distribute the code, keep the source code public to comply with AGPLv3. To clone in a private repository, acquire a commercial license)
```
    git clone https://github.com/calcom/cal.com.git
```

    Go to the project folder

    cd cal.com

    Install packages with yarn

    yarn

    Set up your .env file
        Duplicate .env.example to .env
        Use openssl rand -base64 32 to generate a key and add it under NEXTAUTH_SECRET in the .env file.
        Use openssl rand -base64 24 to generate a key and add it under CALENDSO_ENCRYPTION_KEY in the .env file.

Quick start with yarn dx

        Requires Docker and Docker Compose to be installed
        Will start a local Postgres instance with a few test users - the credentials will be logged in the console

yarn dx

Development tip

    Add NEXT_PUBLIC_DEBUG=1 anywhere in your .env to get logging information for all the queries and mutations driven by trpc.

echo 'NEXT_PUBLIC_DEBUG=1' >> .env


# Manual setup

    Configure environment variables in the .env file. Replace <user>, <pass>, <db-host>, <db-port> with their applicable values

    DATABASE_URL='postgresql://<user>:<pass>@<db-host>:<db-port>'

    If you don't know how to configure the DATABASE_URL, then follow the steps here to create a quick DB using Heroku

    Set a 32 character random string in your .env file for the CALENDSO_ENCRYPTION_KEY (You can use a command like openssl rand -base64 24 to generate one).

    Set up the database using the Prisma schema (found in packages/prisma/schema.prisma)

    yarn workspace @calcom/prisma db-deploy

    Run (in development mode)

    yarn dev

Setting up your first user

    Open Prisma Studio to look at or modify the database content:

    yarn db-studio

    Click on the User model to add a new user record.

    Fill out the fields email, username, password, and set metadata to empty {} (remembering to encrypt your password with BCrypt) and click Save 1 Record to create your first user.

        New users are set on a TRIAL plan by default. You might want to adjust this behavior to your needs in the packages/prisma/schema.prisma file.

    Open a browser to http://localhost:3000 and login with your just created, first user.
