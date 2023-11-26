require 'rake/testtask'
require 'find'
require "bundler/gem_tasks"

desc 'Run tests'
task :default => :test

desc 'Say hello'
task :hello do
  puts "Hello there. This is the 'hello' task."
end

Rake::TestTask.new(:test) do |t|
  t.libs << "test"
  t.libs << "lib"
  t.test_files = FileList['test/**/*_test.rb']
end

desc 'Create main, test, and pedac files'
task :create, [:file_name] do |t, arr|
  sh "touch ./test/#{arr[:file_name]}.rb ./test/#{arr[:file_name]}_test.rb ./test/#{arr[:file_name]}_pedac.txt"
end

desc 'lists every file except .'
task :list_files do
  results = []
  Find.find("/Users/justinshaber/coding_projects/practice_project") do |path|
    # if FileTest.directory?(path)
    #   if File.basename(path).start_with?('.')
    #     Find.prune       # Don't look any further into this directory.
    #   else
    #     next
    #   end
    # else
    #   if File.basename(path).start_with?('.')
    #     next
    #   else
    #     results << path
    #   end
    # end

    next if path.include?('/.')
    results << path if File.file?(path)
  end
  puts results
end