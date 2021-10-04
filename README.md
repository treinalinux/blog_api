# Project Blog Api


```bash
docker start postgres_rails

rails new blog_api -d postgresql --api

```

```ruby

vim config/database.yml

...
  host: 127.0.0.1
  username: postgres
  password: postgres
...

```


```bash
rails generate scaffold Article title:string body:text
```


```ruby

vim db/migrate/20211003145354_create_articles.rb

...
      t.string :title, null: false
      t.text :body, null: false
...

```

```ruby
vim app/models/article.rb

...
validates :title, :body, presence: true
...

```


```bash
rails db:create && rails db:migrate


```

```ruby

rails console

irb(main):002:0> Article.create title: 'Dev Ruby', body: 'Vagas para Desenvolvedor Ruby on Rails ou 
Desenvolvedor Python Django...'
```

```bash
rails server
http :3000/articles
http :3000/articles/1
```

## Version api

```bash

http :3000/api/articles

http :3000/api/articles 'Accept: application/vnd.blog.v1'
http :3000/api/articles 'Accept: application/vnd.blog.v2'

http GET :3000/api/articles

http POST :3000/api/articles title='Novo Blogs com Apis' body='Agora com estudos de api em Ruby On Rails com api e versionamento....'

http :3000/api/articles
http :3000/api/articles/1

http PUT :3000/api/articles/1 titile='Dev Ruby and Python' body='Vagas para Desenvolvedor Ruby on Rails ou Desenvolvedor Python Django...'

http :3000/api/articles
http DELETE :3000/api/articles/4

```


# 


```ruby

rails generate serializer article
      create  app/serializers/article_serializer.rb


vim app/serializers/article_serializer.rb
...
attributes :id, :title, :body
...

http :3000/api/articles


```
