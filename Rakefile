require 'rspec/core/rake_task'
require File.dirname(__FILE__) + '/lib/botsy/version'
 
task :build => :test do
  system "gem build botsy.gemspec"
end

task :release => :build do
  # tag and push
  system "git tag v#{Botsy::VERSION}"
  system "git push origin --tags"
  # push the gem
  system "gem push botsy-#{Botsy::VERSION}.gem"
end
 
RSpec::Core::RakeTask.new(:test) do |t|
  t.pattern = 'spec/**/*_spec.rb'
  fail_on_error = true # be explicit
end
 
RSpec::Core::RakeTask.new(:rcov) do |t|
  t.pattern = 'spec/**/*_spec.rb'
  t.rcov = true
  fail_on_error = true # be explicit
end
