require 'ra11y'
require 'html-proofer'

task :test do

  # Test accessibility
  Ra11y::Site.new("./_site").run

  # Test well-formedness
  HTMLProofer.check_directory("./_site", check_html: true, check_favicon: true, check_opengraph: true, check_img_http: true).run

end
