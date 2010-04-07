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

!SLIDE

# Plein de validations différentes #

!SLIDE

#validates_format_of
## Valide le format de l'attribut

!SLIDE

#validates_length_of
## Valide la taille du champs

!SLIDE

#validate
## en définissant la méthode on peux ajouter les validations personnelles que l'on souhaite

!SLIDE

# errors.add(:field, 'message')
# errors.add_to_base('message')
## Définis les messages d'erreurs. Si une erreurs est ajouté l'objet est invalide.
