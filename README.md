## Scripts to bootstrap Mailchimp integrations built on rails

While these templates may have some differences, such as using/not using backbone, 
they will all provide the following:

* OAuth login strategy with Omniauth with the following routes and a Session controller

```ruby
  match '/auth/failure' => 'sessions#failure'
  match '/signout' => 'sessions#destroy', :as => :signout
  match '/signin' => 'sessions#new', :as => :signin
  match '/auth/:provider/callback' => 'sessions#create'
  resources :users, :only => [ :show, :edit, :update ]

``` 

* A User model with the following attributes

```ruby
  uid: the mailchimp unique id
  email: mailchimp account email address
  apikey: mailchimp apikey

```

* LESS styles that echo the Mailchimp.com user experience (while still being unique)

TODO:
* ask for mailchimp oauth client id and secret in wizard
* write and hook in new relic recipe
* fix powder recipe to run in app directory