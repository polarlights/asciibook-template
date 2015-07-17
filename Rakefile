require 'bundler/setup'
require 'asciidoctor'

file_path = 'asciibook.adoc'
doc = Asciidoctor.load_file file_path
docname = doc.attributes['docname']
version = doc.attributes['revnumber']

desc "Run build task"
task :default => :build

desc "Build all formats"
task :build => ['build:html', 'build:pdf', 'build:epub', 'build:mobi']

namespace :build do
  desc "Build HTML format"
  task :html do
    `bundle exec asciidoctor -D build/#{docname}-#{version} -o index.html #{file_path}`
  end

  desc "Build PDF format"
  task :pdf do
    `bundle exec asciidoctor -r asciidoctor-pdf -D build -o #{docname}-#{version}.pdf #{file_path}`
  end

  desc "Build EPUB format"
  task :epub do
    `bundle exec asciidoctor -r asciidoctor-epub3 -D build -o #{docname}-#{version}.epub #{file_path}`
  end

  desc "Build MOBI format"
  task :mobi do
    `bundle exec asciidoctor -r asciidoctor-epub3 -D build -o #{docname}-#{version}.mobi -a ebook-format=kf8 #{file_path}`
  end
end

desc "Clean build results"
task :clean do
  rm_r Dir['build/*']
end
