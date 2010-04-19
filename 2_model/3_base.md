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
## Créer directement l'objet en Base de données ##
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

# STI ( Single Table Inheritance )

!SLIDE

# Necessite une champs « type » qui inclus la chaine de caractère correspondant à la classe correspondance

!SLIDE

    @@@ ruby
    class User < ActiveRecord::Base
    end

    class Man < User
    end

    class Woman < User
    end

