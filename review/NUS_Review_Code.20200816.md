# NUS REVIEW CODE RESULT 2020/08/16

### Issues from last review and their status
---------
**Issues from last review and their status to control the fixing progress. Status: Fixed or not and reason if not fixed yet**

N/A

### Issues
---------

**Issues found in this review, also assign each issue to member(s). This section include these parts:**

#### Architecture

**The issues that are related to architecture, structure and infrastructure, example:**

1. Third-parties JS/CSS libraries should be placed in vendor instead of app/assets or public
```
#BAD
publish/awesome

#GOOD
vendor/assets/stylesheets/awesome
```
2. Didn't follow RESTful for resource
```
#BAD
get "feeds/album/:id/", to: "albums#show", as: :detail_newst
get "/profile/followers", to: "profile#followers"
get "/profile/followings", to: "profile#followings"
get "/profile/photos", to: "profile#phtos"
get "/profile/albums", to: "profile#albums"

```

#### Security

**The issues that are related to security: authentication, authorization, SSL, known vulnarabilities... Example:**

N/A

#### Performance

**The issues that are related to performance, also include solution issues (e.g: polling instead of socket). Example:**

1. Almost code that get an amount of records (e.g: get 20 products to show on home page) is **pull all** records in database to Ruby and get an amount of records here. It is **very bad** thing and it will **kill the server** when we have large data
```
#BAD
#/app/controllers/photos_controller.rb#feed
@photos = Photo.all

```
#### Coding conventions & best practices

**Example:**

1. LOT of commented code, look very ugly and not clean
```
#BAD
#validates :title, length: { maximum: 100 }, allow_blank: true
#validates :decription, length: { maximum: 1024 }, allow_blank: true
#validates :source, presence: true

```
2. Gemfile should define version for each gem
```
#BAD
gem "jquery-validation-rails"
```
3. Should use HAML/SLIM instead of ERB to write less code and develop more quickly
4. I18n was not used. This is bad because it will be hard if we want to have multi-language feature in the future; using I18n also helps us manage texts better too
```
#BAD
Example:
flash[:create_user_sucess] = "create sucess fullly"
<title>Fotobook</title>
...
```

5. Some of misspelled words
```
#BAD
get "/profile/photos", to: "profile#phtos"

#GOOD
get "/profile/photos", to: "profile#photos"


```
### Lessons learned
-------

**Lessons learned from this review code. They are mostly the summary of important issues, including how to prevent repeated issues**
