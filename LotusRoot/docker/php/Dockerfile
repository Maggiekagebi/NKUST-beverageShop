FROM php:8.2-fpm

# 安裝系統套件
RUN apt-get update && apt-get install -y \
    git \
    unzip \
    curl \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    && docker-php-ext-install pdo pdo_mysql mbstring exif pcntl bcmath gd

# 安裝 Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

# 設置工作目錄
WORKDIR /var/www

# 複製 Laravel 專案
COPY . .

# 設定權限
RUN chown -R www-data:www-data /var/www/storage /var/www/bootstrap/cache

# 執行 PHP-FPM
CMD ["php-fpm"]