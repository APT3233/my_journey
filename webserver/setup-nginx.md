# Setup WebServer with nginx
1. Install nginx & certbot(SSL)
    ```sh
    sudo apt update 
    sudo apt install nginx certbot python3-certbot-nginx make gcc neofetch
    ```

2. Configure nginx
    - Create file conf
        ```sh
        sudo nano /etc/nginx/sites-available/yourdomain
        ```
    - Add config
        ```sh
        server {
            listen 80;
            server_name example.com www.example.com;  
            
            return 301 https://$host$request_uri;
        }
        server {
            listen 443 ssl;
            server_name yourdomain.com www.yourdomain.com;

            ssl_certificate /etc/letsencrypt/live/yourdomain.com/fullchain.pem;
            ssl_certificate_key /etc/letsencrypt/live/yourdomain.com/privkey.pem;

            ssl_session_cache shared:le_nginx_SSL:10m;
            ssl_session_timeout 1440m;

            ssl_protocols TLSv1.2 TLSv1.3;
            ssl_prefer_server_ciphers on;
            ssl_ciphers "ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256";

            root /var/www/html;
            index index.html index.htm index.nginx-debian.html;

            location / {
                try_files $uri $uri/ =404;
            }
        }
        ```
    - Or config reverse proxy
        ```sh
        server {
            listen 443 ssl;
            server_name yourdomain.com;

            ssl_certificate /path/to/your/cert.pem;
            ssl_certificate_key /path/to/your/key.pem;

            location / {
                proxy_pass http://localhost:4444;  # Chuyển hướng tất cả các yêu cầu đến web server ở cổng 4444
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection 'upgrade';
                proxy_set_header Host $host;
                proxy_cache_bypass $http_upgrade;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header X-Forwarded-Proto $scheme;
            }
        }
        ```
    
    - Active conf
        ```sh
        sudo ln -s /etc/nginx/sites-available/yourdomain /etc/nginx/sites-enabled/
        ```
    
3. Get SSL
    ```sh
    sudo certbot --nginx -d yourdomain.com -d www.yourdomain.com
    ```
    - Replace yourdomain.com
    
4. Run nginx
    ```sh
    sudo nginx -t
    ```
    - Restart nginx
    ```sh
    sudo systemctl restart nginx
    ```
