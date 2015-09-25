SpreeNewsletterSubscription
===========================

Allow simple newsletter subscription on Spree stores.

Supports Mailchimp and Mailup.

Installation
------------

Add spree_newsletter_subscription to your Gemfile:

```ruby
gem 'spree_newsletter_subscription'
```

Then for Mailchimp:

```ruby
gem 'mailchimp-api', '~> 2.0.6'
```

or for Mailup:
```ruby
gem 'mailup', '~> 1.2.0'
```

Bundle your dependencies and run the installation generator:

```shell
bundle
bundle exec rails g spree_newsletter_subscription:install
```

Configuration
-------------

Add your configuration to `config/initializers/spree.rb`:

Mailchimp example:

```ruby
SpreeNewsletterSubscription::Config.tap do |config|
  config.provider = 'mailchimp'
  config.provider_config = {
    api_key: 'xxxxxxxxxxxxx-us9',
    list_id: 'xxxxxxxxx'
  }
end
```

Mailup example:

```ruby
SpreeNewsletterSubscription::Config.tap do |config|
  config.provider = 'mailup'
  config.provider_config = {
    client_id: 'xxxxxxxxx',
    client_secret: 'xxxxxxxxx',
    username: 'xxxxxxxxx',
    password: 'xxxxxxxxx',
    list_id: 'xxxxxxxxx'
  }
end
```

You can have different config values for each locale.
If missing, the default is always used.
For example:

```ruby
SpreeNewsletterSubscription::Config.tap do |config|
  config.provider_config = {
    list_id: 'xxxxxxxxx',
    en: {
      list_id: 'yyyyyyyy' # use a different value, only for locale :en
    }
  }
end

Testing
-------

First bundle your dependencies, then run `rake`. `rake` will default to building the dummy app if it does not exist, then it will run specs. The dummy app can be regenerated by using `rake test_app`.

```shell
bundle
bundle exec rake
```

When testing your applications integration with this extension you may use it's factories.
Simply add this require statement to your spec_helper:

```ruby
require 'spree_newsletter_subscription/factories'
```

Copyright (c) 2014 Alessandro Lepore, released under the New BSD License
