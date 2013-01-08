<h1>Steps</h1>
<ul>
<li><code>rails new appname --skip-test-unit</code> creates everything but not the test directory</li>
<li>We are going to add RSPEC this time for test perpose so we need to add gem</li>
<pre>
source 'https://rubygems.org'

gem 'rails', '3.2.10'

group :development, :test do
  gem 'sqlite3', '1.3.5'
  gem 'rspec-rails', '2.11.0'
end

# Gems used only for assets and not required
# in production environments by default.
group :assets do
  gem 'sass-rails',   '3.2.5'
  gem 'coffee-rails', '3.2.2'
  gem 'uglifier', '1.2.3'
end

gem 'jquery-rails', '2.0.2'

group :test do
  gem 'capybara', '1.1.2'
end

group :production do
  gem 'pg', '0.12.2'
end
</pre>
<li><code>bundle install --without production</code></li>
<li><code>rails generate rspec:install</code> to generate rspec</li>
<li>static files can be kept in <code>public</code> directory so we can create <code>public/hello.html</code></li>
<li>We intend to create staticpage and home controller so <code>rails generate controller StaticPages home help --no-test-framework</code>--no-test-framework to suppress the generation of the default RSpec tests, which we won’t be using. CamelCase, which leads to the creation of a controller file written in snake case, so that a controller called StaticPages yields a file called static_pages_controller.rb.Rails generator converts CamelCase to snake case using the underscore method</li>
<li><code>rails generate</code> does not mean creating one file so deleting a file will make trouble while working, <code>rails destroy</code> should be used.
<li><code>rake db:migrate</code>to migrate <code>rake db:rollback</code> to back previous version of db and <code>rake db:migrate VERSION=0</code> or by version number</li>
<li>if we look at <code>controller/StaticPageController</code> we will see that home and help methods are empty so it fails to correspond to "/home" request<li>
<li><code>app/views/static_pages/help.html.erb</code> is what do we see when we visit <code>static_page/home</code></li>

TDD
<li>For request spec <code>rails generate integration_test static_pages</code>creates the static_pages_spec.rb in the spec/requests</li>
<li><code></code></li>
<pre>
describe "Home page" do

  it "should have the content 'Sample App'" do #rspec does not care
    visit '/static_pages/home'
    page.should have_content('Sample App')
  end
end
</pre>
<li>
page.should have_selector('title', :text => "...") =have_selector(’h1’, …)
</li>

<li>Possiblity says that few page should have few structure in common, we can use "embeded ruby" and plae it inside <code>app/views/layouts/application.html.erb</code> inside <code><% ... %></code>, anything inside this tag are considered as ruby code.</li>
<li><code><% yield %></code> replaced other pages content</li>


<li><code>bundle exec rspec spec/requests/static_pages_spec.rb</code>bundle exec to ensure that RSpec runs in the environment specified by our Gemfile</li>
<li>We can manualy add about page rather than using <code>rails generate controller about</code>, we have to add a to <code>config/route.rb</code> a get <code>get "static_page/about"</code> then <code>app/controllers/static_pages_controller.rb</code> we need to add a blank method since it is static as well <code>def about end</code>, then we need a file at view <code>app/views/static_pages</code> names <code>about.html.erb</code><li>

<li> adding <code>guard-rspec</code> to the <code>Gemfile</code> the home.html.erb file is modified, the static_pages_spec.rb, <code>gem 'spork', '0.9.2'</code> boost up test speed</li>
</ul>