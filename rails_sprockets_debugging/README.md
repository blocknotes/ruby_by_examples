# Sprockets debugging

Rails - recently I've got an error while compiling the assets of a project for staging... `ExecJS::RuntimeError: SyntaxError: Unexpected token punc «(», expected punc «:»`

Unfortunately there aren't much informations about the files / lines which cause compile errors from Rails / Sprockets / Uglifier.

Here are some useful hints:

```sh
# Clean & compile assets for a specific env
bundle exec rake tmp:clear assets:clean assets:precompile RAILS_ENV=staging
```

```ruby
# Pipeline - List all assets processed by Sprockets
Rails.application.assets.each_file { |f| p f }
```

```ruby
# Look for the first file which causes the error
Rails.application.assets.each_file do |f|
  if f.end_with?( '.js' )
    p f
    Uglifier.compile( File.read( f ) )
  end
end
```

Then you could use directly `uglifyjs FILENAME` if needed.
