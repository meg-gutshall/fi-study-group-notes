# Deploying on Heroku

> **Dwayne Harmon on 07/02/19 & 08/21/19**

To deploy \(from the French _deployer_\) is "to spread out or arrange strategically." ...In its IT context, deployment encompasses all the processes involved in getting new software or hardware up and running properly in its environment, including installation, configuration, running, testing, and making necessary changes.

## The Process

### Assumptions

1. You are deploying a Rails app \([Rails Support](https://devcenter.heroku.com/categories/rails-support)\)
2. Your app is generated with a PostgreSQL database
3. You have a Heroku account \([https://signup.heroku.com/devcenter](https://signup.heroku.com/devcenter)\)

### Next Steps

* Use [Heroku documentation](https://devcenter.heroku.com/articles/getting-started-with-rails5) and _**read every step**_
  * If you miss a step, it won’t work
* Remove the versioning dependencies on `gem ‘pg’` in your `Gemfile`
* Heroku is very picky about the Bundler version your app uses to deploy
  * [Working with Bundler](https://devcenter.heroku.com/categories/working-with-bundler)
* You can run Heroku migrations directly from your terminal
  * [Deploying to Heroku with Git](https://devcenter.heroku.com/articles/git#prerequisites-install-git-and-the-heroku-cli)
* Rails uses `gem 'puma'` to spin up server instances
* Change the command used to launch your web process by creating a file called `Procfile` \(name has to be exact\) in the root of your app
  * We recommend generating a Puma config file based on [our Puma documentation](https://devcenter.heroku.com/articles/deploying-rails-applications-with-the-puma-web-server) for maximum performance
  * In addition to running commands in your `Procfile`, `heroku local` can also help you manage environment variables locally through a `.env` file
* Hosting services like Heroku and Repl.it are for beginner coders to get their feet wet. You should learn how to deploy on other hosting services like AWS, Digital Ocean, Linode, etc.

## **Resources**

### Flatiron Students and Instructors

* [Rails: Changing from sqlite to postgres and uploading to heroku](https://www.youtube.com/watch?v=5d0cDMhtZ4E&feature=youtu.be)
* [Deploying your SQLite3 Sinatra App to Heroku using PostgreSQL](http://lucaskisabeth.com/2017/06/24/deploying_your_sqlite3_sinatra_app_to_heroku_using_postgresql/)
* [I Deployed My Sinatra App To Heroku](https://medium.com/@sethalexander/i-deployed-my-sinatra-app-to-heroku-9c2785a27225)

### Ruby Gems

* [puma](https://github.com/puma/puma)
* [dotenv](https://github.com/bkeepers/dotenv)

