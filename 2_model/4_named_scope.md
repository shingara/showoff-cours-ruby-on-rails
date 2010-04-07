!SLIDE

# Les named_scope

!SLIDE

# Permet de créer des conditions à la volée

!SLIDE

# Combinable entre elle

!SLIDE

# Améliore la lisibilité

!SLIDE

    @@@ ruby
    class Post < ActiveRecord
      named_scope :drafts, :conditions => ['state = ?', 'draft']
      named_scope :limit, lambda {|num| :limit => num }
    end

    Post.draft
    # SELECT * FROM users where 'state' = 'draft'
    Post.draft.limit(3)
    # SELECT * FROM users where 'state' = 'draft' LIMIT 3

!SLIDE

# Le guide
## [http://guides.rubyonrails.org/active_record_querying.html](http://guides.rubyonrails.org/active_record_querying.html)
