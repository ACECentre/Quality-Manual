require 'fileutils'
require 'tmpdir'
require 'rake'

desc 'Generate deck from Travis CI and publish to GitHub Pages.'
task :travis do
  # if this is a pull request, do a simple build of the site and stop
  if ENV['TRAVIS_PULL_REQUEST'].to_s.to_i > 0
    puts 'Pull request detected. Doing nowt.'
    next
  end

  repo = %x(git config remote.origin.url).gsub(/^git:/, 'https:').strip
  deploy_url = repo.gsub %r{https://}, "https://#{ENV['GH_TOKEN']}@"
  deploy_branch = repo.match(/github\.io\.git$/) ? 'master' : 'gh-pages'
  rev = %x(git rev-parse HEAD).strip

  Dir.mktmpdir do |dir|
    sh "git clone --branch gh-pages #{repo} #{dir}"
    sh "asciidoctor Main.adoc -D #{dir} -o index.html"
    sh "asciidoctor -r asciidoctor-pdf -b pdf Main.adoc -o Main.pdf"
    sh "asciidoctor -b docbook5 Main.adoc -D #{dir} -o Main.xml"
    sh "pandoc #{dir}/Main.xml -f docbook -t docx -o ./Main.docx"
    Dir.chdir dir do
      # setup credentials so Travis CI can push to GitHub
      verbose false do
        sh "git config user.name '#{ENV['GIT_NAME']}'"
        sh "git config user.email '#{ENV['GIT_EMAIL']}'"
      end

      sh 'git add --all'
      sh "git commit -m 'Built from #{rev}'."
      verbose false do
        sh "git push -q #{deploy_url} #{deploy_branch}"
      end
    end
  end
end
