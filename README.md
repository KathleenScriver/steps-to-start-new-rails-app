# Rails Boilerplate

simply clone this repo for a boilerplate rails app with testing tools included.

rails new <project-name> -T -d=postgresql --skip-turbolinks --skip-spring

add to gemfile these "basics"
```
  gem 'pry'
  gem 'rspec-rails'
  gem 'capybara'
  gem 'shoulda-matchers'
  gem 'launchy'
  gem 'database_cleaner'
  gem 'faker'
  gem 'factory_bot_rails'
  gem 'simplecov'
```

bundle install

rails generate rspec:install

#### config stuff:
- In `spec/spec_helper.rb`
add to top of file:
  ```
  require 'simplecov'
  SimpleCov.start 'rails'
```
- In `spec/rails_helper.rb`
add to top of file:

  `DatabaseCleaner.strategy = :truncation`

- Add in RSpec.configure block:
```
    config.include FactoryBot::Syntax::Methods

    config.include Capybara::DSL

    config.before :each do
        DatabaseCleaner.clean
      end

    config.after :each do
        DatabaseCleaner.clean
    end

    Shoulda::Matchers.configure do |config|
     config.integrate do |with|
       with.test_framework :rspec
       with.library :rails
     end
```
