# Tracker::Git

Update Pivotal Tracker depending on your local Git repository.

This gem finds all finished stories and bugs and if it finds the story id in a Git commit, marks that story as delivery.

This has proved useful as part of a 'deploy to staging' strategy. If you automatically deploy to a staging environment after a successful continuous integration build, and want to update a story from 'finished' to 'delivered', then this Gem is for you.

## CI

[![Build Status](https://secure.travis-ci.org/robb1e/tracker-git.png)](http://travis-ci.org/robb1e/tracker-git)
[![Code Climate](https://codeclimate.com/badge.png)](https://codeclimate.com/github/robb1e/tracker-git)
[![Dependency Status](https://gemnasium.com/robb1e/tracker-git.png)](https://gemnasium.com/robb1e/tracker-git)

## Installation

Add this line to your application's Gemfile:

    gem 'tracker-git'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install tracker-git

## Usage

This gem will create a 'tracker' binary. Call that in your deploy script with
the tracker id and access token as command line arguments, or with following
environment variables set, and your finished stories will be updated to
delivered.

    export TRACKER_PROJECT_ID=123456
    export TRACKER_TOKEN=abc123
    tracker

You can also pass the project id and token in as parameters

    tracker 123456 abc123
    
## Optional parameters

Optionally you can specify a git branch to search for completed story IDs as
the third command line argument or with the GIT\_BRANCH environment variable.

If you want to add a label (tag) to the story marked as delivered, you
can use the `--label` flag:

    tracker --label THE_LABEL


For detect tasks only in commits which delivered to servers

    --remote-branch=heroku/master

For commenting task with message 'Delivered by script to <%server_name_parameter%>'

    --server-name=staging

Optionally you can specify a git branch to search for completed story IDs as
the third command line argument or with the GIT\_BRANCH environment variable.

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Added some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
