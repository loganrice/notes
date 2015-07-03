# Using Constraints to Enforce Subdomain
It is often common to serve api requests using an api subdomain.

One method is to:
```ruby
#config/routes.rb
resources :videos
resources :episodes, constraints: { subdomain: 'api' }
```

Or to use the constraints method and pass in a block:
```ruby
#config/routes.rb
resources :videos

constraints subdomain: 'api' do
  resources :episodes
end
