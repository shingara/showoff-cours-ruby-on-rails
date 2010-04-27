!SLIDE

# 1 seul fichier pour gérer les routes

!SLIDE

# routes.rb
## config/routes.rb

!SLIDE

# map.root

!SLIDE

## défini le controller/action de
## /

    @@@ ruby
    map.root :controller  => 'articles', :action => 'index'


!SLIDE

# map.connect

!SLIDE

## fait matcher l'url
## /archives
## au controller Article et l'action archives

    @@@ ruby
    map.connect '/archives/', :controller => "articles",
                              :action => "archives"

!SLIDE

# Les routes nommés

!SLIDE

# map.what_you_want

!SLIDE

## fait matcher l'url
## /articles.rss
##au controller articles et l'action index

    @@@ ruby
    map.rss 'articles.rss', :controller => 'articles',
                            :action => 'index',
                            :format => 'rss'

!SLIDE

## génére la méthode rss_url pour définir l'url

!SLIDE

# Gestion d'une ressource

!SLIDE

# map.ressources

!SLIDE

## génére toutes les routes nécessaires pour une ressource

!SLIDE

    @@@ ruby
    map.ressources :parties

!SLIDE

    @@@
    parties    GET    /parties(.:format)                 {:action=>"index", :controller=>"parties"}
               POST   /parties(.:format)                 {:action=>"create", :controller=>"parties"}
    new_party  GET    /parties/new(.:format)             {:action=>"new", :controller=>"parties"}
    edit_party GET    /parties/:id/edit(.:format)        {:action=>"edit", :controller=>"parties"}
    party      GET    /parties/:id(.:format)             {:action=>"show", :controller=>"parties"}
               PUT    /parties/:id(.:format)             {:action=>"update", :controller=>"parties"}
               DELETE /parties/:id(.:format)             {:action=>"destroy", :controller=>"parties"}

