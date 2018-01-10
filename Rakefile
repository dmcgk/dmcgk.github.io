require 'ra11y'
#require 'html-proofer'

task :test do

  # Test accessibility
  Ra11y::Site.new("./_site").run

  # Test well-formedness
  # Disabled: Causes an issue with the GitHub Pages gem
  #my_github_urls = Regexp.new 'github.com/'
  #my_raw_github_urls = Regexp.new 'raw.githubusercontent.com/'
  #ignored_urls = ["#", my_github_urls, my_raw_github_urls]
  #HTMLProofer.check_directory("./_site", only_4xx: true, check_html: true, url_ignore: ignored_urls).run

end
