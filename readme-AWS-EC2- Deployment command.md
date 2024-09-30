
# Documentation: Deploying a Django Project on AWS EC2

This documentation outlines the steps Mohammad Arman used to deploy a Django project on an AWS EC2 instance. These steps include updating packages, cloning repositories, installing dependencies, setting up a virtual environment, and running the Django application.




## Deployment

To deploy this project run

1. Update the System Packages
Before installing any dependencies, it is essential to update the system packages on the EC2 instance.

```bash
 sudo apt-get update


```
2. Clone the Project Repositories
Clone the required GitHub repositories to the EC2 instance.

Cloning your Django Employee Management project:
```bash
 
git clone https://github.com/mdarman4002/EmployeeManagement-Django-project-.git

```
3. Navigate to the Project Directory
After cloning, navigate into the project directory.
```bash
 
cd EmployeeManagement-Django-project-

```
List the contents of the directory to confirm the project structure:
```bash
 
ls
ls -lrt

```
Move to the specific Django app directory (in this case, MyFirstApp):
```bash
 
cd MyFirstApp

```
4. Upgrade System Packages
To ensure all packages are up-to-date, upgrade the system:
```bash
 sudo apt upgrade -y


```

5. Install Necessary Dependencies
Install Python-related packages, libraries for PostgreSQL, NGINX, and other necessary tools:
```bash
 
sudo apt install python3-pip python3-dev libpq-dev nginx curl -y

```

Ensure python3-pip is installed:
```bash
sudo apt install python3-pip -y
```

Install the virtual environment package:
```bash
sudo apt install python3-venv

```

6. Set Up a Virtual Environment
Create a Python virtual environment inside the project folder:
```bash
python3 -m venv venv

```

Activate the virtual environment:
```bash
source venv/bin/activate

```
7. Install Django and Gunicorn
Install Django and Gunicorn (a Python WSGI HTTP server) within the virtual environment:
```bash
pip install django
pip install django gunicorn

```

8. Install Pillow
Pillow is used for handling images in Django:
```bash
python3 -m pip install Pillow

```
if you have requirements.txt file then 
Install all the project dependencies listed in the requirements.txt file:(These are optional if you don't have a this file skip these command)
```bash
pip install -r requirements.txt

```
If the requirements.txt file does not exist, create one by freezing the installed packages:(option)
```bash
pip freeze > requirements.txt

```

10. Run Django Migrations
Before running the application, apply database migrations:
```bash
python3 manage.py makemigrations
python3 manage.py migrate

```

11. Create a Django Superuser
To access the Django admin panel, create a superuser:


```bash
python3 manage.py createsuperuser

```

12. Run the Django Application
Finally, run the Django development server:
```bash
python3 manage.py runserver

```
This completes the deployment steps on an AWS EC2 instance.
