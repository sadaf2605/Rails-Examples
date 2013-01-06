<h1>Steps:</h1>

<ol>
</li><code>rails new first_app</code> in the commandline to create a project and it is going to generate following files:</li>
<table class="tabular"><tbody><tr><th><strong>File/Directory</strong></th><th class="align_left"><strong>Purpose</strong></th></tr><tr class="top_bar"><td class="align_left"><code>app/</code></td><td class="align_left">Core application (app) code, including models, views, controllers, and helpers</td></tr><tr><td class="align_left"><code>app/assets</code></td><td class="align_left">Applications assets such as cascading style sheets (CSS), JavaScript files, and images</td></tr><tr><td class="align_left"><code>config/</code></td><td class="align_left">Application configuration</td></tr><tr><td class="align_left"><code>db/</code></td><td class="align_left">Database files</td></tr><tr><td class="align_left"><code>doc/</code></td><td class="align_left">Documentation for the application</td></tr><tr><td class="align_left"><code>lib/</code></td><td class="align_left">Library modules</td></tr><tr><td class="align_left"><code>lib/assets</code></td><td class="align_left">Library assets such as cascading style sheets (CSS), JavaScript files, and images</td></tr><tr><td class="align_left"><code>log/</code></td><td class="align_left">Application log files</td></tr><tr><td class="align_left"><code>public/</code></td><td class="align_left">Data accessible to the public (e.g., web browsers), such as error pages</td></tr><tr><td class="align_left"><code>script/rails</code></td><td class="align_left">A script for generating code, opening console sessions, or starting a local server</td></tr><tr><td class="align_left"><code>test/</code></td><td class="align_left">Application tests (made obsolete by the <code>spec/</code> directory in <a class="ref" href="static-pages#sec-static_pages_with_rails">Section&nbsp;3.1.2</a>)</td></tr><tr><td class="align_left"><code>tmp/</code></td><td class="align_left">Temporary files</td></tr><tr><td class="align_left"><code>vendor/</code></td><td class="align_left">Third-party code such as plugins and gems</td></tr><tr><td class="align_left"><code>vendor/assets</code></td><td class="align_left">Third-party assets such as cascading style sheets (CSS), JavaScript files, and images</td></tr><tr><td class="align_left"><code>README.rdoc</code></td><td class="align_left">A brief description of the application</td></tr><tr><td class="align_left"><code>Rakefile</code></td><td class="align_left">Utility tasks available via the <code>rake</code> command</td></tr><tr><td class="align_left"><code>Gemfile</code></td><td class="align_left">Gem requirements for this app</td></tr><tr><td class="align_left"><code>Gemfile.lock</code></td><td class="align_left">A list of gems used to ensure that all copies of the app use the same gem versions</td></tr><tr><td class="align_left"><code>config.ru</code></td><td class="align_left">A configuration file for <a href="http://rack.rubyforge.org/doc/">Rack middleware</a></td></tr><tr><td class="align_left"><code>.gitignore</code></td><td class="align_left">Patterns for files that should be ignored by Git</td></tr></tbody></table>

</li>Unfortunately, gem updates often cause minor but potentially confusing breakage, so in this tutorial we’ll include explicit version numbers known to work.</li>
<pre>
source 'https://rubygems.org'

gem 'rails', '3.2.10'

group :development do
  gem 'sqlite3', '1.3.5'
end


# Gems used only for assets and not required
# in production environments by default.
group :assets do
  gem 'sass-rails',   '3.2.5'
  gem 'coffee-rails', '3.2.2'

  gem 'uglifier', '1.2.3'
end

gem 'jquery-rails', '2.0.2'
</pre>
Heroku uses the PostgreSQL database so we need to use this gem:
<pre>
group :production do
  gem 'pg', '0.12.2'
end
</pre>
[<code>gem 'uglifier', '>= 1.2.3'</code> denotes updated version of 1.2.3 and whereas the ~> 3.2.2 notation only performs upgrades to minor point releases]

<li><code>heroku create</code></li>
<li><code>heroku git:remote -a myapp</code></li>
<li><code>git push heroku master</code></li>
</ol>
