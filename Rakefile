require 'rake/testtask'
Rake::TestTask.new do |t|
  t.libs << "test"
  t.test_files = FileList['test/*_test.rb']
  t.verbose = true
end

desc 'Dumps output to a CSS file for testing'
task :debug do
  require 'sass'
  require './lib/bootstrap-sass/compass_functions'
  require './lib/bootstrap-sass/rails_functions'
  path = './vendor/assets/stylesheets'
  %w(bootstrap bootstrap-responsive).each do |file|
    engine = Sass::Engine.for_file("#{path}/_#{file}.scss", syntax: :scss, load_paths: [path])
    File.open("./#{file}.css", 'w') { |f| f.write(engine.render) }
  end
end

require 'jeweler'
Jeweler::Tasks.new do |gem|
  gem.name = "querobolsa-bootstrap-sass"
  gem.version = '2.0.4.2'
  gem.authors = ["Thomas McDonald"]
  gem.email = 'dev@querobolsa.de'
  gem.summary = "Twitter's Bootstrap + Sass"
  gem.description = "Twitter's Bootstrap, converted to Sass and ready to drop into Rails or Compass"
  gem.homepage = "http://github.com/thiagobrandam/querobolsa-bootstrap-sass"

  gem.add_development_dependency 'compass'
  gem.add_development_dependency 'sass-rails', '~> 3.1'

  gem.files = Dir["vendor/**/*.{scss,js,png}"] + Dir["lib/**/*"] + Dir["templates/**/*"] + ["README.md", "LICENSE"]
end
Jeweler::RubygemsDotOrgTasks.new

task default: :test

