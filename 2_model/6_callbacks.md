!SLIDE

# Callbacks

!SLIDE

# Appelé avant ou après l'action en question

!SLIDE

# Plein de callbacks

!SLIDE center

## « before » et « after »

 * create
 * update
 * save
 * delete

!SLIDE

    @@@ruby
    class User < ActiveRecord::Base
      before_save :update_time

      def update_time
        self.updated_at = Time.now
      end
    end

!SLIDE

# Tout dans le guide
## [http://guides.rubyonrails.org/activerecord_validations_callbacks.html](http://guides.rubyonrails.org/activerecord_validations_callbacks.html)
