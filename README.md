# Bad test

Reproducing problem with: https://github.com/rails/rails/pull/51005

```bash
# Returns exit code 0
bin/rails test test/bad_require_test.rb test/fail_test.rb; echo $?

# Could not load test file: test/bad_require_test.rb. Did you mean? test/fail_test.rb
# Running 0 tests in a single process (parallelization threshold is 50)
# Run options: --seed 3296
#
# # Running:
#
#
#
# Finished in 0.000129s, 0.0000 runs/s, 0.0000 assertions/s.
# 0 runs, 0 assertions, 0 failures, 0 errors, 0 skips
# 0


# undefined method `squish' for an instance of String (NoMethodError)
bin/rails test test/file_no_exist_text.rb test/fail_test.rb; echo $?

# /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/test_unit/runner.rb:14:in `initialize': undefined method `squish' for an instance of String (NoMethodError)
#
#        super(<<~MESSAGE.squish)
#                        ^^^^^^^
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/test_unit/runner.rb:69:in `new'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/test_unit/runner.rb:69:in `rescue in block in load_tests'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/test_unit/runner.rb:61:in `block in load_tests'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/test_unit/runner.rb:60:in `each'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/test_unit/runner.rb:60:in `load_tests'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/test_unit/runner.rb:52:in `run'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/commands/test/test_command.rb:33:in `perform'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/thor-1.3.1/lib/thor/command.rb:28:in `run'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/thor-1.3.1/lib/thor/invocation.rb:127:in `invoke_command'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/command/base.rb:178:in `invoke_command'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/thor-1.3.1/lib/thor.rb:527:in `dispatch'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/command/base.rb:73:in `perform'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/command.rb:71:in `block in invoke'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/command.rb:149:in `with_argv'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/command.rb:69:in `invoke'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/commands.rb:18:in `<main>'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/3.3.0/bundled_gems.rb:74:in `require'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/3.3.0/bundled_gems.rb:74:in `block (2 levels) in replace_require'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/bootsnap-1.18.3/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:30:in `require'
#	from bin/rails:4:in `<main>'
#/Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/3.3.0/bundled_gems.rb:74:in `require': cannot load such file -- /Users/bensheldon/Repositories/bensheldon/rails_new/missing_test/test/file_no_exist_text.rb (LoadError)
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/3.3.0/bundled_gems.rb:74:in `block (2 levels) in replace_require'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/bootsnap-1.18.3/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:30:in `require'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/test_unit/runner.rb:61:in `block in load_tests'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/test_unit/runner.rb:60:in `each'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/test_unit/runner.rb:60:in `load_tests'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/test_unit/runner.rb:52:in `run'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/commands/test/test_command.rb:33:in `perform'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/thor-1.3.1/lib/thor/command.rb:28:in `run'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/thor-1.3.1/lib/thor/invocation.rb:127:in `invoke_command'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/command/base.rb:178:in `invoke_command'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/thor-1.3.1/lib/thor.rb:527:in `dispatch'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/command/base.rb:73:in `perform'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/command.rb:71:in `block in invoke'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/command.rb:149:in `with_argv'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/command.rb:69:in `invoke'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/bundler/gems/rails-b291408f9381/railties/lib/rails/commands.rb:18:in `<main>'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/3.3.0/bundled_gems.rb:74:in `require'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/3.3.0/bundled_gems.rb:74:in `block (2 levels) in replace_require'
#	from /Users/bensheldon/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/bootsnap-1.18.3/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:30:in `require'
#	from bin/rails:4:in `<main>'
# 1
```
