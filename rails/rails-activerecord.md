# Rails ActiveRecord

> **Dwayne Harmon on 11/14/19**

## **Polymorphism**

* Use when it's an either/or situation
* `new_review.reviewable` → have to make dynamic calls to see what was being reviewed
  * Calling `new_review.artist` or `new_review.song` will not work because it could be either one
  * Can however call `Artist.reviews` or `Song.reviews`
* And we still have `User has_many :reviews` and `Review belongs_to :user`

## **Scope Methods**

* Class \(block-style\) methods return `nil` if the returned `ActiveRecord::Relation` object is `nil` or `false` \(empty\)
  * Not helpful to any developer ever
* Scope methods return `all` if the returned `ActiveRecord::Relation` object is `nil` or `false` \(empty\)
  * Very helpful

