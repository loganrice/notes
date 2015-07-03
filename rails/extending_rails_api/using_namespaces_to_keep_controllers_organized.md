#Using Namespaces to Keep Controllers Organized

It is good practice to keep web controllers seperate from api controllers
in a rails project.

To do this you need to add a namespace to the routes.

```ruby
#config/routes.rb
constraints subdomain: 'api' do
  namespace :api do
    resources :products
  end
end
```

However, this will create a uri with unessessary duplication.
The word "api" appears twice.
```
http://api.cars.com/api/products
```

In order to fix this we need to pass in a path option in our namespace.

```ruby
#config/routes.rb
constraints subdomain: 'api' do
  namespace :api, path: '/' do
    resources :products
  end
end
```

Now the uri becomes like this:

```
http://api.cars.com/products
```

The route can also be rewritten to:

```ruby
namespace :api, path: '/', constraints: { subdomain: 'api' } do
  resources :products
end
```

Now in the controllers, create a namespace for the api controllers only.

```ruby
#app/controllers/api/products_controller.rb
module Api
  class ProductsController < ApplicationController
  end
end
```

By convention rails uses camel case for naming the Api module.
If you would like to use all caps, like API (since api is an acronym), then

Update the inflections file

```ruby
#config/initializers/inflections.rb
ActiveSupport::Inflector.inflections(:en) do |inflect|
  inflect.acronym 'API'
end
```

Then update the controller to:

```ruby
#app/controllers/api/products_controller.rb
module API
  class ProductsController < ApplicationController
  end
end
```

