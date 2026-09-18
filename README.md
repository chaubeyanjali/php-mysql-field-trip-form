# PHP MySQL Field Trip Form

A simple web form built with PHP and MySQL that lets students register for a field trip. Submitted details are validated by the browser and saved to a MySQL database, with a confirmation message shown on success.

## Features

- Single-page HTML form styled with custom CSS and Google Fonts
- Collects name, age, gender, email, phone, and additional notes
- Saves each submission to a MySQL database via `mysqli`
- Displays a confirmation message after successful submission

## Tech Stack

- PHP (procedural, `mysqli` extension)
- MySQL
- HTML / CSS

## Project Structure

```
.
├── index.php     # Form UI + PHP logic to insert submissions into MySQL
├── style.css     # Styling for the form
└── bg.avif       # Background image
```

## Database Setup

This project expects a database named `trip` with a table named `trip`. Create it with:

```sql
CREATE DATABASE IF NOT EXISTS trip;

USE trip;

CREATE TABLE IF NOT EXISTS trip (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    age VARCHAR(10),
    gender VARCHAR(20),
    email VARCHAR(100),
    phone VARCHAR(20),
    other TEXT,
    dt TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

You can run this via the MySQL CLI or a tool like phpMyAdmin.

## Getting Started

1. **Install a local server stack** such as XAMPP, WAMP, or MAMP (PHP + MySQL + Apache).
2. **Clone this repository** into your server's web root (e.g. `htdocs`):
   ```bash
   git clone https://github.com/chaubeyanjali/php-mysql-field-trip-form.git
   ```
3. **Create the database and table** using the SQL above.
4. **Update database credentials** in `index.php` if they differ from the defaults (`localhost` / `root` / no password):
   ```php
   $server = "localhost";
   $username = "root";
   $password = "";
   ```
5. **Start Apache and MySQL**, then open the form in your browser, e.g.:
   ```
   http://localhost/php-mysql-field-trip-form/index.php
   ```
6. Fill out and submit the form — a confirmation message will appear once your details are saved.

## Known Limitations / Ideas for Improvement

- Form values are inserted directly into the SQL query, which is vulnerable to SQL injection. Consider switching to **prepared statements** (`mysqli::prepare`) for safer input handling.
- No server-side validation is currently performed on submitted fields (e.g. age as a number, phone format).
- Database credentials are hard-coded in `index.php`; consider moving them to a config file or environment variables for real deployments.

## License

No license specified yet. Add a `LICENSE` file if you'd like to make reuse terms explicit.
