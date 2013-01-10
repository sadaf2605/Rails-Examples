<h1>Stpes:</h1>

<ul>
<li><code></code></li>
<li><code><%= link_to "Sign up now!", '#', class: "btn btn-large btn-primary" %></code> changes the code to <code><a href="#" class="btn btn-large btn-primary">Sign up now!</a></code></li>
<li>We need to create <code>app/assets/stylesheets/custom.css.scss</code> file <code>scss</code> file has a lot of good things, like we can use variables, nested css and so on.</li>
<li>In <code>app/assets/stylesheets/custom.css.scss</code> we add <code>@import "bootstrap";</code> which imports default css, then we can add our own csss </li>
<li>Partials, using <code><%= render 'layouts/header' %></code> we can separate them into different files. Then It look for header in <code>app/views/layouts/_home.html.erb</code> directory.</li>
<li>in rspec we can also use <code>visit about_path</code> in stead of <code>visit 'static_pages/about'</code></li>
<li>To change the routes, in <code>config/routes.rb</code> we need to write similar command <code> match '/help',    to: 'static_pages#help'</code></li>
<li>in rspec if a group of description is on same page we can take common of its before activity<code>before { visit root_path }</code></li>
<li><code></code></li>
<li><code></code></li>
<li><code></code></li>
<li><code></code></li>
<li><code></code></li>
<li><code></code></li>
<li><code></code></li>
</ul>