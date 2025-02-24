# SoftDjango - Deploy Django Websites with Softaculous 🚀  

SoftDjango is a Softaculous package that enables one-click deployment of Django applications on any server. It automates environment setup, dependency installation, and database configuration, making Django deployment seamless for shared hosting, VPS, and cloud servers.  

## Features  
✅ One-click Django installation via Softaculous  
✅ Automatic virtual environment setup  
✅ Pre-configured database support (PostgreSQL/MySQL)  
✅ Dependency installation (`pip install -r requirements.txt`)  
✅ Automatic migrations (`python manage.py migrate`)  
✅ Easy upgrades and uninstallation  

## Installation  

### **Step 1: Clone the Repository**  
```sh
git clone https://github.com/yourusername/softdjango.git
cd softdjango

### **Step 2: Configure Softaculous**  
1. Copy the `softdjango` package folder into your Softaculous installation directory:  
   ```
   /var/softaculous/scripts/
   ```
2. Restart Softaculous services if needed.

### **Step 3: Deploy via Softaculous**  
1. Open Softaculous in your hosting panel.  
2. Search for "SoftDjango" in the available scripts.  
3. Click "Install" and configure the Django project settings.  
4. Complete the installation, and your Django app is ready! 🎉  

## Uninstallation  
To remove SoftDjango from Softaculous:  
```sh
rm -rf /var/softaculous/scripts/softdjango
```

To uninstall a deployed Django instance, use Softaculous' "Remove" option or manually delete the files.

## Updating SoftDjango  
SoftDjango can be updated via Softaculous or manually:  
```sh
cd /var/softaculous/scripts/softdjango
git pull origin main
```

## Contributing  
We welcome contributions! If you’d like to improve SoftDjango, fork this repository and submit a pull request.

## License  
This project is licensed under the MIT License.

---

### Need Help?  
📧 Contact: abhijeet151@gmail.com  
🌐 Website: [abhijeetcs.dev](https://abhijeetcs.dev)  
