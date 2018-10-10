### machinist
---
https://github.com/notahat/machinist

```ruby
describe Comment, "without_spam scope" do
  it "doesn't include spam" do
    spam = Comment.make!(:spam => true)
    Comment.without_spam.should_not include(spam)
  end
end

require 'machinist/active_record'
User.blueprint do
  username { "user#{sn}" }
end
Post.blueprint do
  author
  title { "Post #{sn}" }
  body { "Lorem ipsum..." }
end
Comment.blueprint do
  post 
  email { "commenter#{sn}@example.com" }
  body { "Lorem ipsum..." }
end

config.generators do |g|
  g.fixture_replacement :machinist
end

Post.blueprint do
  title { "A Post" }
  body { "Lorem ipsum..." }
end
Post.make!

Post.make!(:title => "A Specific Title")
User.blueprint do
  username { "user-#{sn}" }
end

Commnet.blueprint do
  post { Post.make }
end

Comment.blueprint do
  post
end

post = Post.make(:title => "A particluar title")
comment = Commnet.make(:post => post)

Post.blueprint do
  comments(3)
end

User.blueprint do
  name { "User #{sn}" }
  email { "user-#{sn}@example.com" }
end
User.blueprint(:admin) do
  name { "Admin User #{sn} " }
  admin { true }
end
User.make!(:admin)

class Post
  extend Machinist::Machinable
  attr_accessor :title
  attr_accessor :body
end
Post.blueprint do
  title { "A title!" }
  body { "A body!" }
end
Post.blueprint do
  author { "Author #{sn}" }
  body { "Post by #{object.author}" }
end

```

```
gem 'machinist', '>= 2.0.0.beta2'
bundle
rails g machinist:install
```
