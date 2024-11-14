<h1>Spatie Laravel Permission Setup</h1>

<p>Follow these steps to install and configure the Spatie Laravel Permission package.</p>

<h2>Installation Steps</h2>

<h3>Step 1: Install the Spatie Package via Composer</h3>

<p>Run the following command to install the package:</p>

<pre><code>composer require spatie/laravel-permission</code></pre>

<h3>Step 2: Register the Service Provider (if not auto-registered)</h3>

<p>The service provider should automatically get registered. If not, manually add it in your <code>config/app.php</code> file:</p>

<pre><code>
'providers' => [
    // ...
    Spatie\Permission\PermissionServiceProvider::class,
];
</code></pre>

<h3>Step 3: Publish the Migration and Config Files</h3>

<p>Publish the <code>migrations</code> and the <code>config/permission.php</code> config file with:</p>

<pre><code>php artisan vendor:publish --provider="Spatie\Permission\PermissionServiceProvider"</code></pre>

<h3>Step 4: Run the Migrations</h3>

<p>Run the migrations to set up the necessary database tables:</p>

<pre><code>php artisan migrate</code></pre>

<h3>Step 5: Setup the Middleware</h3>

<p>This package provides <code>RoleMiddleware</code>, <code>PermissionMiddleware</code>, and <code>RoleOrPermissionMiddleware</code>. Follow the instructions below based on your Laravel version:</p>

<h4>For Laravel 10</h4>
<p>Add the middleware aliases in your <code>app/Http/Kernel.php</code> file to use them:</p>

<pre><code>
// Laravel 10+ uses $middlewareAliases
protected $middlewareAliases = [
    // ...
    'role' => \Spatie\Permission\Middleware\RoleMiddleware::class,
    'permission' => \Spatie\Permission\Middleware\PermissionMiddleware::class,
    'role_or_permission' => \Spatie\Permission\Middleware\RoleOrPermissionMiddleware::class,
];
</code></pre>

<h4>For Laravel 11</h4>
<p>In Laravel 11, you can add the middleware directly in <code>bootstrap/app.php</code> as follows:</p>

<pre><code>
$middleware->alias([
    'role' => \Spatie\Permission\Middleware\RoleMiddleware::class,
    'permission' => \Spatie\Permission\Middleware\PermissionMiddleware::class,
    'role_or_permission' => \Spatie\Permission\Middleware\RoleOrPermissionMiddleware::class,
]);
</code></pre>

<p>Your Spatie Permission package is now ready to use!</p>

<h3>Additional References</h3>
<ul>
    <li><a href="https://spatie.be/docs" target="_blank">Spatie Documentation</a></li>
    <li><a href="https://www.fundaofwebit.com/post/laravel-10-spatie-user-roles-and-permissions-tutorial#google_vignette" target="_blank">Laravel 10 Spatie User Roles and Permissions Tutorial</a></li>
</ul>
