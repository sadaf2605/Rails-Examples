<h1>Steps:</h1>
<ul>
<li><code>rails generate scaffold User username:string email:string<code>The argument of the scaffold command is the singular version of the resource name (in this case, User), together with optional parameters for the data model’s attributes.(Note that there is no need to include a parameter for id; it is created automatically by Rails for use as the primary key in the database.)</li>
<li><code>bundle exec rake -T db<code>To see all the Rake tasks available, run</li>
<li><code>bundle exec rake db:migrate<code>in order to ensure that the command uses the version of Rake corresponding to our Gemfile, we need to run rake using bundle exec.</li>
<table class="tabular"><tbody><tr><th class="align_left"><strong>URI</strong></th><th class="align_left"><strong>Action</strong></th><th class="align_left"><strong>Purpose</strong></th></tr><tr class="top_bar"><td class="align_left"><a href="http://localhost:3000/users">/users</a></td><td class="align_left"><code>index</code></td><td class="align_left">page to list all users</td></tr><tr><td class="align_left"><a href="http://localhost:3000/users/1">/users/1</a></td><td class="align_left"><code>show</code></td><td class="align_left">page to show user with id <code>1</code></td></tr><tr><td class="align_left"><a href="http://localhost:3000/users/new">/users/new</a></td><td class="align_left"><code>new</code></td><td class="align_left">page to make a new user</td></tr><tr><td class="align_left"><a href="http://localhost:3000/users/1/edit">/users/1/edit</a></td><td class="align_left"><code>edit</code></td><td class="align_left">page to edit user with id <code>1</code></td></tr></tbody></table>

<li>in <code>config/routes.rb</code> we have <code>resources :users</code> and in <code>app/controllers/</code> we do have <code>users_controller</code>, in this file all the methods are responsible to handle respective routies of their name. </li>
<li>Weekness of scaffolding are that: No data validations, No authentication, No tests, No layout, No real understanding.</li>
<li> Now if we do <code>rails generate scaffold Micropost content:string user_id:integer<code> it is going to create resources: microposts in the route and microposts controller</li>
<table class="tabular"><tbody><tr><th class="align_left"><strong>HTTP request</strong></th><th class="align_left"><strong>URI</strong></th><th class="align_left"><strong>Action</strong></th><th class="align_left"><strong>Purpose</strong></th></tr><tr class="top_bar"><td class="align_left"><tt>GET</tt></td><td class="align_left">/microposts</td><td class="align_left"><code>index</code></td><td class="align_left">page to list all microposts</td></tr><tr><td class="align_left"><tt>GET</tt></td><td class="align_left">/microposts/1</td><td class="align_left"><code>show</code></td><td class="align_left">page to show micropost with id <code>1</code></td></tr><tr><td class="align_left"><tt>GET</tt></td><td class="align_left">/microposts/new</td><td class="align_left"><code>new</code></td><td class="align_left">page to make a new micropost</td></tr><tr><td class="align_left"><tt>POST</tt></td><td class="align_left">/microposts</td><td class="align_left"><code>create</code></td><td class="align_left">create a new micropost</td></tr><tr><td class="align_left"><tt>GET</tt></td><td class="align_left">/microposts/1/edit</td><td class="align_left"><code>edit</code></td><td class="align_left">page to edit micropost with id <code>1</code></td></tr><tr><td class="align_left"><tt>PUT</tt></td><td class="align_left">/microposts/1</td><td class="align_left"><code>update</code></td><td class="align_left">update micropost with id <code>1</code></td></tr><tr><td class="align_left"><tt>DELETE</tt></td><td class="align_left">/microposts/1</td><td class="align_left"><code>destroy</code></td><td class="align_left">delete micropost with id <code>1</code></td></tr></tbody></table>
<li>If we want to add conditions for validations, we can add to<code>app/models/micropost.rb</code>, this <code>validates :content, :length => { :maximum => 140 }</code> which will pre check.</li>
<li>In a blog a User is going to have more than one microblogs, on the other hand a microblog can only belong to a user so to make this relation we have to go to <code>app/models/user.rb<code> and add <code>has_many :microposts</code> and <code>app/models/microposts.rb<code> and add <code>belong_to :user</code></li>
<li>We can get access to db using Ruby console <code>rails console<code> </li>
<pre>
user_first = User.first
user_first.microposts
</pre>
</ul>