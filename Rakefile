PROJECTS = {
  "rails"      => %w(rails),
  "rspec"      => %w(rspec-dev rspec-expectations rspec-mocks rspec-core rspec rspec-rails),
  "carllerche" => %w(astaire),
  "carlhuda"   => %w(beard bundler),
  "datamapper" => %w(
    dm-transactions
    dm-migrations
    dm-core
    dm-do-adapter
    dm-yaml-adapter
    dm-sqlserver-adapter
    dm-oracle-adapter
    dm-postgres-adapter
    dm-mysql-adapter
    dm-sqlite-adapter
    dm-models
    dm-ar-finders
    dm-rails
    dm-constraints
    do
    dm-timestamps
    extlib
    dm-more
    dm-validations
    dm-types
    dm-tags
    dm-sweatshop
    dm-serializer
    dm-observer
    dm-is-versioned
    dm-is-tree
    dm-is-state_machine
    dm-is-searchable
    dm-is-remixable
    dm-is-nested_set
    dm-is-list
    dm-cli
    dm-aggregates
    dm-adjust
    data_mapper
    dm-active_model
  )
}

PROJECTS.each do |user, names|
  names.each do |name|
    repo = "http://github.com/#{user}/#{name}.git"

    desc "Fetch #{user}/#{name}"
    task name do
      if File.directory?(name)
        Dir.chdir(name) { sh("git pull") }
      else
        sh "git clone #{repo} --recursive"
      end
    end

    task :all => name
  end
end

task :gitignore do
  File.open(".gitignore", 'w') do |f|
    PROJECTS.values.flatten.each do |name|
      f.puts name
    end
  end
end

desc "Fetch all repos"
task :all

task :default => :all
