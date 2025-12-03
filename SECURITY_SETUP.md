# Security Setup Instructions

## IMPORTANT: Exposed Credentials

Your AWS credentials were previously committed to git. Please take these immediate actions:

### 1. Rotate AWS Credentials
- Go to AWS Console → IAM → Users
- Delete or deactivate the exposed access keys:
  - `AKIARZDBIBTA5GFLMR4Y`
- Generate new access keys if needed

### 2. Environment Setup

Create a `.env` file (NOT tracked in git) based on `.env.example`:

```bash
cp .env.example .env
```

Then update `.env` with your actual values:
- Generate a new SECRET_KEY using: `python -c 'from django.core.management.utils import get_random_secret_key; print(get_random_secret_key())'`
- Add new AWS credentials (if needed)

### 3. Database Setup

The database has been removed from git. Set it up again:

```bash
# Activate virtual environment
source venv/Scripts/activate  # Windows
# or
source venv/bin/activate      # Linux/Mac

# Run migrations
python manage.py migrate

# Create superuser
python manage.py createsuperuser
```

### 4. Email Configuration

The project uses console email backend for development. All emails will be printed to the console.

To test email functionality:
- Register a new user
- Check the console for the verification email
- Email verification is set to 'optional', so users can still login without verifying

### 5. Removed Features

- **Stripe Payment Integration**: Completely removed. Orders are now Cash on Delivery.
- The checkout flow no longer requires payment processing

### 6. Security Improvements Made

- ✅ Removed .env and db.sqlite3 from git history
- ✅ Removed all Stripe-related code
- ✅ Configured console email backend
- ✅ Added authorization check to prevent users from viewing others' orders
- ✅ Removed debug print statements
- ✅ Fixed duplicate context processors
- ✅ Email verification changed from mandatory to optional

### 7. Production Checklist

Before deploying to production:

- [ ] Set `DEBUG = False` in settings
- [ ] Configure proper `ALLOWED_HOSTS`
- [ ] Use a production-grade database (PostgreSQL recommended)
- [ ] Configure real email backend (SendGrid, Mailgun, AWS SES, etc.)
- [ ] Set up HTTPS
- [ ] Configure proper static file serving
- [ ] Review and enable CSRF, XSS, and other security middleware
- [ ] Use environment-specific settings files
