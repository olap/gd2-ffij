# -*- ruby -*-

require 'rubygems'
require 'rubygems/package_task'
require 'rake/testtask'
require 'rdoc/task'

if RUBY_VERSION >= '1.9'
  begin
    gem 'psych'
  rescue Exception => e
    # it's okay, fall back on the bundled psych
  end
end

$:.push 'lib'

version = File.read('VERSION') rescue ''

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name        = "gd2-ffij"
    gem.summary     = "gd2-ffij is a refactoring of the Ruby/GD2 library implemented with FFI"
    gem.description = gem.summary
    gem.email       = "dark.panda@gmail.com"
    gem.homepage    = "http://github.com/dark-panda/gd2-ffij"
    gem.authors =    [ "J Smith" ]
    gem.add_dependency "ffi", "~> 1.0.0"
  end
  Jeweler::GemcutterTasks.new
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: sudo gem install jeweler"
end

desc 'Test GD2 interface'
Rake::TestTask.new(:test) do |t|
  t.test_files = FileList['test/**/*_tests.rb']
  t.verbose = !!ENV['VERBOSE_TESTS']
end

desc 'Build docs'
Rake::RDocTask.new do |t|
  require 'rdoc'
  t.title = "gd2-ffij #{version}"
  t.main = 'README'
  t.rdoc_dir = 'doc'
  t.rdoc_files.include('README', 'COPYING', 'COPYRIGHT', 'lib/**/*.rb')
end
