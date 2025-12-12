# Hardware Store - Django E-commerce Platform

A full-featured e-commerce platform built with Django for selling hardware products online. Features include product catalog, shopping cart, checkout with cash on delivery, user authentication, and order management.

## Features

- **Product Management**: Browse and search hardware products with categories and detailed descriptions
- **User Authentication**: User registration, login, and profile management using Django Allauth
- **Shopping Cart**: Add, update, and remove items from cart with real-time total calculations
- **Simple Checkout**: Cash on Delivery order processing
- **Order History**: Users can view their past orders and order details
- **Responsive Design**: Mobile-friendly interface with Bootstrap 4
- **AWS S3 Integration**: Optional cloud storage for media files
- **Admin Panel**: Full-featured Django admin for managing products, orders, and users

## Tech Stack

- **Backend**: Django 5.2.8
- **Database**: SQLite (development) / PostgreSQL (production)
- **Frontend**: HTML, CSS, Bootstrap 4, JavaScript
- **Payment**: Cash on Delivery (no payment gateway)
- **Cloud Storage**: AWS S3 (optional)
- **Authentication**: Django Allauth

## Project Structure

```
hardware_store/
├── cart/                   # Shopping cart functionality
├── checkout/               # Checkout and payment processing
├── homepage/               # Landing page
├── products/               # Product catalog and management
├── profiles/               # User profiles and order history
├── templates/              # HTML templates
├── static/                 # Static files (CSS, JS, images)
├── media/                  # User-uploaded files
├── hardware_store/         # Main project settings
├── manage.py               # Django management script
├── requirements.txt        # Python dependencies
└── .env.example           # Environment variables template
```

## Prerequisites

- Python 3.8 or higher
- pip (Python package manager)
- Virtual environment (recommended)
- AWS account (optional, for S3 storage)

## Installation

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd hardware_store
```

### 2. Create and activate virtual environment

**Windows:**
```bash
python -m venv venv
venv\Scripts\activate
```

**macOS/Linux:**
```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Set up environment variables

Copy the example environment file and configure it:

```bash
cp .env.example .env
```

Edit `.env` and update the following variables:

```env
# Generate a new SECRET_KEY
SECRET_KEY=your-secret-key-here

# For development
DEBUG=True
ALLOWED_HOSTS=127.0.0.1,localhost

# Database (SQLite for development)
DATABASE_URL=sqlite:///db.sqlite3

# AWS S3 (Optional - only if you want to use S3 for media files)
USE_AWS=False
AWS_ACCESS_KEY_ID=your-aws-access-key
AWS_SECRET_ACCESS_KEY=your-aws-secret-key
AWS_STORAGE_BUCKET_NAME=your-bucket-name
AWS_S3_REGION_NAME=your-region
```

**Generate a new SECRET_KEY:**
```bash
python -c 'from django.core.management.utils import get_random_secret_key; print(get_random_secret_key())'
```

### 5. Run database migrations

```bash
python manage.py migrate
```

### 6. Create a superuser (admin account)

```bash
python manage.py createsuperuser
```

Follow the prompts to create your admin account.

### 7. Collect static files

```bash
python manage.py collectstatic --noinput
```

### 8. Run the development server

```bash
python manage.py runserver
```

Visit `http://127.0.0.1:8000` in your browser to see the application.

## Configuration

### AWS S3 Setup (Optional)

To use AWS S3 for media file storage:

1. Create an S3 bucket in your AWS console
2. Create an IAM user with S3 access
3. Update your `.env` file with AWS credentials
4. Set `USE_AWS=True` in `.env`



## Usage

### Admin Panel

Access the admin panel at `http://127.0.0.1:8000/admin` to:
- Add/edit/delete products
- Manage categories
- View and process orders
- Manage users

### Adding Products

1. Log in to the admin panel
2. Go to Products section
3. Click "Add Product"
4. Fill in product details (name, description, price, image, etc.)
5. Save the product

## Development

### Running Tests

```bash
python manage.py test
```

### Creating Migrations

After modifying models:

```bash
python manage.py makemigrations
python manage.py migrate
```

## Deployment

### Production Checklist

Before deploying to production:

1. Set `DEBUG=False` in your production environment
2. Generate a new, strong `SECRET_KEY`
3. Update `ALLOWED_HOSTS` with your domain
4. Use PostgreSQL instead of SQLite
5. Set up proper static file serving
6. Configure email backend for order confirmations
7. Enable HTTPS and update security settings




