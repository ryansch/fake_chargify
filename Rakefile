require 'rubygems'
require 'bundler'
begin
	Bundler.setup(:default, :development)
rescue Bundler::BundlerError => e
	$stderr.puts e.message
	$stderr.puts "Run `bundle install` to install missing gems"
	exit e.status_code
end
require 'rake'

require 'jeweler'
require 'lib/fake_chargify/version.rb'
Jeweler::Tasks.new do |gem|
	# gem is a Gem::Specification... see http://docs.rubygems.org/read/chapter/20 for more options
	gem.name = "fake_chargify"
	gem.homepage = "http://github.com/ryansch/fake_chargify"
	gem.summary = %Q{Chargify Test Harness}
	gem.description = %Q{Uses FakeWeb to grab requests to Chargify and return customized responses.}
	gem.email = "ryan@instanceinc.com"
	gem.authors = ["Ryan Schlesinger"]
	gem.version = FakeChargify::Version::STRING
	# Include your dependencies below. Runtime dependencies are required when using your gem,
	# and development dependencies are only needed for development (ie running rake tasks, tests, etc)
	#  gem.add_runtime_dependency 'jabber4r', '> 0.1'
	#  gem.add_development_dependency 'rspec', '> 1.2.3'
end
Jeweler::RubygemsDotOrgTasks.new

require 'spec/rake/spectask'
Spec::Rake::SpecTask.new(:spec) do |test|
	test.spec_files = FileList['spec/**/*.rb']
end

require 'rcov/rcovtask'
Rcov::RcovTask.new do |test|
	test.libs << 'test'
	test.pattern = 'test/**/test_*.rb'
	test.verbose = true
end

task :default => :spec

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
	version = File.exist?('VERSION') ? File.read('VERSION') : ""

	rdoc.rdoc_dir = 'rdoc'
	rdoc.title = "fake_chargify #{version}"
	rdoc.rdoc_files.include('README*')
	rdoc.rdoc_files.include('lib/**/*.rb')
end
