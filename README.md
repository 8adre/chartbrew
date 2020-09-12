<p align="center">
  <a href="https://chartbrew.com">
    <img src="https://docs.chartbrew.com/assets/logo_full_2.png" alt="ChartBrew logo" width="250"/>
  </a>
</a>

<p align="center">
  <a href="https://circleci.com/gh/chartbrew/chartbrew" target="_blank"><img src="https://circleci.com/gh/chartbrew/chartbrew.svg?style=svg" alt="ChartBrew build" /></a>
  <a href="https://app.codacy.com/gh/chartbrew/chartbrew" target="_blank"><img src="https://api.codacy.com/project/badge/Grade/b245aa07f69c4250a2de9d24efc659e6"></a>
  <a href="https://discord.gg/KwGEbFk" target="_blank"><img src="https://img.shields.io/discord/656557151048957995?label=Discord" alt="" /></a>
</p>

<p align="center">
  <strong>
    <a href="https://chartbrew.com">Chartbrew</a> is an open-source web application that can connect directly to databases and APIs and use the data to create beautiful charts. It features a chart builder, editable dashboards, embedable charts, query & requests editor, and team capabilities.
  </strong>
</p>

<p align="center">
  <a href="https://chartbrew.com">
    <img src="https://docs.chartbrew.com/assets/flat_browser.jpg" alt="ChartBrew logo" width="600"/>
  </a>
</a>

<hr />

📚 [**Read the full docs here**](https://docs.chartbrew.com)

🔧 [**Development roadmap**](https://github.com/orgs/chartbrew/projects/1) - start here if you want to contribute

🚙 [**Public feature roadmap over here**](https://trello.com/b/IQ7eiDqZ/chartbrew-roadmap)

💬 [**Join our Slack workspace**](https://join.slack.com/t/chartbrew/shared_invite/enQtODU3MzYzNTkwOTMwLTZiOTA5YzczODUzZGFiZmQyMGI1ZGVmZGI4YTVmOTBkMTI0YzQ2ZjJjOGI5NzQ0NmNmYzRmMDk3MmY4YmI4MTI)

🤟 [**Join our Discord**](https://discord.gg/KwGEbFk)

## Data sources

Currently, ChartBrew supports connections to these data sources.

* MySQL
* PostgreSQL
* MongoDB
* APIs that support JSON data

## Prerequisites

* Built with NodeJS v12.17.0 (might work with earlier versions)
* NPM
* MySQL v5+ Server running and an empty database to use for Chartbrew

## Start

It is recommended you head over to the more detailed documentation to find out how to set up Chartbrew

[📚 You can find it here](https://docs.chartbrew.com/#getting-started)

## Quickstart

If you already have a MySQL server running, create a database called charbrew and adjust the parameters below with your connection settings. The command will then setup everything for you.

**Important** Windows command line is not supported at the moment. Use something like [Cygwin](http://www.cygwin.com/) on Windows.

```sh
npx create-chartbrew-app myApp --dbname="chartbrew" --dbusername="root" --dbpassword="" --dbhost="localhost"
```

The arguments are optional, but they set the environmental variables needed for the project to run. [Check out which need to be set here.](https://docs.chartbrew.com/#set-up-environmental-variables)

**Run the database migrations**

If the database parameters are correct, the migrations should run automatically. If the new database wasn't populated with tables, ensure all the environmental variables are set, then run the following command in the `server` folder:

```sh
cd server
npm run db:migrate
```

### Run the project in Development

Open two terminals, one for front-end and the other for back-end.

```sh
# frontend
cd client/
npm run start

# backend
cd server/
npm run start-dev
```

## Docker container

### Run docker image

Run the following commands and configure the variables:

```sh
docker pull razvanilin/chartbrew:docker
```

```sh
docker run --rm -p 3210:3210 -p 3000:3000 \
  -e CB_API_HOST=0.0.0.0 \
  -e CB_DB_HOST=host.docker.internal \
  -e CB_DB_NAME=chartbrew \
  -e CB_DB_USERNAME=root \
  -e CB_DB_PASSWORD=password \
  -e REACT_APP_CLIENT_HOST=http://localhost:3000 \
  -e REACT_APP_API_HOST=http://localhost:3210 \
  razvanilin/chartbrew:docker
```
Check `.env-template` in the repository for extra variables for enabling `One account` or mail capabilities.


### Run locally with docker-compose

Open up `.env-template` in the root folder of the project and make sure that the database host var is set to `db` like so:

`CB_DB_HOST=localhost` -> `CB_DB_HOST=db`

Also make sure the other variables are set in a way that suits your setup.

Then run the following commands:

```sh
npm run prepareSettings
docker-compose up
```

For more information on how to configure, modify and deploy ChartBrew, [**read the full docs here**](https://docs.chartbrew.com)

## Acknowledgements

Many thanks to [everybody that contributed](https://github.com/chartbrew/chartbrew/graphs/contributors) to this open-source project 🙏

[Start here if you want to become a contributor](https://github.com/chartbrew/chartbrew/blob/master/CONTRIBUTING.md)