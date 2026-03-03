# 🛍️ Local Mart - Digital Product Selling Platform

A comprehensive PHP-based eCommerce platform with user and admin dashboards.

## 📋 Features

### User Features
- ✅ Secure authentication (signup, login, password reset)
- ✅ Product browsing with advanced filters
- ✅ Shopping cart management
- ✅ Wishlist system
- ✅ Product reviews and ratings
- ✅ Order management and tracking
- ✅ Multiple delivery addresses
- ✅ Guest checkout option
- ✅ Recently viewed products

### Admin Features
- ✅ Product management (CRUD operations)
- ✅ Inventory tracking
- ✅ Order management
- ✅ Coupon and discount management
- ✅ User management
- ✅ Sales analytics and reports
- ✅ Settings and configuration

## 🛠️ Tech Stack

- **Frontend**: PHP, Bootstrap 5, JavaScript, HTML5, CSS3
- **Backend**: PHP (OOP Structure)
- **Database**: MySQL 5.7+
- **Security**: BCRYPT password hashing, CSRF protection, Secure sessions
- **API**: RESTful API architecture

## 📁 Project Structure

```
Local Mart/
├── public/
│   ├── index.php              # Main entry point
│   ├── assets/
│   │   ├── css/
│   │   │   └── style.css       # Custom styles
│   │   ├── js/
│   │   │   └── main.js         # Main JavaScript
│   │   ├── images/             # Images
│   │   └── uploads/            # User uploads
├── app/
│   ├── Database.php            # Database connection
│   ├── Model.php               # Base model
│   ├── Auth.php                # Authentication
│   ├── Router.php              # Router
│   ├── controllers/
│   │   ├── Controller.php       # Base controller
│   │   ├── HomeController.php
│   │   ├── AuthController.php
│   │   └── ... (other controllers)
│   ├── models/
│   │   ├── User.php
│   │   ├── Product.php
│   │   ├── Order.php
│   │   └── ... (other models)
│   ├── middleware/
│   │   └── Middleware.php      # Auth & CSRF middleware
│   └── views/
│       ├── layout.php          # Main layout
│       ├── home/
│       ├── auth/
│       └── ... (other views)
├── config/
│   ├── app.php                 # App configuration
│   ├── database.php            # Database configuration
├── database/
│   └── schema.sql              # Database schema
├── .env.example                # Environment template
└── README.md                   # This file
```

## 🚀 Quick Start

### 1. Prerequisites
- PHP 7.4+
- MySQL 5.7+
- XAMPP/WAMP/LAMP
- Composer (optional)

### 2. Installation

```bash
# 1. Clone or download the project to htdocs
cd /xampp/htdocs/Local\ Mart

# 2. Copy environment file
cp .env.example .env

# 3. Update .env with your database credentials
# Edit .env and set:
# DB_HOST=localhost
# DB_NAME=local_mart
# DB_USER=root
# DB_PASS=

# 4. Create database
# Open MySQL and create database:
# CREATE DATABASE local_mart CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

# 5. Import schema
# mysql -u root -p local_mart < database/schema.sql

# 6. Set permissions (Linux/Mac)
chmod 755 public/uploads
chmod 644 public/assets/css/style.css
chmod 644 public/assets/js/main.js
```

### 3. Access Application

- **User Site**: `http://localhost/Local%20Mart/`
- **Admin Panel**: `http://localhost/Local%20Mart/admin/login`

## 🔐 Security Features

✅ **Password Security**: BCRYPT hashing with salts
✅ **SQL Injection Prevention**: Prepared statements
✅ **CSRF Protection**: Token-based verification
✅ **Session Security**: HTTPOnly cookies, SameSite=Strict
✅ **Input Validation**: Server-side validation
✅ **Secure Headers**: Security headers for XSS prevention
✅ **Auto Logout**: Session timeout after 30 minutes inactivity

## 📊 Database Schema

### Core Tables
- `users` - User accounts
- `admins` - Admin accounts with roles
- `categories` - Product categories
- `brands` - Product brands
- `products` - Product catalog
- `product_images` - Product image gallery
- `cart` - Shopping cart items
- `wishlist` - User wishlists
- `orders` - Customer orders
- `order_items` - Items in orders
- `reviews` - Product reviews
- `coupons` - Discount codes

### Additional Tables
- `addresses` - Delivery addresses
- `order_tracking` - Order status updates
- `returns` - Return requests
- `support_tickets` - Customer support
- `abandoned_carts` - Cart recovery
- `activity_logs` - System audit logs
- `settings` - Site configuration

## 🔑 Default Admin Login

```
Email: admin@localmart.com
Password: Admin@12345
```

**IMPORTANT**: Change this immediately after first login!

## 📝 API Endpoints

### Products
- `GET /api/products` - List products
- `GET /api/product/{id}` - Get product details
- `GET /api/products/search?q=search_term` - Search products

### Cart
- `POST /api/cart/add` - Add to cart
- `GET /api/cart/count` - Get cart count

### Wishlist
- `POST /api/wishlist/add` - Add to wishlist
- `POST /api/wishlist/remove` - Remove from wishlist

## 🎨 Customization

### Theme Colors
Edit `public/assets/css/style.css`:
```css
:root {
    --primary: #667eea;
    --secondary: #764ba2;
    --success: #28a745;
    --danger: #dc3545;
}
```

### Configuration
Edit `config/app.php`:
```php
'app_name' => 'Local Mart',
'currency' => 'INR',
'gst' => 18,
'free_delivery_above' => 299,
```

## 📚 Documentation

### Creating a New Controller

```php
// app/controllers/MyController.php
class MyController extends Controller {
    public function index() {
        $data = ['key' => 'value'];
        $this->render('my-view', $data);
    }
    
    public function json($data, $code = 200) {
        $this->json($data, $code);
    }
}
```

### Creating a New Model

```php
// app/models/MyModel.php
class MyModel extends Model {
    protected $table = 'my_table';
    
    public function customMethod() {
        // Your logic
    }
}
```

### Creating a View

```php
// app/views/my-view.php
<?php
$page_title = 'My Page';
ob_start();
?>

<h1><?php echo $page_title; ?></h1>
<!-- Your content -->

<?php
$content = ob_get_clean();
include __DIR__ . '/layout.php';
?>
```

## 🐛 Troubleshooting

### Database Connection Error
- Check MySQL is running
- Verify credentials in `.env`
- Check database exists

### 404 Page Not Found
- Verify URL rewrite is working
- Check router configuration
- Verify controller and method exist

### Session Issues
- Clear browser cookies
- Check PHP session settings
- Verify session.save_path is writable

## 📧 Email Configuration

In `.env`, configure SMTP:
```
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your_email@gmail.com
SMTP_PASS=your_password
```

## 🔄 Future Enhancements

- [ ] Mobile app integration
- [ ] Payment gateway integration (Razorpay, Stripe)
- [ ] Advanced analytics dashboard
- [ ] Email notifications
- [ ] SMS notifications
- [ ] Live chat support
- [ ] AI-powered recommendations
- [ ] Real-time inventory sync
- [ ] Multi-vendor support
- [ ] Advanced reporting

## 📞 Support

For support or issues:
1. Check the troubleshooting section
2. Review error logs in PHP logs
3. Contact the development team

## 📄 License

This project is **proprietary**. Unauthorized copying or distribution is prohibited.

## ✨ Contributing

Contributions are welcome! Please:
1. Create a feature branch
2. Make your changes
3. Submit a pull request

---

**Made with ❤️ for making local shopping digital**
