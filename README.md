# PHP Web Interface - `php_interface`

The PHP web interface demonstrates server-side rendering with gRPC data. It interacts with the `playing_field` service to load subscribed strategies and initiate matchups.

```powershell
# Install the PHP dependencies
composer install

# Generate the PHP gRPC client stubs
Update-PhpGrpc -ProtosArray @("model", "playing_field")

# Navigate to the public directory
cd ./public

# Start the PHP built-in server
php -S localhost:$env:PHP_INTERFACE_PORT
```

## Building the Project with Nix

To build the project using Nix, you can run the following command:

```sh
nix build --option sandbox false
```

### Note:

Disabling the sandbox is necessary for this build because the `php` command needs network access to download Composer packages.
While this approach works for now, we are exploring more elegant solutions to handle dependencies in a sandboxed environment.
This includes pre-fetching dependencies or using local caches to ensure a secure and reproducible build process.
