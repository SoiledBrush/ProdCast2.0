# Compiled Docker Compose for Django + React application.
* Backend: Django + Gunicorn
* Frontend: React 
* Database: PostgreSQL

## Installation & Setup
### 1.Clone the repository
   ```
   git clone <your-repo-url>
   cd <project-folder>
   ```

### 2.Configure environment
  Edit the following files before running:
   ```
   backend/settings.py
   ```

  * ALLOWED_HOSTS → include your domain or server IP
  * CORS_ALLOWED_ORIGINS → add your frontend domain
     
   ```
   docker-compose.yml
   ``` 
    
  * Ensure database credentials in environment section match Django settings.
    
      
     
    
  > [!NOTE]
>  I am currently working on making those steps easier through env variables
### 3.Build & start containers
   ```
   docker compose up -d --build
   ```
This will start:
  * PostgreSQL on port 5432
  * Backend on port 8000 
  * Frontend on port 80
    
### 4.Run migrations & create superuser

Open a shell into the backend container: 
   ```
docker compose exec backend python manage.py migrate
docker compose exec backend python manage.py createsuperuser
```
 > [!NOTE]
> This part will get automated too
### 5. Access the app
 * Frontend: http://localhost/
 * Backend: http://localhost:8000/admin/

  > [!TIP]
>  To change API base URL used by frontend, update `frontend/src/links.jsx`

