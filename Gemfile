# frozen_string_literal: true

source 'https://rubygems.org'

git_source(:github) { |repo_name| "https://github.com/#{repo_name}" }

# Synchronize with https://pages.github.com/versions
ruby '>=2.7.1'

gem 'github-pages', group: :jekyll_plugins

if Gem::Version.new(RUBY_VERSION) >= Gem::Version.new('3.0.0')
    gem 'webrick', '>= 1.6.1'
end

gem 'wdm', '>= 0.1.0' if Gem.win_platform?
