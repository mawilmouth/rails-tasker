# RailsTasker

`rails_tasker` provides a system to automate your post-deploy tasks as Plain Old Ruby Objects that are easy to test and create.

A new database table (`rails_tasker_tasks`) is created in order to keep track of the state of each task in a similar way to how rails maintains the states of migrations. 

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'rails_tasker'
```

And then execute:

    $ bundle install

Or install it yourself as:

    $ gem install rails_tasker

Run the install generator to create the needed configurations and migration:

    $ rails generate rails_tasker:install

Run the migration:

    $ rails db:migrate

## Usage

###### Create a new task

    $ rails generate rails_tasker:task new_task_name
- This will create the following task file: `lib/rails_tasker/tasks/<current_timestamp>_new_task_name.rb`

###### Add the logic to the task
- Each task must implement a `#call` instance method.
    - This is the main method that will be called in order execute your new task.

###### Run all pending tasks

    $ rake rails_tasker:run

###### Or run a specific task

    $ rake rails_tasker:run[version]

###### Note 
It is recommended to run this after the migrations in the deployment process.

That's it. A very simple system for post-deploy tasks.

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/mawilmouth/rails_tasker.

## License

The gem is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).
