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

# enrobe la migration dans une transaction si la base de données le permet #

!SLIDE

# On peut annuler la migration #

!SLIDE commandline incremental

    $ rake db:migrate:down VERSION=20100324220333
    ==  CreateUsers: reverting ====================================================
    -- drop_table(:users)
       -> 0.0007s
    ==  CreateUsers: reverted (0.0008s) ===========================================

!SLIDE commandline incremental

# Mais plein d'autres tâches pour manipuler notre base de données #

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
