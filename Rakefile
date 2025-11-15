require 'yaml'

Config = YAML.load(File.open("./_config.yml"))

task default: %w[init]

desc "init environment"
task :init do
  sh "rake --tasks"
end

desc "run jekyll server"
task :serve do
  sh "bundle exec jekyll serve"
end


desc "clean blog static files"
task :clean do
  sh "bundle exec jekyll clean"
  puts '----'
  puts '[clean] done'
end

desc "build blog static files"
task :build  => [:clean]do
  sh "bundle exec jekyll build"

  puts '----'
  puts '[build] done'
end

desc "deploy github pages"
task :deploy => [:build] do

  pages_repository = Config["pages_repository"]

  sh "cd _site && \
   git init && \
   git add . && \
   git commit -m 'update blog' ; \
   git remote add origin #{pages_repository} &&  \
   git push --set-upstream origin main -f"

   puts '---'
   puts '[delpoy] done'
end

desc "push blog"
task :push do
  sh "git add . && \
   git commit -m 'update blog' && \
   git push"

   puts '---'
   puts '[push] done'
end


desc "push blog & deploy"
task :pd => [:push, :deploy] do
   puts '[push & deploy] done'
end


desc "create a new post"
task :new, [:post_name]  do |t, args|
  post_name = args[:post_name]
  date = Time.now.strftime("%Y-%m-%d")
  time = Time.now.strftime("%Y-%m-%d %H:%M:%S %z")
  file_name = "#{date}-#{post_name}"

  temple = "---
title: #{post_name}
date: #{time}
categories: 未定义
layout: post
location: null
author: #{Config["author"]}
email: #{Config["email"]}
---
"
  File.open("./_posts/#{file_name}.md", 'w') do |f|
    f << temple
  end

  puts "[create post] #{file_name}"
end




# alias task
def alias_task(tasks)
  tasks.each do |new_name, old_name|
      task new_name, [*Rake.application[old_name].arg_names] => [old_name]
  end
end

alias_task [
  [:s, :serve],
  [:c, :clean],
  [:b, :build],
  [:d, :deploy],
  [:p, :push]
]
