# 🚀 Django EventX - Asynchronous, Dependency-Free Cross-App Event System  

## 📌 Overview  
**Django EventX** is a lightweight, dependency-free, and highly efficient **event-driven system** for Django projects. It allows cross-app communication **without relying on Celery, Redis, Django Channels, or signals**.  

With EventX, you can **trigger events asynchronously** that work in the background without affecting response performance.  

---

## ❌ Problems with Existing Event Systems  

Django provides several ways to handle asynchronous tasks, but each has limitations:  

🔴 **Celery & Redis** – Requires additional dependencies, setup, and external workers.  
🔴 **Django Channels** – Heavy for simple cross-app communication.  
🔴 **Signals** – Executes synchronously, affecting response time.  
🔴 **Threading & Async Views** – Limited and doesn’t offer event-driven flexibility.  

---

## 🚀 Why EventX?  

✅ **Fully Asynchronous** – Events run in the background without blocking responses.  
✅ **No External Dependencies** – No need for Redis, Celery, or additional workers.  
✅ **Flexible & Scalable** – Works seamlessly across Django apps.  
✅ **Easy to Use** – Just trigger an event and listen for it.  
✅ **Improves Performance** – Avoids unnecessary overhead of other async solutions.  

---

## 🎯 Features  

✔️ **Event-Based Architecture** – Decouple app logic by using event listeners.  
✔️ **Threaded Execution** – Runs event handlers asynchronously in separate threads.  
✔️ **Custom Event Handlers** – Easily create and register event handlers.  
✔️ **Works with Any Django App** – No need to modify your Django settings.  
✔️ **Automatic Event Logging** – Track event execution.  

---

## 📂 Project Structure  

```plaintext
eventx/
│── eventx/                     # Core package directory
│   ├── __init__.py              # Package initializer
│   ├── settings.py              # Default settings
│   ├── event_manager.py         # Event management logic
│   ├── listeners.py             # Register event listeners
│   ├── logger.py                # Event logging
│   ├── utils.py                 # Helper functions
│
│── example_project/             # Example Django project
│   ├── manage.py
│   ├── example_project/
│   │   ├── settings.py
│   │   ├── urls.py
│   │   ├── wsgi.py
│
│── tests/                       # Unit tests for EventX
│── pyproject.toml               # Package dependencies and config
│── .pre-commit-config.yaml      # Pre-commit hooks
│── README.md                    # Documentation
│── LICENSE                      # License file
│── setup.py                     # Installation script
```

---

## 📦 Installation  

Install Django EventX using pip:  

```bash
pip install django-eventx
```

OR Install from source:  

```bash
git clone https://github.com/YOUR_GITHUB_USERNAME/django-eventx.git
cd django-eventx
pip install -e .
```

---

## 🔧 Configuration  

### **1️⃣ Add EventX to Installed Apps**  

In `settings.py`, add:  

```python
INSTALLED_APPS = [
    # Other apps...
    'eventx',
]
```

### **2️⃣ Define Event Listeners**  

In `listeners.py`, register your event handlers:  

```python
from eventx.event_manager import event_listener

@event_listener("user_registered")
def send_welcome_email(user):
    print(f"Sending welcome email to {user.email}")

@event_listener("order_placed")
def notify_admin(order):
    print(f"New order received: {order.id}")
```

### **3️⃣ Trigger Events**  

In your views or services, trigger an event:  

```python
from eventx.event_manager import trigger_event

def register_user(request):
    user = User.objects.create(email="test@example.com")
    
    # Trigger event asynchronously
    trigger_event("user_registered", user=user)

    return JsonResponse({"message": "User registered successfully"})
```

---

## 🛠 Available Functions  

### **🔹 `trigger_event(event_name, **kwargs)`**  
Triggers an event and executes all registered listeners in the background.  

### **🔹 `event_listener(event_name)`**  
Registers a function as an event listener for a given event.  

### **🔹 `list_registered_events()`**  
Returns a list of all registered event listeners.  

---

## 🚀 Benefits of Using Django EventX  

### ✔️ **Performance**  
- Events run **in a separate thread**, keeping the request-response cycle fast.  
- No need for **Celery workers or Redis**, reducing infrastructure costs.  

### ✔️ **Simplicity**  
- **No complex setup** – Just install and start using event listeners.  
- **No additional configurations** required in Django settings.  

### ✔️ **Flexibility**  
- Works across **multiple Django apps**.  
- Easily extends by adding new **event handlers**.  

---

## 🚧 Limitations  

🔴 **Threading Limitations**  
- Uses Python’s threading module, which is limited by the **Global Interpreter Lock (GIL)**.  

🔴 **Not Suitable for Long-Running Tasks**  
- For CPU-intensive tasks (e.g., video processing), a task queue like Celery is better.  

🔴 **No Guaranteed Execution**  
- If the Django server crashes, pending events **won’t be retried** automatically.  

---

## 🚀 Contributing  

We welcome contributions!  

1️⃣ Fork the repo  
2️⃣ Create a feature branch: `git checkout -b feature-name`  
3️⃣ Commit changes: `git commit -m "Add new feature"`  
4️⃣ Push branch: `git push origin feature-name`  
5️⃣ Open a Pull Request  

---

## 📜 License  

This project is licensed under the **MIT License**.  

---

## ⭐ Support  

If you like this project, give it a ⭐ on GitHub!  

