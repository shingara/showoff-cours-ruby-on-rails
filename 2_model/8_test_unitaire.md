!SLIDE

# Les tests unitaires des models

!SLIDE

# Les test unitaires sont placé dans le dossier /test/unit

!SLIDE

# Par défaut chaque test est dans une transaction
# pour éviter de corrompre ses données

!SLIDE

# Utilisation de factory_girl pour créer les données type

!SLIDE

# Facetory_girl génére des données et permet de les enregistrer en base

!SLIDE

# gem install factory_girl

!SLIDE

    @@@ ruby
    Factory.define(:user) do |u|
      u.login 'shingara'
      u.firstname 'cyril'
    end

!SLIDE

# On peux les appeler dans nos tests

    @@@ ruby
    Factory.make(:user) # Sauvé en base
    Factory.make(:user, :login => 'madx') # Sauvé en base

!SLIDE

# On peux créer des objets sans les sauver en base avec build

    @@@ ruby
    Facetory.build(:user) # rien de sauvé en base
    Factory.build(:user, :login => 'madx') # rien de sauvé en base
