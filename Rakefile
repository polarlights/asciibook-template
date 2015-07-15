desc "Build all formats"
task :build => ['build:html', 'build:pdf', 'build:epub', 'build:mobi']

namespace :build do
  desc "Build HTML format"
  task :html do
    `bundle exec asciidoctor -D build/html book.adoc`
  end
  desc "Build PDF format"
  task :pdf do
    `bundle exec asciidoctor-pdf -D build book.adoc`
  end

  desc "Build EPUB format"
  task :epub do
    `bundle exec asciidoctor-epub3 -D build book.adoc`
  end

  desc "Build MOBI format"
  task :mobi do
    `bundle exec asciidoctor-epub3 -D build -a ebook-format=kf8 book.adoc`
  end
end
