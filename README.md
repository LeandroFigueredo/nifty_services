# NiftyServices
[![Build Status](https://travis-ci.org/fidelisrafael/nifty_services.svg)](https://travis-ci.org/fidelisrafael/nifty_services)
## Introduction

Nifty Services comes to solve your Ruby applications(*including but not limited to* Rails, Grape, Sinatra, and plain Ruby) code mess with **simplicity in mind**!

NiftyServices provides a very nifty, simple & clear API to **organize and reuse** your application **domain logic in plain Ruby Services Objects** turning your codebase in a very extensible, standardized and reusable components.

**Most important:** You and your team win what I consider the best benefit when using Nifty Services: **Easily and scalable maintained code.**
 Believe me, you'll fall in :heart_eyes: with this small piece of code, keep reading!

This gem was designed and conventioned to be used specially with **Web API applications**, but this is just a convention, you can use it even with [shoes (for desktop apps)](https://github.com/shoes/shoes) applications if you  want, for example.

#### :book: I know, this README is very huge

As you can see, this README needs some time to be full read, but is very difficulty to explain all things, concepts and philosophy of this gem without writing a lot, we can't escape this :(

But remember one thing: This is a **tecnical documentation**, not a blog post, I'm pretty sure you can take about 30 minutes + some cups of :coffee: to better understand all NiftyServices can
do for you and your project. Good reading, and if you have some question, [please let me know](issues/new).

---

## Conventions

Below, some very importants things about conventions for this cute :gem: :)

### :white_check_mark: Single responsibility <a name="conventions-single-responsibility"></a>

Each service class is responsible for perform exactly [one single task](https://en.wikipedia.org/wiki/Single_responsibility_principle), say goodbye for code (most important: logic) duplication in your code.
Beside this, one of the aim of NiftyServices is to provide a **very standardized** code architecture, allowing developers to quickly develop and implement new features keeping the application codebase organized and stable.

### :hammer: Common and single-run execution method

Each service object must respond to `#execute` instance method, which is allowed to be **called just one time** per instance.
`#execute` method is responsible to perform code validation(parameter validation, access level control), execution(send mail, register users) and fire callbacks so you can execute hooks actions **after/before success or execution fail**.

### :package: Rich Service Objects

When dealing with services objects, you will get a very rich objects to work with, forgot about getting only `true or false` return values, one of the main purpose of objects it's to keep your code domain logic accessible and reusable, so your application can really take the best approach when responding to actions.

### :lock: Security - Access Control Level

Think and implement security rules from the first minutes of live in your applications! NiftyServices strongly rely on **Access Control Level(ACL)** to perform actions, in other words, you will only **allow authorized users to read, create, update or delete records in your database**!

Now you know the basic concepts and philosophy of `NiftyServices`, lets start working with this candy library?

---


## Table of Contents

* [Dafuck is this gem](#introduction)
* [Conventions](#conventions)
  * [Single Responsability](#conventions-single-responsibility)
  * [Method execution](#hammer-common-and-single-run-execution-method)
  * [Rich Service Objects](#package-rich-service-objects)
  * [Security & Access Level Control](#lock-security---access-control-level)
* [Installation](#installation)
* [Usage](./docs/usage.md#usage)
  * [Basic Service Markup](./docs/usage.md#basic-service-markup)
  * [How a Service must be created](./docs/usage.md#wrapping-things-up)
  * [Services API](./docs/usage.md#services-public-api)
    * [Full Public Service API Methods List](./docs/usage.md#full-public-api-methods-list)
  * [Handling Success & Error Responses](./docs/usage.md#success--error-responses)
    * [Success response](./docs/usage.md#white_check_mark-handling-success-zap)
    * [Error response](./docs/usage.md#red_circle-handling-error-boom)
      * [Custom error response methods](./docs/usage.md#custom-error-response-methods)
  * [CRUD Services](#crud-services)
    * [**Create** - BaseCreateService](#white_check_mark-crud-create)
      * [I18n Setup](#earth_americas-i18n-setup)
      * [Error - Invalid User](#alien-invalid-user)
      * [Error - Not authorized](#no_entry_sign-not-authorized-to-create)
      * [Error - Invalid record](#boom-record-is-invalid)
    * [**Update** - BaseUpdateService](#white_check_mark-crud-update)
      * [I18n Setup](#earth_asia-i18n-setup)
      * [Error - Invalid User](#update-resource-user-invalid)
      * [Error - Resource don't belongs to user](#update-resource-dont-belongs-to-user)
      * [Error - Resource dont exists](#update-resource-dont-exists)
    * [**Delete** - BaseDeleteService](#white_check_mark-crud-delete)
        * [I18n Setup](#earth_africa-i18n-setup)
        * [Error - Invalid User](#delete-resource-user-invalid)
        * [Error - Resource don't belongs to user](#delete-resource-dont-belongs-to-user)
        * [Error - Resource dont exists](#delete-resource-dont-exists)
   * [I18n Setup](#us-fr-jp-i18n-support-uk-es-de)
   * [Callbacks](#callbacks)
      * [Using custom callbacks](#creating-custom-callbacks)
   * [Configuration](#construction-configuration-construction)
   * [Web Frameworks integration](#web-frameworks-integrations)
      * [Ruby on Rails](#frameworks-rails)
      * [Grape/Sinatra/Rack](#frameworks-rack)
      * [Sample Integrations](#integration-examples)
   * [Basic Services class Markups](#pray-basic-service-markups-raised_hands)
      * [BaseCreateService Basic Markup](#basecreateservice-basic-markup)
      * [BaseUpdateService Basic Markup](#baseupdateservice-basic-markup)
      * [BaseDeleteService Basic Markup](#basedeleteservice-basic-markup)
      * [BaseActionService Basic Markup](#baseactionservice-basic-markup)
   * [CLI Generators](#cli-generators)
   * [Roadmap](#roadmap)
   * [Development](#computer-development)
   * [Contributing](#thumbsup-contributing)
   * [License - MIT](#memo-license)

---

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'nifty_services', '~> 0.0.5'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install nifty_services

---

## :computer: Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake rspec` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem(:gem:) onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

---

## :thumbsup: Contributing

Bug reports and pull requests are welcome on GitHub at http://github.com/fidelisrafael/nifty_services. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](contributor-covenant.org) code of conduct.

---

## :memo: License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
