docker run -d -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins

# gem
group :test do
  gem "simplecov", require: false
  gem "simplecov-json", require: false
  gem "simplecov-rcov", require: false
end

# spec_helper.rb
require "sunspot/rails/spec_helper"
require "simplecov-json"
require "simplecov-rcov"

SimpleCov.formatters = [
  SimpleCov::Formatter::HTMLFormatter,
  SimpleCov::Formatter::JSONFormatter,
  SimpleCov::Formatter::RcovFormatter
]
SimpleCov.start

$PROJECT_NAME - project name in Jenkins
$ID - Docker container ID

# Login to Docker
docker exec -it $ID bash

# Install Ruby 2.3
rvm install 2.3

# Check
rvm list known

# Install MySQL client
sudo apt-get install libmysqlclient-dev

# Manage Jenkins

## Configure System
### Jenkins Location
- URL: http://$URL:7070/
- System Admin e-mail address: $EMAIL

### GitHub
- GitHub Servers
  - API URL: https://api.github.com
  - Credentials: Personal access token
  - Manage hooks

### Git plugin
- Create new accounts base on author/committer's email

## Plugins
- DocLinks
- RubyMetrics
- embeddable-build-status
- GitHub plugin
- Git plugin
- GIT server Plugin
- GitHub API Plugin
- GitHub Pull Request Builder Plugin

# Project
# Configure
## General
Project name: $PROJECT_NAME

- GitHub project
  - Project url: https://github.com/$USERNAME/$PROJECT_NAME/

## Source Code Management
- Git
- Repository URL: git@github.com:$USERNAME/$PROJECT_NAME.git

## Build Triggers
- Build when a change is pushed to GitHub
- GitHub Pull Request Builder
  - Admin list: romankrasavtsev
  - Use github hooks for build triggering

## Build Environment
- Delete workspace before build starts
- Add timestamps to the Console Output

## Build
- Execute shell
#!/bin/bash
source ~/.bash_profile
cd ~/workspace/$PROJECT_NAME/
bundle install
bundle exec rake db:drop RAILS_ENV=test
bundle exec rake db:create RAILS_ENV=test
bundle exec rake db:schema:load RAILS_ENV=test
bundle exec rake db:migrate RAILS_ENV=test
bundle exec rspec spec
bundle exec rubocop

## Post-build Actions
- Publish documents
  - Title: Coverage report
  - Directory to archive: coverage
  - Archive recursively
  - Index file: index.html

If you have an error "java.lang.NoClassDefFoundError: hudson/maven/Maven Module", you have to install "Maven Integration plugin"

- Publish Rcov Report
  - Rcov report directory: coverage/rcov

- Set build status on GitHub commit post-build action

# Download the latest version
cd /usr/share/jenkins
sudo mv jenkins.war jenkins_old.war
sudo wget http://mirrors.jenkins.io/war/latest/jenkins.war

# Safe restart
URL/safeRestart
