# Speeding Up Your Rails App

> **Jenn Hansen on 02/20/19 & 11/17/19**

Speeding up an app always starts with the database.

## **Pre-Loading Associations**

* First and major way to speed up your app
* Associations actually have to render

### **Examples from the slides**

* On the `Cities#index` view, each listing of a city will also display the country, meaning that however many cities we have is how many times we query the database. This is way too much!
* On the homepage, all active users are listed and it displays the and it displays the cities the users have visited. Again, this is a lot of database queries.
  * The solution? Use `.includes`. It joins the cities table with the country table and the user table with the cities table so there isn't that additional query each time a city or a user is loaded—it's already pre-loaded!
* You can give `.includes` multiple arguments and create a nested `.includes` too

{% tabs %}
{% tab title="Cities\#index" %}
{% code title="cities\_controller.rb" %}
```ruby
def index
  @cities = City.all.includes(:country)
end

# :country is singular because a city belongs_to a country
```
{% endcode %}
{% endtab %}

{% tab title="Homepage" %}
{% code title="users\_controller.rb" %}
```ruby
def index
  @users = User.active_users.includes(:cities)
end

# :cities is plural because a user has_many cities
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Removing Unnecessary Queries

| **Do...** | **Don't...** |
| :--- | :--- |
| Try to stick to one SQL query per table |  |
| Execute queries in the controller | Execute queries while loading partials |
| Preload associations | Put query methods, like `where`, in instance methods of a model |
| Create new associations that you can preload if you need to call a scope on an association when rendering collections | Call scopes on associations when you're rendering collections |
| Use `.present?` or `.blank?` | Use `.exists?` or `.empty?` |

## **`count` vs. `size`**

* `.count` will always query the database
  * Only use this if you need the count at that exact moment
* `.size` queries the database only if the query hasn't already been cached in memory
  * If you call `.size` before the association is loaded, you still end up with two queries. You can get around this by calling `.load.size` which will only execute one query.

{% tabs %}
{% tab title="Count" %}
```ruby
def count(column_name = nil)
  if block_given?
    #...
    return super()
  end
  
  calculate(:count, column_name)
end


<% @comments.each do |comment| %>
  <%= comment.text %>
<% end %>
<%= @comments.count %>

# This will execute two queries
```
{% endtab %}

{% tab title="Size" %}
```ruby
def size
  loaded? ? @records.length : count(:all)
end


<% @comments.each do |comment| %>
  <%= comment.text %>
<% end %>
<%= @comments.size %>

# This will execute one query

<%= @post.comments.size %>
<% @post.comments.each do |comment| %>
  <%= comment.text %>
<% end %>

# This will execute two queries

<%= @post.comments.load.size %>
<% @post.comments.each do |comment| %>
  <%= comment.text %>
<% end %>

# This will execute one query
```
{% endtab %}
{% endtabs %}

## **Indexing Your Database**

Any column in your database that you will regularly use for queries should be indexed as long as that attribute or object isn't frequently deleted or created.

`rails generate migration AddIndexToContacts phone_number:string:index`

```ruby
class AddIndexToContacts < ActiveRecord::Migration
  def change
    add_index :contacts, :phone_number
  end
end
```

## Bullet Gem

{% embed url="https://github.com/flyerhzm/bullet" %}

Basically a linter for N+1 queries

* Add to `Gemfile` and run `bundle install`
* Follow configuration instructions in the repo's `README.md`
  * Pick which types of notifications you want to receive from this gem

## Slides

{% embed url="https://drive.google.com/open?id=1QqBknZRdiZAruEW7KD9IytUSXwPRwS6IEB3-mjdJKQI" %}

## **Resources**

* [Caching with Rails](https://guides.rubyonrails.org/caching_with_rails.html)
* [Delegation](https://apidock.com/rails/v6.0.0/Module/delegate)
* [Preload](https://api.rubyonrails.org/classes/ActiveRecord/QueryMethods.html#method-i-preload)
* [Eager Loading Associations](https://guides.rubyonrails.org/v5.2/active_record_querying.html#eager-loading-associations)
* [ActiveRecord's `select` & `pluck`](https://medium.com/@amliving/activerecords-select-pluck-3d5c58872053) 
* [5 Simple Tweaks to Make Your Rails App Faster](https://allenan.com/5-simple-tweaks-to-make-your-rails-app-faster/)
* [10 Tips to Speed Up Your Ruby on Rails App](https://applikeysolutions.com/blog/10-tips-to-speed-up-your-ruby-on-rails-app)
* [4 Easy Ways to Speed Up Your Rails App](https://blog.skylight.io/4-easy-ways-to-speed-up-your-rails-app/)
* [How to Preload Rails Scopes](https://www.justinweiss.com/articles/how-to-preload-rails-scopes/)

### **ActiveRecord Querying**

* [Making Sense of ActiveRecord `joins`, `includes`, `preload`, and `eager_load`](https://scoutapm.com/blog/activerecord-includes-vs-joins-vs-preload-vs-eager_load-when-and-where) 
* [The Odin Project: ActiveRecord Queries](https://www.theodinproject.com/courses/ruby-on-rails/lessons/active-record-queries)
* [ActiveRecord's Queries Tricks](https://medium.com/rubyinside/active-records-queries-tricks-2546181a98dd)
* [ActiveRecord::QueryMethods](https://api.rubyonrails.org/classes/ActiveRecord/QueryMethods.html)
* [3 ActiveRecord Mistakes That Slow Down Rails Apps](https://www.speedshop.co/2019/01/10/three-activerecord-mistakes.html)

### **Faster Rails Blog Series**

* [Is Your Database Properly Indexed?](https://semaphoreci.com/blog/2017/05/09/faster-rails-is-your-database-properly-indexed.html)
* [How to Check if a Record Exists](https://semaphoreci.com/blog/2017/03/14/faster-rails-how-to-check-if-a-record-exists.html)
* [Eliminating N+1 Queries](https://semaphoreci.com/blog/2017/08/09/faster-rails-eliminating-n-plus-one-queries.html)
* [Indexing Large Database Tables without Down Time](https://semaphoreci.com/blog/2017/06/21/faster-rails-indexing-large-database-tables.html)

