# 🚀 Django Middleware Manager  

## 📌 Overview  
**Django Middleware Manager** is a powerful package that dynamically manages middleware execution based on request properties such as URL path, app, view, headers, and more. It enhances security, performance, and flexibility while keeping middleware configurations dynamic and lightweight.  

---

## ❌ Problems with Django's Default Middleware System  

Django provides a built-in middleware system that works in a **static** way:  
✅ **Middleware execution is always in a fixed order** (as listed in `MIDDLEWARE` settings).  
✅ **Cannot conditionally enable or disable middleware** dynamically based on request properties.  
✅ **Inefficient when multiple middleware checks are unnecessary** for certain paths, views, or apps.  
✅ **Difficult to integrate external services** like rate limiting, performance logging, or header-based middleware activation.  

**🚀 Solution?** Django Middleware Manager dynamically **activates, deactivates, and manages middleware** based on request conditions, making it more efficient, secure, and flexible.  

---

## 🎯 Features  
✅ **Centralized Middleware Management**  
✅ **Dynamic Middleware Activation & Deactivation**  
✅ **Header Injection for Request-based Control**  
✅ **Performance Logging & Monitoring**  
✅ **Security & Rate Limiting Middlewares**  
✅ **Works Seamlessly with Django Middleware System**  

---

## 📂 Repository Structure  
```plaintext
middleware-manager/
│── middleware_manager/       # Core package directory
│   ├── middlewares/          # Custom middleware implementations
│   │   ├── performance_middleware.py
│   │   ├── logging_middleware.py
│   │   ├── security_middleware.py
│   │   ├── rate_limit_middleware.py
│   ├── __init__.py
│   ├── base_middleware.py    # Core middleware logic
│   ├── manager.py            # Middleware manager implementation
│   ├── settings.py           # Middleware settings
│   ├── utils.py              # Utility functions
│
│── example_project/          # Example Django project for testing
│   ├── manage.py
│   ├── example_project/
│   │   ├── __init__.py
│   │   ├── settings.py
│   │   ├── urls.py
│   │   ├── wsgi.py
│
│── tests/                    # Unit tests for middleware
│── pyproject.toml            # Package dependencies and config
│── .pre-commit-config.yaml   # Pre-commit hooks
│── README.md                 # Project Documentation
│── LICENSE                   # License file
│── setup.py                  # Installation script
```  

---

## 📦 Installation  
```bash
pip install django-middleware-manager
```  

OR Install from source:  
```bash
git clone https://github.com/YOUR_GITHUB_USERNAME/middleware-manager.git
cd middleware-manager
pip install -e .
```  

---

## 🔧 Configuration  

### **1️⃣ Add Middleware Manager to `MIDDLEWARE` in `settings.py`**  
```python
MIDDLEWARE = [
    'middleware_manager.manager.MiddlewareManager',
]
```  

### **2️⃣ Register Custom Middlewares**  
```python
MIDDLEWARE_MANAGER = {
    "default_middlewares": [
        "middleware_manager.middlewares.logging_middleware.LoggingMiddleware",
        "middleware_manager.middlewares.performance_middleware.PerformanceMiddleware",
    ],
    "dynamic_middlewares": [
        {
            "middleware": "middleware_manager.middlewares.security_middleware.SecurityMiddleware",
            "conditions": {"path_contains": "/secure/"}
        }
    ]
}
```  

---

## 🛠 Available Middlewares  

### 🔹 **Logging Middleware**  
📌 Logs all incoming requests & responses for debugging.  
✅ Tracks request headers, response status, and execution time.  

### 🔹 **Performance Middleware**  
📌 Measures request processing time.  
✅ Logs slow requests exceeding the defined threshold.  

### 🔹 **Security Middleware**  
📌 Adds security headers like **CSP, XSS Protection, HSTS**.  
✅ Blocks insecure requests dynamically.  

### 🔹 **Rate Limiting Middleware**  
📌 Restricts excessive API requests to prevent abuse.  
✅ Uses **Redis** or **in-memory storage** for rate tracking.  

---

## 🚀 Benefits of Using Middleware Manager  

### ✔️ **Efficiency**  
- Avoids executing unnecessary middleware for irrelevant requests.  
- Reduces processing time by **conditionally** applying middleware.  

### ✔️ **Security**  
- Dynamically enables security middleware for sensitive requests.  
- Blocks requests based on headers, origin, and path.  

### ✔️ **Flexibility**  
- Allows middleware execution based on **URL patterns, apps, views, and headers**.  
- Developers can **easily register new middleware** with minimal configuration.  
```  

