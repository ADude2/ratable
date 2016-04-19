# Ratable

A simple gem that provides a framework to build a rating system, JQuery Raty and some default views.

### Getting Started

1. Add the gem to your Gemfile `gem 'ratable'`.
2. Run the installer `rails g ratable:install`.
3. Run the views generator `rails g ratable:views` *(optional)*.
4. Add `acts_as_ratee` to the model to be rated.
5. Add `acts_as_rater` to the model doing the rating *(optional)*.

### Rating Model

The `Ratable::Rating` model will be added to your `schema.rb` after running the migration added by `rails g ratable:install`. This model has a polymorphic `ratee` and `rater`.

The `Ratable::Rating` attributes are:

* `ratee`: poly reference (ratee_id, ratee_type) *(required)*
* `rater`: poly reference (rater_id, rater_type) *(optional)*
* `value`: integer *(required)*
* `comment`: text *(optional)*

The only required attributes for a `Ratable::Rating` are `ratee` and `value`.

### Methods

`acts_as_ratee`: Makes a model ratable. Accepts the parameters `has_many` and `has_one`, which are both booleans. Defaults to `has_many`, but can be change to `has_one`: `acts_as_ratee(has_one: true)`

`acts_as_rater`: Make a model the rater. Accepts the parameters `has_many` and `has_one`, which are both booleans. Defaults to `has_many`, but can be changeed to `has_one`: `acts_as_rater(has_one: true)`

`ratee.ratings`: Returns a ratee's associated ratings.

`rater.ratings`: Returns a rater's associated ratings.

`ratee.rate(attributes)`: Creates a Rating for the ratee in question.

`rater.rate(attributes)`: Creates a Rating for the rater in question.

`ratee.ratings.by_rater(rater)`: `Ratable::Rating` scope that returns a ratee's ratings for a particular rater.

`rater.ratings.by_rater(ratee)`: `Ratable::Rating` scope that returns a rater's ratings for a particular ratee.