# Rails Active Storage

> **Dwayne Harmon on 10/24/19**

{% embed url="https://github.com/dwyn/ActiveStorageDemo" %}

* Active Storage is where you keep media in Rails
  * Images, music, videos, etc.

## **Setup**

* Run `rails active_storage:install` in the terminal
  * This copies a migration from Rails source code
* Run `rails db:migrate`

## **Active Storage Tables**

### Blobs

* Covers metadata of the uploaded files

## **Getting Media Files**

* In `config/storage.yml`, you uncomment the service you use or add in another one
* In `config/environments/` change each environment file to let it know where the active storage files are being hosted

## **Models**

* Use the `has_one_attached :image` association in your model
  * This changes depending on what type of media you use

## **Forms**

* Use the `file_field` tag to upload media

## **Resources**

* YouTube Channel: [Go Rails](https://www.youtube.com/channel/UCIQmhQxCvLHRr3Beku77tww)
* Documentation: [Active Storage Overview](https://guides.rubyonrails.org/active_storage_overview.html)

