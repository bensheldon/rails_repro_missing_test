# Bad test

Reproducing problem with: https://github.com/rails/rails/pull/51005

```bash
# Returns exit code 0
bin/rails test test/bad_require_test.rb test/fail_test.rb

# undefined method `squish' for an instance of String (NoMethodError)
bin/rails test test/file_no_exist_text.rb test/fail_test.rb
```
