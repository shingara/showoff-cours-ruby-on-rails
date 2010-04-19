!SLIDE

# Helpers

!SLIDE

# Se mette par défaut dans
# `app/helpers`

!SLIDE

# Un helper spécifique à chaque controllers
# Il a le même nom que le controller

!SLIDE

# Pour le controller
# `parties`
# Son helper sera
# `parties_helper`

!SLIDE

# Les Helpers sont des modules
# pas des classes

!SLIDE

# Que des méthodes de modules appelées directement

!SLIDE

# ApplicationHelper
## helper toujours présent.

!SLIDE

# Rails fourni plein de helpers chargés tout le temps

!SLIDE

# FormHelper
## Permet d'avoir des méthodes d'aide à la création d'un formulaire

!SLIDE

# En ERB

    @@@ html
    <% form_for :parties do |f| %>
      <p>
        <%= f.label :name %>
        <%= f.text_field :name %>
      </p>
      <p><%= submit_tag 'Update' %></p>
    <% end %>

!SLIDE

# Devient en HTML

    @@@ html
    <form method="post" action="/parties">
      <p>
        <label>Name</label>
        <input type="text" value="" name="parties[name]" />
      </p>
      <p><input type="submit" value="Update" /></p>
    </form>

!SLIDE

# form_for se base sur l'object pour en définir les données

!SLIDE

# il cherchera donc les valeurs dans ses attributs d'instance
# Dans l'exemple `name`
