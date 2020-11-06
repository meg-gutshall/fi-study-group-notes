# Writing Tests

> **Dwayne Harmon on 09/04/19**

### **Testing**

* Use `RSpec` instead of `minitest`
  * `rails new_app -T` → this flag tells Rails to skip test files when generating the `new_app Rails` app
* In `.rspec`, write `--format-documentation` to receive useful output for failed tests

### **Unit Tests**

* Testing controllers and models
* Use gems `shoulda` and `shoulda-matchers` to help with creating these tests

### **Feature Tests**

* Use `Capybara` for these tests since it involves the view
* `context` is specific to `RSpec`; `scenario` is specific to `Capybara`
* You can refer to specific HTML tags using `within()` \(i.e. `within('form')`\)

