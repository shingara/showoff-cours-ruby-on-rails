!SLIDE

# Associations

!SLIDE

# 1 - N

!SLIDE

# belongs_to
## Appartiens

!SLIDE

# has_many
## a plusieurs

!SLIDE

    @@@ ruby
    class User < ActiveRecord::Base
      has_many :tasks
    end

!SLIDE

#tasks
## au plusieurs

!SLIDE

## Pas de modification dans la base de donnée. Aucun champs supplémentaire.

!SLIDE

    @@@ ruby
    class Task < ActiveRecord::Base
      belongs_to :user
    end

!SLIDE

# user
## au singulier

!SLIDE

## Au niveau de la base de donnée,
## ajout du champs « user_id » (au singulier) qui est
## la clé étrangère de « User »

!SLIDE

## Il faut donc créer la migration pour ajouter
## ce champs dans la base de données.

!SLIDE

## les méthodes « belongs_to » et « has_many » ne servent
## qu'à créer des méthodes

!SLIDE

# Conseil
## Ajouter un index sur « user_id ».
## Pas d'index créé par défaut.

!SLIDE

    @@@ ruby
    class AddAssociationToUsersTask < ActiveRecord::Migration
      def self.up
        add_column :tasks, :user_id, Integer
        add_index :tasks, :user_id
      end

      def self.down
        remove_column :tasks, :user_id
        remove_index :tasks, :user_id
      end
    end

!SLIDE

# Maintenant tout y est

!SLIDE

# Plusieurs méthodes utilitaires

    @@@ ruby
    user.tasks
    user.tasks.build(:name => 'my todo')
    user.tasks.create(:name => 'my todo')

!SLIDE

# #build crée l'assocation sans sauvegarder l'objet en base de donnée

!SLIDE

# #create crée l'association en sauvegardant l'objet en base de donnée

!SLIDE

    @@@ ruby
    task = Task.new
    user = User.find(2)
    user.tasks << task
    user.save # task est sauvé

!SLIDE

# Mais aussi d'autres associations

!SLIDE

# 1 - 1

!SLIDE

# has_one
# belongs_to

!SLIDE

# la clé étrangère sur le belongs_to

!SLIDE

# N - N

!SLIDE

# has_and_belongs_to_many
## Dans les deux models

!SLIDE

# Nécessite une table intermédiaire

!SLIDE

# Sans clé primaire

!SLIDE

# table de jointure avec les deux noms des models au pluriel

!SLIDE

    @@@ ruby
    class User < ActiveRecord::Base
      has_and_belongs_to_many :tasks
    end

    class Task < ActiveRecord::Base
      has_and_belongs_to_many :users
    end

    class CreateUserTaskTable < ActiveRecord::Migration
      def self.up
        create_table :users_tasks, :id => false do |t|
          t.integer :user_id
          t.integer :task_id
        end
      end
    end

!SLIDE

# Pas d'ajout d'information dans la table intermédiaire

!SLIDE

# Préférer « :through » qui fait l'associations

!SLIDE

# Nécessite de créer la table intermédiaire

!SLIDE

# Nécessite de créer le fichier du model de la table intermédiaire

!SLIDE

    @@@ ruby
    class User < ActiveRecord::Base
      has_many :user_tasks
      has_many :tasks, :through => :user_tasks
    end

    class UserTask < ActiveRecord::Base
      belongs_to :user
      belongs_to :task
    end

    class Task < ActiveRecord::Base
      has_many :user_tasks
      has_many :users, :through => :user_tasks
    end

!SLIDE

# Association Polymorphic

!SLIDE

# options « :polymorphic => true »

!SLIDE

# Nécessite 2 champs dans la base de données
## association_id   Integer
## association_type String

!SLIDE

    @@@ ruby
    class Asset < ActiveRecord::Base
      belongs_to :attachable, :polymorphic => true
    end

    class Post < ActiveRecord::Base
      has_many :assets, :as => :attachable
    end

    @asset.attachable = @post

!SLIDE

# Le guide
## [http://guides.rubyonrails.org/association_basics.html](http://guides.rubyonrails.org/association_basics.html)
