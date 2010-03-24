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

# Eviter de se marcher sur les pieds en modifiant la base de donnée #

!SLIDE center

# Les adapters #
## Active Record supporte plusieurs système de base de donnée dont les plus communes ##
 * sqlite
 * mysql
 * postgresql
 * ms-sql
 * oracle

!SLIDE

# Création des base de donnée #

## rake db:create ##
## rake db:create:all ##

!SLIDE

# Création du schéma de la base de donnée ? #

!SLIDE

# Pas de SQL #

!SLIDE

# Faisons du Ruby #

!SLIDE

# Les migrations #

!SLIDE

# 1 fichier par migration #

!SLIDE

# préfixé par le timestamp de création #

!SLIDE

# Tout dans le dossier /db/migrate #

!SLIDE

# Un script pour générer une migration #

!SLIDE commandline incremental

    $ ruby script/generate migration create_users
      exists  db/migrate
      create  db/migrate/20100324224104_create_users.rb

!SLIDE

    @@@ ruby
    class CreateUsers < ActiveRecord::Migration
      def self.up
        create_table :users do |t|
          t.string :login
          t.string :email

          t.timestamps
        end
      end

      def self.down
        drop_table :users
      end
    end

!SLIDE

# script ruby avec #
# un methode self.up #
# et #
# une méthode self.down #

!SLIDE

# self.up #

## est executé pour réaliser la migration ##

!SLIDE

# self.down #

## est executé pour faire un rollback sur la migration ##

!SLIDE

# create_table #

# méthode pour créer une table SQL #

!SLIDE

# timestamp #

## Permet d'ajouter des champs created_at et updated_at ##

!SLIDE center

# Plein de méthode de manipulation de BDD #

 * add_column
 * add_index
 * drop_table
 * rename_table
 * rename_column
 * remove_column

!SLIDE

# voir la documentation #
## http://api.rubyonrails.org/classes/ActiveRecord/Migration.html ##


!SLIDE

# Une table SQL « versions » pour gérer les migrations executées #

    @@@ sql
    sqlite> .schema schema_migrations
    CREATE TABLE "schema_migrations"
      ("version" varchar(255) NOT NULL);
    CREATE UNIQUE INDEX "unique_schema_migrations"
      ON "schema_migrations" ("version");

## Contient la liste des migrations effectuées ##

!SLIDE

# Executer les migrations ? #

!SLIDE

# rake db:migrate #

!SLIDE commandline incremental

   $ rake db:migrate
    ==  CreateUsers: migrating ====================================================
     -- create_table(:users)
       -> 0.0015s
     ==  CreateUsers: migrated (0.0017s) ===========================================

!SLIDE

# Ne relance pas les migration déjà fait #

!SLIDE commandline

   $ rake db:migrate
    # nothing

!SLIDE

# enrobe la migration dans une transaction si la base de donnée le permet #

!SLIDE

# On peut annuler la migration #

!SLIDE commandline incremental

    $ rake db:migrate:down VERSION=20100324220333
    ==  CreateUsers: reverting ====================================================
    -- drop_table(:users)
       -> 0.0007s
    ==  CreateUsers: reverted (0.0008s) ===========================================

!SLIDE commandline incremental

# Mais plein d'autres tâches pour manipuler notre base de donnée #

    $ rake -T db
    (in /tmp/tmp)
    rake db:abort_if_pending_migrations  # Raises an error if there are pending migrations
    rake db:charset                      # Retrieves the charset for the current environment's database
    rake db:collation                    # Retrieves the collation for the current environment's database
    rake db:create                       # Create the database defined in config/database.yml for the current RAILS_ENV
    rake db:create:all                   # Create all the local databases defined in config/database.yml
    rake db:drop                         # Drops the database for the current RAILS_ENV
    rake db:drop:all                     # Drops all the local databases defined in config/database.yml
    rake db:fixtures:identify            # Search for a fixture given a LABEL or ID.
    rake db:fixtures:load                # Load fixtures into the current environment's database.
    rake db:migrate                      # Migrate the database through scripts in db/migrate and update db/schema.rb by invoking db:schema:dump. Target speci...
    rake db:migrate:down                 # Runs the "down" for a given migration VERSION.
    rake db:migrate:redo                 # Rollbacks the database one migration and re migrate up.
    rake db:migrate:reset                # Resets your database using your migrations for the current environment
    rake db:migrate:up                   # Runs the "up" for a given migration VERSION.
    rake db:reset                        # Drops and recreates the database from db/schema.rb for the current environment and loads the seeds.
    rake db:rollback                     # Rolls the schema back to the previous version.
    rake db:schema:dump                  # Create a db/schema.rb file that can be portably used against any DB supported by AR

!SLIDE commandline

    $ ...
    rake db:schema:load                  # Load a schema.rb file into the database
    rake db:seed                         # Load the seed data from db/seeds.rb
    rake db:sessions:clear               # Clear the sessions table
    rake db:sessions:create              # Creates a sessions migration for use with ActiveRecord::SessionStore
    rake db:setup                        # Create the database, load the schema, and initialize with the seed data
    rake db:structure:dump               # Dump the database structure to a SQL file
    rake db:test:clone                   # Recreate the test database from the current environment's database schema
    rake db:test:clone_structure         # Recreate the test databases from the development structure
    rake db:test:load                    # Recreate the test database from the current schema.rb
    rake db:test:prepare                 # Check for pending migrations and load the test schema
    rake db:test:purge                   # Empty the test database
    rake db:version                      # Retrieves the current schema version number

!SLIDE

# Mais une documentation détaillé, il y a le guide #

# [http://guides.rubyonrails.org/migrations.html](http://guides.rubyonrails.org/migrations.html) #

!SLIDE

# Les models dans les dossiers /app/model

!SLIDE

# Le nom de la classe est au singulier

!SLIDE

# Le nom de la table est au pluriel

!SLIDE

# Création d'object #

!SLIDE

# #new #
## prend un Hash pour définir les attributs ##
## N'enregistre pas l'objet en Base. nécessite #save pour cela ###
    @@@ ruby
    user = User.new(:login => 'shingara)
    # => #<User id: nil, login: "shingara", email: nil, created_at: "2010-03-24 23:28:34", updated_at: "2010-03-24 23:28:34">
    user.save
    # => true


!SLIDE

# #create #
## Créer directement l'objet en Base de donnée ##
    @@@ ruby
    user = User.create(:login => 'shingara)
    # => #<User id: 1, login: "shingara", email: nil, created_at: "2010-03-24 23:28:34", updated_at: "2010-03-24 23:28:34">

!SLIDE

# La recherche d'objet #

!SLIDE

# #find #
    @@@ ruby
    User.find(1)
    # => #<User id: 1, login: "shingara", email: nil, created_at: "2010-03-24 23:28:34", updated_at: "2010-03-24 23:28:34">

!SLIDE

# #all #
    @@@ ruby
    User.all
    # => [#<User id: 1, login: "shingara",
          #<User id: 2, login: "shin"]

    User.all(:conditions => {:login => 'shingara'})
    # => [#<User id: 1, login: "shingara"]

!SLIDE

# #count #
    @@@ ruby
    User.count
    #=> 2

!SLIDE

# #find_by_*

## Permet de créer des méthode en fonction des attributs ##

    @@@ ruby
    User.find_by_login('shingara')
    # => [#<User id: 1, login: "shingara", email: "cyril.mougel@gmail.com"]
    User.find_by_login_and_email('shingara',
                                 'cyril.mougel@gmail.com')
    # => [#<User id: 1, login: "shingara", email: "cyril.mougel@gmail.com"]

!SLIDE

# #first
    @@@ ruby
    User.first
    # => #<User id: 1, login: "shingara"

    User.first(:conditions => {:login => 'shingara'})
    # => #<User id: 1, login: "shingara"

!SLIDE

# Les named_scope
## Permet de créer des conditions à la volée
## Combinable entre elle

!SLIDE

    @@@ ruby
    class Post < ActiveRecord
      named_scope :drafts, :conditions => ['state = ?', 'draft']
      named_scope :limit, lambda {|num| :limit => num }
    end

    Post.draft
    # SELECT * FROM users where 'state' = 'draft'
    Post.draft.limit(3)
    # SELECT * FROM users where 'state' = 'draft' LIMIT 3

!SLIDE

# Les validations #

!SLIDE

# Permet de ne pas enregistrer des données fausses #

!SLIDE

# Posséde un message spécifique #

!SLIDE

    @@@ ruby
    class User
      validates_presence_of :login
    end

    user = User.new
    user.valid?
    # => false
    user.save
    # => false
    user.errors
    # => ["Login can't be blank"]

