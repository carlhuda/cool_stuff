PROJECTS = {
  "rails"         => %w(rails arel jquery-ujs prototype-ujs rails_upgrade sass-rails),
  "rack"          => %w(rack rack-contrib),
  "rspec"         => %w(rspec-dev rspec-expectations rspec-mocks rspec-core rspec rspec-rails),
  "josh"          => %w(rack-mount),
  "nex3"          => %w(haml),
  "cowboyd"       => %w(therubyracer),
  "jashkenas"     => %w(docco coffee-script),
  "documentcloud" => %w(underscore backbone),
  "chriseppstein" => %w(compass),
  "joshbuddy"     => %w(usher),
  "carllerche"    => %w(astaire),
  "carlhuda"      => %w(beard bundler janus),
  "tomhuda"       => %w(metamorph.js),
  "jnicklas"      => %w(capybara),
  "thoughtbot"    => %w(factory_girl paperclip),
  "mislav"        => %w(will_paginate),
  "dkubb"         => %w(veritas),
  "hassox"        => %w(warden),
  "brynary"       => %w(rack-test),
  "jquery"        => %w(jquery jquery-ui qunit),
  "plataformatec" => %w(simple_form devise responders mail_form devise_example),
  "rtomayko"      => %w(rack-cache ronn rocco),
  "mikel"         => %w(mail),
  "lsegal"        => %w(yard),
  "kevwil"        => %w(aspen),
  "brotherbard"   => %w(gitx),
  "eventmachine"  => %w(eventmachine),
  "macournoyer"   => %w(thin),
  "igrigorik"     => %w(em-http-request),
  "evanphx"       => %w(rubinius kpeg),
  "sproutcore"    => %w(sproutcore-ui sproutcore20 sproutguides starter-kit),
  "getbpm"        => %w(bpm spade),
  "ialexi"        => %w(hedwig),
  "wycats"        => %w(handlebars.js muse thor nerdtree moneta guides net-http sproutcore-chrome-extension net2-reactor),
  "ttilley"       => %w(fssm),
  "sandro"        => %w(ruby-fsevent),
  "rubygems"      => %w(rubygems),
  "ruby"          => %w(ruby),
  "drbrain"       => %w(net-http-persistent),
  "jimweirich"    => %w(rake),
  "geemus"        => %w(fog excon),
  "sstephenson"   => %w(sprockets),
  "zaach"         => %w(jison cafe jsonlint zii-jsconf2010-talk orderly.js),
  "chriseppstein" => %w(sass),
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
      puts "* #{user}/#{name}"
      if File.directory?(name)
        Dir.chdir(name) do
          sh "git pull -q"
          sh "git submodule update"
        end
      else
        sh "git clone #{repo} --recursive"
      end
    end

    task :all => name
  end
end

task :gitignore do
  File.open(".gitignore", 'w') do |f|
    f.puts ".bundle"
    PROJECTS.values.flatten.each do |name|
      f.puts name
    end
  end
end

desc "Make a Gemfile"
task :gemfile do
  File.open("Gemfile", "w") do |f|
    f.puts "source 'http://rubygems.org'"
    f.puts "path   '.'"
    f.puts
    PROJECTS.values.flatten.each do |name|
      next if name =~ /^(dm|do|qunit|jquery|prototype|devise_example|rspec-dev|veritas|rails_upgrade)/

      f.puts "gem '#{name}'"
    end
  end
end

desc "Fetch all repos"
task :all

task :default => :all
