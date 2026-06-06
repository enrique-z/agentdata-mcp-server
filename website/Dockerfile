FROM nginx:alpine
COPY public/ /usr/share/nginx/html/
# Allow dotfiles (.well-known) to be served by nginx
RUN echo 'server { listen 80; server_name localhost; root /usr/share/nginx/html; location / { try_files $uri $uri/ =404; } location ~ /\.well-known { allow all; } }' > /etc/nginx/conf.d/default.conf
