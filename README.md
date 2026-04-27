# Python_Blog

A simple multi-user blogging web app written in Python with Flask and MongoDB. Users can register, log in, create blogs, and add posts to those blogs.

## Tech Stack

- Python
- Flask (web framework, server-side rendered Jinja templates)
- MongoDB (via PyMongo) for data storage

## Project Structure

```
app.py              # Flask routes (home, login, register, blogs, posts)
common/database.py  # Thin PyMongo wrapper (initialize / insert / find)
models/
  user.py           # User model (register, login, get blogs)
  blog.py           # Blog model (create, list posts)
  post.py           # Post model (create, fetch by blog)
templates/          # Jinja templates (home, login, register, new_blog, posts, ...)
static/css/         # Stylesheets
```

Data is stored in three MongoDB collections: `users`, `blogs`, `posts`, inside a database named `fullstack`.

## Prerequisites

- Python 3
- A running MongoDB instance (defaults to `mongodb://127.0.0.1:27017`)

## Setup and Run

1. Clone the repo and enter it:
   ```
   git clone https://github.com/Arjun-B-J/Python_Blog.git
   cd Python_Blog
   ```

2. Install dependencies:
   ```
   pip install flask pymongo
   ```

3. Make sure MongoDB is running locally on the default port (27017). To use a different MongoDB instance, edit the `URI` constant in `common/database.py`.

4. Run the app:
   ```
   python app.py
   ```

   The server starts on `http://127.0.0.1:4995` in debug mode.

## Configuration

- `FLASK_SECRET_KEY`: Set this environment variable in production to a strong, random secret used to sign Flask session cookies. If unset (e.g. during local development), the app falls back to a random per-process key generated via `os.urandom(64)`, which means existing sessions are invalidated on each restart. Always set `FLASK_SECRET_KEY` in production so sessions persist across restarts.

## Usage

- Visit `/register` to create an account.
- Log in at `/login`.
- After logging in you are redirected to your blogs page where you can create a new blog and add posts to it.
