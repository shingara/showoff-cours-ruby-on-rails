!SLIDE

# La couche Model #

!SLIDE

# Pattern Active Record #

!SLIDE

# On ne défini pas les noms de champs #

!SLIDE

# On examine la table SQL pour connaitre les attributs de l'objet #

!SLIDE

# une classe #
# == #
# Un table SQL #

!SLIDE

# Un model c'est juste une classe #

!SLIDE

# Voici une classe de model #

    @@@ ruby
    class User < ActiveRecord::Base
    end

!SLIDE

# Rien de plus #

!SLIDE

# Correspondance avec la table SQL#
# « users » #

!SLIDE

# La table « users » #
## CREATE TABLE "users" ##
##("id" INTEGER PRIMARY KEY AUTOINCREMENT NOT NULL, "login" varchar(255), "email" varchar(255), "created_at" datetime, "updated_at" datetime);##

!SLIDE

# L'object « User » #

    @@@ Ruby
    User.new
     => #<User id: nil, login: nil, email: nil, created_at: nil, updated_at: nil>
    User.new.attributes.keys
     => ["created_at", "updated_at", "login", "email"]


!SLIDE

# configuration #
## définission du fichier `config/database.yml` ##

!SLIDE

    @@@ Ruby
    # SQLite version 3.x
    # gem install sqlite3-ruby (not necessary on OS X Leopard)
    development:
      adapter: sqlite3
      database: db/development.sqlite3
      pool: 5
      timeout: 5000

    # Warning: The database defined as "test" will be erased and
    # re-generated from your development database when you run "rake".
    # Do not set this db to the same as development or production.
    test:
      adapter: sqlite3
      database: db/test.sqlite3
      pool: 5
      timeout: 5000

    production:
      adapter: sqlite3
      database: db/production.sqlite3
      pool: 5
      timeout: 5000

!SLIDE

# 3 environments #

!SLIDE

# production #
# development #
# test #

!SLIDE

# development #

## Environment par défaut #

!SLIDE

# production #

## Environment a utiliser lors de la mise en production ##

!SLIDE

# test #
## Environement utilisé lors du lancement des tests ##
## unitaires/fonctionnels/integrations ##

!SLIDE

# Pourquoi 3 environments ? #

!SLIDE

# Eviter de se marcher sur les pieds en modifiant la base de données #

!SLIDE center

# Les adapters #
## Active Record supporte plusieurs système de base de données dont les plus communes ##
 * sqlite
 * mysql
 * postgresql
 * ms-sql
 * oracle

!SLIDE

# Création des base de données #

## rake db:create ##
## rake db:create:all ##

!SLIDE

# Création du schéma de la base de données ? #

!SLIDE

# Pas de SQL #

!SLIDE

# Faisons du Ruby #
