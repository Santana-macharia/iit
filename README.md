

This is a basic web app to illustrate deployment with nginx and waitress

### Steps

1. Download and copy nginx to `C:/`.

2. Install Python 3.7 in `C:/Python37` and install 

    - `django`, `openpyxl` and `waitress`

3. Edit `ALLOWED_HOSTS` in `settings.py`. Waitress will be running the Django server at `http://localhost:8080`.

4. Collect static files by running `python manage.py collectstatic`

5. Edit `nginx_waitress/iit_nginx.conf`

    - Edit the `server_name`

    - Edit the path to `/static` (and `/media` if needed)
    
    - Edit `proxy_pass` to match the server running from Waitress (i.e. `runserver.py`). This will usually be `localhost` or your IP address

6. Create two directories inside of `C:/nginx/`

    - Create `sites-enabled` and `sites-available`

    - Copy `iit_nginx.conf` to the two directories

6. Edit `C:/nginx/conf/nginx.conf`

    - Add `include <path to your sites-enabled/iit_nginx.conf>;`

    - Change port `80` to a non-essential port like `10`. 

7. Open a terminal at `C:/nginx/` and run `nginx.exe -t` to check files, and if everything is successful run `nginx.exe` to start the server

8. Open a web browser and navigate to `http://localhost`
