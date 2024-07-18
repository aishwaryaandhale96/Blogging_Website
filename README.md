# Flask Blog Application

This is a Flask-based web application for creating and managing blog posts. It features user authentication, post creation, editing, commenting, and more.

## Features

- User registration and authentication
- Create, edit, and delete blog posts
- Add comments to blog posts
- Use CKEditor for rich-text editing
- Admin-only access for creating, editing, and deleting posts

## Installation guide

1. **Clone the repository:**
    ```bash
    git clone https://github.com/aishwaryaandhale96/Blogging_Website.git
    cd flask-blog
    ```

2. **Create and activate a virtual environment:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    ```

3. **Install the dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

4. **Run code:**
   ```bash
   python main.py
   ```   

## Usage

### User Registration

Users can register by providing an email, password, and name. The password is hashed for security.

### User Login

Registered users can log in using their email and password. Passwords are verified using a hashed comparison.

### Creating Posts

Logged-in users with admin privileges can create new blog posts using a form with fields for the title, subtitle, image URL, and content.

### Editing Posts

Admin users can edit existing posts. The edit form is pre-filled with the current post data.

### Deleting Posts

Admin users can delete posts. Once deleted, posts are permanently removed from the database.

### Adding Comments

Logged-in users can add comments to blog posts. Comments are associated with both the post and the user who created them.

## Forms

### CreatePostForm

Form for creating and editing blog posts.

- `title`: Title of the blog post (StringField)
- `subtitle`: Subtitle of the blog post (StringField)
- `img_url`: URL of the blog post image (StringField)
- `body`: Content of the blog post (CKEditorField)
- `submit`: Submit button (SubmitField)

### RegisterForm

Form for user registration.

- `email`: User's email (StringField)
- `password`: User's password (PasswordField)
- `name`: User's name (StringField)
- `submit`: Submit button (SubmitField)

### LoginForm

Form for user login.

- `email`: User's email (StringField)
- `password`: User's password (PasswordField)
- `submit`: Submit button (SubmitField)

### CommentForm

Form for adding comments to blog posts.

- `comment_text`: Text of the comment (CKEditorField)
- `submit`: Submit button (SubmitField)

## Database Models

### BlogPost

Represents a blog post.

- `id`: Primary key (Integer)
- `author_id`: Foreign key to User (Integer)
- `title`: Title of the post (String)
- `subtitle`: Subtitle of the post (String)
- `date`: Date of the post (String)
- `body`: Content of the post (Text)
- `img_url`: Image URL of the post (String)
- `comments`: Relationship to Comment

### User

Represents a registered user.

- `id`: Primary key (Integer)
- `email`: User's email (String)
- `password`: User's hashed password (String)
- `name`: User's name (String)
- `posts`: Relationship to BlogPost
- `comments`: Relationship to Comment

### Comment

Represents a comment on a blog post.

- `id`: Primary key (Integer)
- `text`: Text of the comment (Text)
- `author_id`: Foreign key to User (Integer)
- `post_id`: Foreign key to BlogPost (Integer)
- `comment_author`: Relationship to User
- `parent_post`: Relationship to BlogPost


