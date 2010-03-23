!SLIDE
<script type="text/javascript">
  $(function(){
    $('a').replaceCcWithLogo();
  });
</script>


# Cours de Ruby on Rails #

## Par Cyril Mougel ##
### cyril.mougel@gmail.com ###

!SLIDE

# Première release en 2004 #

!SLIDE center

# Créé par David Heinemeier Hansson « DHH » #

![DHH](dhh.jpg "DHH")

<p class="cc">
Image de <span xmlns:cc="http://creativecommons.org/ns#" about="http://www.flickr.com/photos/jesper/1414028690/"><a rel="cc:attributionURL"     href="http://www.flickr.com/photos/62337512@N00/">Jesper Rønn-Jensen</a> <a rel="license" href="http://creativecommons.org/licenses/by/2.0/">(CC)</a></span>
</p>

!SLIDE center

# De la société 37 Signals #

![37_signal](37signals.png "37 Signals")

!SLIDE center

# Extrait de BaseCamp #

![Basecamp](basecamp.png "BaseCamp")

!SLIDE

# En ruby car ... #

!SLIDE

# Possibilité d'introspection du code #

## User.find_by_name('hello') ##

!SLIDE center

# Une syntaxe simple #

    @@@ ruby
    class Project < ActiveRecord::Base
      has_many :users
    end


!SLIDE

# Le concept ? #

!SLIDE

# Concu pour les développeurs #
# Par les développeurs #

!SLIDE

# Un cadre de travail minimal #

!SLIDE

# Mais complet #

!SLIDE

# Uniquement pour faire du Web #

!SLIDE

# et que du web #

!SLIDE

# « Convention over Configuration » #

!SLIDE

# Moins on a de fichier de configuration #

!SLIDE

# Moins on a de fichier à éditer #

!SLIDE

# « Don't repeat Yourself » #

!SLIDE

# Arrêtons de copier coller notre code #
# à d'autre endroit #

!SLIDE

# Un seul langage a apprendre #

!SLIDE

# Ruby on Rail est #
# MVC #

!SLIDE

# Model #
# View #
# Controller #

!SLIDE

# Le modèle ( Model ) #

!SLIDE

# Couche métier #

!SLIDE

# Correspondance avec les Bases de données #

!SLIDE

# Les vues ( Views ) #

!SLIDE

# La présentation HTML #

!SLIDE

# Juste du HTML #

!SLIDE

# Les contolleurs ( Controllers ) #

!SLIDE

# Dispatch les URL #

!SLIDE

# Une URL == Une action #

!SLIDE

# Un hierachie de fichier défini #

!SLIDE

# Chaque couche à sa place #

!SLIDE

# model #
# == #
# app/models #

!SLIDE

# view #
# == #
# app/views #

!SLIDE

# controller #
# == #
# app/controllers #

!SLIDE

# Un dossier de configuration #
# == #
# /config #

!SLIDE

# Un dossier de librairie #
# == #
# /lib #

!SLIDE

# Un seul fichier pour gérer les URL #

!SLIDE

# route.rb #

!SLIDE

# Une aide a la création #

!SLIDE commandline incremental

    $ rails my_app
      create
      create  app/controllers
      create  app/helpers
      create  app/models
      create  app/views/layouts
      create  config/environments
      create  config/initializers
      create  config/locales
      create  db
      create  doc
      create  lib
      create  lib/tasks
      create  log
      create  public/images
      create  public/javascripts
      create  public/stylesheets
      create  script/performance
      create  test/fixtures
      create  test/functional
      create  test/integration
      create  test/performance
      create  test/unit
      create  vendor
      create  vendor/plugins
      create  tmp/sessions
      create  tmp/sockets
      create  tmp/cache
      create  tmp/pids

!SLIDE commandline

    $ ...
      create  Rakefile
      create  README
      create  app/controllers/application_controller.rb
      create  app/helpers/application_helper.rb
      create  config/database.yml
      create  config/routes.rb
      create  config/locales/en.yml
      create  db/seeds.rb
      create  config/initializers/backtrace_silencers.rb
      create  config/initializers/inflections.rb
      create  config/initializers/mime_types.rb
      create  config/initializers/new_rails_defaults.rb
      create  config/initializers/session_store.rb
      create  config/environment.rb
      create  config/boot.rb
      create  config/environments/production.rb
      create  config/environments/development.rb
      create  config/environments/test.rb
      create  script/about
      create  script/console
      create  script/dbconsole
      create  script/destroy
      create  script/generate
      create  script/runner
      create  script/server
      create  script/plugin
      create  script/performance/benchmarker


