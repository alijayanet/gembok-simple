# 🚀 GEMBOK - Modern ISP Management System

<p align="center">
  <img src="https://img.shields.io/badge/version-2.0.0-blue?style=for-the-badge" alt="Version">
  <img src="https://img.shields.io/badge/license-MIT-green?style=for-the-badge" alt="License">
  <img src="https://img.shields.io/badge/php-%3E%3D7.4-8892BF?style=for-the-badge&logo=php" alt="PHP">
  <img src="https://img.shields.io/badge/mysql-%3E%3D5.7-4479A1?style=for-the-badge&logo=mysql" alt="MySQL">
</p>

<p align="center">
  <strong>All-in-one solution for Internet Service Providers with seamless MikroTik and GenieACS integration</strong>
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/alijayanet/gembok-simple/main/assets/sim4.png" alt="Gembok Dashboard" width="100%">
</p>

---

## ✨ Features Overview

### 🛠️ Core Management
- **Customer Management** - Complete customer lifecycle
- **Package Management** - Flexible internet packages
- **Billing System** - Automated invoicing and payments
- **Sales Portal** - Dedicated agent dashboard with deposit system
- **MikroTik Integration** - PPPoE and Hotspot management
- **GenieACS Integration** - ONU/ONT monitoring and control

### 📊 Advanced Features
- **Real-time Monitoring** - Live status and statistics
- **Interactive Map** - Location-based customer visualization
- **Trouble Ticket System** - Issue tracking and resolution
- **Voucher Generator** - MikroTik hotspot voucher creation
- **Sales Deposit System** - Prepaid balance for agents
- **Mobile Responsive** - Works on all devices

### 🔗 Integrations
- **WhatsApp API** - Instant notifications
- **Tripay Payment** - Multiple payment gateways
- **Telegram Bot** - Automated alerts
- **GenieACS TR-069** - Device management

---

## 🚀 Quick Installation

### Prerequisites
- PHP 7.4 or higher
- MySQL 5.7 or higher
- Web server (Apache/Nginx)
- MikroTik router (optional)
- GenieACS server (optional)

### Installation Steps

#### 1. Clone or Download
```bash
git clone https://github.com/alijayanet/gembok-simple.git
# Or download ZIP file from GitHub
```

#### 2. Upload to Server
Upload all files to your web directory (public_html/www)

#### 3. Run Web Installer
```bash
http://your-domain.com/install.php
```

#### 4. Follow Installation Wizard
1. **Server Check** - Verify requirements
2. **Database Setup** - Configure database connection
3. **Admin Account** - Create admin credentials
4. **MikroTik Config** - Connect to MikroTik (optional)
5. **Integrations** - Set up WhatsApp, Payment, etc. (optional)

#### 5. Complete Setup
- Access admin panel: `http://your-domain.com/admin/login`
- Access customer portal: `http://your-domain.com/portal/login`
- Access sales portal: `http://your-domain.com/sales/login`

---

## 🎨 Admin Dashboard Preview

<p align="center">
  <img src="https://raw.githubusercontent.com/alijayanet/gembok-simple/main/assets/sim5.png" alt="Admin Dashboard" width="800">
</p>

### Dashboard Features:
- 📈 Real-time statistics and charts
- 👥 Customer status overview
- 💰 Revenue tracking
- 📋 Active invoices monitoring
- 🌐 MikroTik device status
- 📡 GenieACS ONU monitoring

---

## 🖥️ Customer Portal

<p align="center">
  <img src="https://raw.githubusercontent.com/alijayanet/gembok-simple/main/assets/customer-portal.png" alt="Customer Portal" width="800">
</p>

### Portal Features:
- 🔐 Login with phone number
- 📦 Package information
- 💳 Payment status & history
- 📶 ONU/ONT status and signal
- 🌐 WiFi SSID & Password management
- 🎫 Trouble ticket submission

---

## 🔧 Configuration

### Environment Variables
The system uses a simple configuration file located at `includes/config.php`:

```php
<?php
// Database Configuration
define('DB_HOST', 'localhost');
define('DB_NAME', 'gembok_db');
define('DB_USER', 'root');
define('DB_PASS', '');

// MikroTik Configuration
define('MIKROTIK_HOST', '192.168.1.1');
define('MIKROTIK_USER', 'admin');
define('MIKROTIK_PASS', '');
define('MIKROTIK_PORT', 8728);

// Application Configuration
define('APP_NAME', 'GEMBOK');
define('APP_URL', 'http://localhost/gembok-simple');
define('APP_VERSION', '2.0.0');

// GenieACS Configuration
define('GENIEACS_URL', 'http://localhost:7557');
define('GENIEACS_USERNAME', '');
define('GENIEACS_PASSWORD', '');
?>
```

---

## 📊 API Endpoints

| Endpoint | Purpose | Methods |
|----------|---------|---------|
| `/api/dashboard.php` | Dashboard statistics | GET |
| `/api/customers.php` | Customer management | GET, POST, PUT, DELETE |
| `/api/invoices.php` | Invoice operations | GET, POST, PUT, DELETE |
| `/api/mikrotik.php` | MikroTik operations | GET, POST |
| `/api/genieacs.php` | GenieACS operations | GET, POST |
| `/api/onu_locations.php` | ONU location management | GET, POST |
| `/api/onu_wifi.php` | WiFi settings control | POST |
| `/api/portal_password.php` | Portal password management | POST |

---

## 🤖 Cron Jobs Setup

To enable automated features, set up cron jobs on your server:

### Linux/CPanel
```bash
# Recommended: run scheduler every 5 minutes
*/5 * * * * /usr/bin/php /path/to/your/gembok-simple/cron/scheduler.php

# If your hosting uses MultiPHP (ea-phpXX), use the PHP binary assigned to your domain (MultiPHP Manager)
# Example:
# */5 * * * * /usr/local/bin/ea-php81 /home/USERNAME/public_html/gembok-simple/cron/scheduler.php
```

### Web Cron (Alternative)
If your hosting cannot run PHP CLI cron, you can call the web runner with a token:
```text
*/5 * * * * https://your-domain.com/cron/run.php?token=YOUR_CRON_TOKEN
```
For security, prefer CLI cron when possible and keep the token private.

### Windows (Task Scheduler)
- Create scheduled task
- Run `php.exe` with path to `cron\scheduler.php`
- Schedule every 5 minutes

### Automated Tasks:
- 🔄 Auto invoice generation
- 🔒 Auto isolation for unpaid bills
- 📬 Payment reminder notifications
- 📊 Daily activity reports
- 💾 Automatic backups

---

## 🔐 Security Features

- 🔑 Strong password hashing (bcrypt)
- 🛡️ SQL injection prevention (prepared statements)
- 🚫 XSS protection (output encoding)
- 🏷️ CSRF tokens for forms
- 🕵️ Session management with timeout
- 📝 Activity logging
- 🔍 Input validation and sanitization

---

## 📱 Mobile Responsive

The application is fully responsive and optimized for mobile devices.

---

## 💼 Sales Portal (New)

A dedicated portal for sales agents/resellers to sell hotspot vouchers.

- **Access**: `http://your-domain.com/sales/login.php`
- **Features**:
  - Deposit System (Topup by Admin)
  - Sell Vouchers (Deduct from Deposit)
  - Transaction History
  - Mobile Responsive UI

### For Admins:
1. Go to **Sales Users** menu to create sales accounts.
2. Go to **Sales Users > Paket** to assign which profiles a sales agent can sell and set their prices.
3. Topup their deposit balance.

![Image](https://github.com/user-attachments/assets/724e5ac2-626e-4f2d-bd1f-1265b70b544f)
