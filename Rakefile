require 'rubygems'
require 'rake/gempackagetask'
require 'rake/rdoctask'
require 'spec/rake/spectask'

PLUGIN = 'merb_restcontroller'
NAME = 'merb_restcontroller'
GEM_VERSION = '0.0.1'
AUTHORS = 'Maciej Piechotka'
EMAIL = nil
HOMEPAGE = nil
SUMMARY = 'Plugin for Merb allowing to keep the rest controllers DRY'

spec = Gem::Specification.new do |s|
  s.name = NAME
  s.version = GEM_VERSION
  s.platform = Gem::Platform::RUBY
  s.has_rdoc = true
  s.extra_rdoc_files = %w{README LICENSE TODO}
  s.summary = SUMMARY
  s.description = s.summary
  s.author = AUTHOR
  s.homepage = HOMEPAGE
  s.add_dependency 'merb_core', '>=0.9.0'
  s.require_path = 'lib'
  s.autorequire = PLUGIN
  s.files = %w{README LICENSE Rakefile TODO} + Dir.glob("lib/**/*")
end

Rake::GemPackageTask.new(spec) do |pkg|
  pkg.gem_spec = spec
end

Rake::RDocTask.new do |rd|
  rd.rdoc_dir = "doc"
  rd.rdoc_files.include "lib/**/*.rb"
end

desc "Run all specs"
Spec::Rake::SpecTask.new('specs') do |st|
  st.libs = ['lib', 'spec']
  st.spec_files = FileList['spec/**/*.rb']
  st.spec_opts = ['--format specdoc', '--color']
end

desc "Run rcov"
Spec::Rake::SpecTask.new('rcov') do |rct|
  rct.libs = ['lib', 'spec']
  rct.rcov = true
  rct.rcov_opts = ['-x gems', '-x usr', '-x spec']
  rct.spec_files = FileList['spec/**/*.rb']
  rct.spec_opts = ['--format specdoc', '--color']
end
