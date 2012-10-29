require 'active_record'
require 'yaml'
require 'logger'

task :default => :migrate

desc "Migrate the database through scripts in db/migrate. Target specific version with VERSION=x"
task :migrate => :environment do
  ActiveRecord::Migrator.migrate('migrate', ENV["VERSION"] ? ENV["VERSION"].to_i : nil )
end

task :environment do
  ActiveRecord::Base.establish_connection(YAML::load(File.open('database/configuration/database.yml')))
  ActiveRecord::Base.logger = Logger.new(File.open('database/logs/database.log', 'a'))
end
