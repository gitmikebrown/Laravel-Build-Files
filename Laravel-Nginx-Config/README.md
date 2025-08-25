# Laravel Nginx Configuration

This repository contains a basic Nginx server block configuration for serving a Laravel application. It’s designed for simplicity, clarity, and easy deployment.

## 📦 File Overview

- `default.conf`: Nginx server block for Laravel, configured to serve from `/var/www/html/laravel/public/`.

## 🚀 Usage

1. **Copy the config file** to your Nginx sites-available directory:
   ```bash
   sudo cp default.conf /etc/nginx/sites-available/laravel.conf
   ```

2. **Enable the site:**
   ```bash
   sudo ln -s /etc/nginx/sites-available/laravel.conf /etc/nginx/sites-enabled/
   ```

3. **Test the configuration**
   ```bash
   sudo nginx -t
   ```

4. **Reload Nginx**
   ```bash
   sudo systemctl reload nginx
   ```

## ⚙️ Requirements

- Laravel app located at `/var/www/html/laravel`
- PHP-FPM running on `127.0.0.1:9000` (or adjust to your socket path, e.g. `unix:/run/php/php8.2-fpm.sock`)
- Nginx installed and running

## 🔐 Optional Enhancements

Uncomment the following lines in `default.conf` for improved security:

```nginx
add_header X-Frame-Options "SAMEORIGIN";
add_header X-XSS-Protection "1; mode=block";
add_header X-Content-Type-Options "nosniff";
```
## 🧠 Notes

- The config uses `try_files` to route requests to Laravel’s `index.php`.
- Dotfiles are blocked by default (commented out—uncomment if needed).
- You can customize `server_name` to match your domain or IP.

## 🛠️ Troubleshooting

- If PHP files download instead of execute, check your `fastcgi_pass` and ensure PHP-FPM is running.
- For production, consider enabling HTTPS and adding rate limiting or caching.


