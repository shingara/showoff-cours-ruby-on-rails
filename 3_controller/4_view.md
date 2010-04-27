!SLIDE

# Les views

!SLIDE

# située dans /app/views

!SLIDE

# Encore une convention

!SLIDE

# La vue par défaut d'une action d'un controllers est située
# Dans le dossier
# du nom du controller et le fichier du nom de la view

!SLIDE

# La view de l'action `new`
# du controllers `parties`
# sera donc :
# `app/views/parties/new.html.erb`

!SLIDE

# Plusieurs systèmes de templates

!SLIDE

# Le plus courant est celui par défaut de Rails est
# ERB

!SLIDE

# Le deuxième plus connu est
# [HAML](http://haml-lang.com/)

!SLIDE

# l'ERB est une légère modification du HTML

!SLIDE

# Ajoute la balise `<% %>` qui permet d'être interprété en ruby

!SLIDE

    @@@ ruby
    <p><%= 1 + 1 %></p>

## donne

    @@@ HTML
    <p>2</p>

!SLIDE

# On peux créer des méthodes dans les helpers
