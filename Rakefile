require 'rubygems'
require 'rake/gempackagetask'

WINDOWS = (PLATFORM =~ /win32|cygwin/ ? true : false) rescue false
SUDO = WINDOWS ? '' : 'sudo'

load 'force_bind.gemspec'
Rake::GemPackageTask.new(SPEC) do |pkg|
  pkg.gem_spec = SPEC
  pkg.need_zip = true
  pkg.need_tar = true
end

desc "Install the gem locally"
task :install => :package do 
  sh "#{SUDO} gem install pkg/#{SPEC.name}-#{SPEC.version}.gem --local"
  sh "rm -rf pkg/#{SPEC.name}-#{SPEC.version}" unless ENV['KEEP_FILES']
end
