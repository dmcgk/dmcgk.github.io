require 'html-proofer'

task :test do
  HTMLProofer.check_directory("./_site", check_html: true, check_favicon: true, check_opengraph: true, check_img_http: true).run
end
