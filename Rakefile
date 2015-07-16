require 'bundler/setup'
require 'asciidoctor'

book = Asciidoctor.load_file 'book.adoc'
version = book.attributes['revnumber']

desc "Run build task"
task :default => :build

desc "Build all formats"
task :build => ['build:html', 'build:pdf', 'build:epub', 'build:mobi']

namespace :build do
  desc "Build HTML format"
  task :html do
    `bundle exec asciidoctor -D build/book-#{version} -o index.html book.adoc`
  end

  desc "Build PDF format"
  task :pdf do
    `bundle exec asciidoctor -r asciidoctor-pdf -D build -o book-#{version}.pdf book.adoc`
  end

  desc "Build EPUB format"
  task :epub do
    `bundle exec asciidoctor -r asciidoctor-epub3 -D build -o book-#{version}.epub book.adoc`
  end

  desc "Build MOBI format"
  task :mobi do
    `bundle exec asciidoctor -r asciidoctor-epub3 -D build -o book-#{version}.mobi -a ebook-format=kf8 book.adoc`
  end
end

desc "Clean build results"
task :clean do
  rm_r Dir['build/*']
end
