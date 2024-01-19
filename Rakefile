this_dir = File.expand_path('..', __FILE__)
lib_dir  = File.join(this_dir, 'lib')
$LOAD_PATH.unshift(lib_dir) unless $LOAD_PATH.include?(lib_dir)

require 'terminfo/version'
require 'rubygems'
require 'hoe'
require 'rake/extensiontask'

PROJECT_NAME = 'terminfo-for-ruby-3'

Hoe.plugin :bundler
Hoe.plugin :gemspec

Hoe.spec PROJECT_NAME do
  developer "Tanaka Akira", "akr@fsij.org"
  license "modified BSD"

  self.version     = TermInfo::VERSION
  self.readme_file = "README.md"

  self.extra_dev_deps <<
		%w(rdoc ~>4.0) <<
		%w(rake-compiler >=0) <<
		%w(rake ~>13) <<
		%w(hoe-bundler ~>1.2) <<
		%w(hoe-gemspec ~>1.0) <<
		%w(hoe-version ~>1.2) <<
		%w(hoe ~>3.14)
		
  self.spec_extras = {
    extensions: %w( ext/terminfo/extconf.rb ),
    required_ruby_version: '>= 1.9'
  }

  self.clean_globs += %w(
    lib/terminfo/*.so
  )

  Rake::ExtensionTask.new('terminfo', spec) do |ext|
    ext.ext_dir = 'ext/terminfo'
    ext.lib_dir = File.join('lib', 'terminfo')
  end
end