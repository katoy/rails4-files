
[![Build Status](https://travis-ci.org/katoy/rails4-files.png?branch=master)](https://travis-ci.org/katoy/rails4-files)
[![Dependency Status](https://gemnasium.com/katoy/rails4-files.png)](https://gemnasium.com/katoy/rails4-files)
[![Coverage Status](https://coveralls.io/repos/katoy/rails4-files/badge.png)](https://coveralls.io/r/katoy/rails4-files)

# Rail3-faile の rails4 での作成し直し。


## 空の Rails4 環境の構築

* rails アプリを生成して、 github に commit.

  rails new rails4-files -T
  cd rails4-files
  git add .
  git status
  git commit -am "After rails new rails4-files -T"
  git remote add origin https://github.com/katoy/rails4-files.git
  git push -u origin master
  cp ~/.gemrc .
  rbenv local 2.1.2
  emacs .gitignore
  bundle install
  git mv README.rdoc README.md
  emacs README.md
  rails s

* Gem を設定し、rspec が走るところまでを確認。

  emacs Gemfile
  emacs Rakefile
  bundle update
  emacs config/initializers/secret_token.rb
    # See  http://railstutorial.jp/book/ruby-on-rails-tutorial
    #      リスト 3.2 秘密トークンを動的に生成する。
    #      config/initializers/secret_token.rb
  rails generate rspec:install
  rails g cucumber:install --rspec --capybara
  bundle exec guard init rspec
  bundle exec guard init cucumber
  bundle exec guard init spork
  bundle exec spork rspec --bootstrap
  bundle exec spork cucumber --bootstrap

  rake spec
  rake cucumber
  ls coverage/rcov
  emacs .travis.yml


//--- End of File ---

