# Many exist, these are mine. 
## Just a few rails templates

The first template(s) will be focused on bootstrapping a Mailchimp integration

###Mailchimp Integration

While these templates may have some differences, such as using/not using backbone, 
the Mailchimp templates will all provide the following:

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
  :uid => the mailchimp unique id
  :email => mailchimp account email address
  :apikey => mailchimp apikey
```

* LESS styles that echo the Mailchimp.com user experience (while still being unique)
 
 
## How to use

```bash
  $ rails new MyNewApp -m https://raw.github.com/wnadeau/rails-application-templates/master/rails3-backbone-twitter-bootstrap-mailchimp.txt
```
 Then answer the prompts.

##TODO:
* ask for mailchimp oauth client id and secret in wizard
* write and hook in new relic recipe
* fix powder recipe to run in app directory