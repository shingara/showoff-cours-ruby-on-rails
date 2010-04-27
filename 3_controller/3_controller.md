!SLIDE

# controller

!SLIDE

    @@@ ruby
    class PartiesController < ApplicationController
    end

!SLIDE

# Nom au pluriel

!SLIDE

# fichier dans le dossier
# /app/controllers

!SLIDE

# Hérite de ApplicationController
## ApplicationController
## (app/controllers/application_controller.rb)
## Est le fichier de base

!SLIDE

# Chaque méthode du controller
# est une action potentielle si mappée par une route

!SLIDE

# Pour une resource plusieurs méthode créer de base
## index
## show
## new
## edit
## destroy
## update
## create


!SLIDE

# Des Filtres

!SLIDE

# before_filter
## execute du code avant l'action

!SLIDE

# after_filter
## execute du code après l'action

!SLIDE

# respond_to
## permet de changer de comportement
## en fonction du mime-type
