Here is a basic README file for setting up Laravel Passport in a Laravel project:

---

# Laravel Passport Authentication

This project demonstrates the use of Laravel Passport to implement OAuth2 authentication in a Laravel application.

## Requirements

- PHP >= 7.3
- Composer
- Laravel >= 8.0
- MySQL or any other supported database

## Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/hardik79/laravel-api.git
   cd laravel-api
   ```

2. **Install dependencies**

   ```bash
   composer install
   ```

3. **Set up environment variables**

   Copy the `.env.example` file to `.env` and update your database credentials and other necessary settings.

   ```bash
   cp .env.example .env
   ```

4. **Generate application key**

   ```bash
   php artisan key:generate
   ```

5. **Run database migrations**

   ```bash
   php artisan migrate
   ```

6. **Install Passport**

   ```bash
   php artisan passport:install
   ```

7. **Check Configure Passport**

   In `config/auth.php`, update the `api` guard to use Passport:

   ```php
   'guards' => [
       'api' => [
           'driver' => 'passport',
           'provider' => 'users',
       ],
   ],
   ```

## Usage

1. **Register a new user**

   Send a `POST` request to `/api/register` with the following fields:

   ```json
   {
       "name": "Your Name",
       "email": "your-email@example.com",
       "password": "your-password",
       "password_confirmation": "your-password"
   }
   ```

2. **Login**

   Send a `POST` request to `/api/login` with the following fields:

   ```json
   {
       "email": "your-email@example.com",
       "password": "your-password"
   }
   ```

   The response will include an access token.

3. **Access protected routes**

   Use the access token to access protected routes by including it in the `Authorization` header:

   ```http
   Authorization: Bearer your-access-token
   ```

## API Endpoints

- **Register**: `POST /api/register`
- **Login**: `POST /api/login`
- **User Profile**: `GET /api/user` (Requires authentication)

## Contributing

Feel free to contribute by creating a pull request. Please follow the contribution guidelines.

## License

This project is licensed under the MIT License.

---

Feel free to customize the README file according to your project's specifics and needs.
