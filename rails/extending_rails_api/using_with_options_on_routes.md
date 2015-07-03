# Using with options on routes

When creating routes it can become verbose when restricted access to the
action. For example, what if we wanted to only show the index action for 
 several resources. 

We could write:
```ruby
resources :products, only: :index
resources :addresses, only: :index
resources :users, only: :index
```

This can be rewritten like this:
```ruby
with_options only: :index do |list_only|
  list_only.resources :products
  list_only.resources :addresses
  list_only.resources :users
end
```

The arguments (i.e. :index) are added automatically to all of the resources
inside of the block.
