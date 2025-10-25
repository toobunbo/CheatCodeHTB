# CheatCodeHTB
## Dusty Alleys

```config
server {
        listen 80 default_server;
        server_name alley.$SECRET_ALLEY;

    location / {
        root /var/www/html/;  
        index index.html;              
    }

        location /alley {
                        proxy_pass http://localhost:1337;
                        proxy_set_header Host $host;
                        proxy_set_header X-Real-IP $remote_addr;
                        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                        proxy_set_header X-Forwarded-Proto $scheme;
        }

        location /think  { 
                        proxy_pass http://localhost:1337;
                        proxy_set_header Host $host;
                        proxy_set_header X-Real-IP $remote_addr;
                        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                        proxy_set_header X-Forwarded-Proto $scheme;

                        }
}

server {
        listen 80;
                server_name guardian.$SECRET_ALLEY;

        location /guardian {
                        proxy_pass http://localhost:1337;
                        proxy_set_header Host $host;
                        proxy_set_header X-Real-IP $remote_addr;
                        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                        proxy_set_header X-Forwarded-Proto $scheme;
        }
}
```
