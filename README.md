# Vue Quasar App

A Vue 3 Quasar Project

## Install the dependencies
```bash
yarn
# or
npm install
```

### Start the app in development mode (hot-code reloading, error reporting, etc.)
```bash
quasar dev
```


### Build the app for production
```bash
quasar build

// the build is in dist/spa
// the "dist" is in the .gitignore, so it will be pulled on server.
// So, you don't need to build on server, just git pull
```
### NGINX configuration for production for vuejs must have try_files $uri $uri/ /index.html;
https://router.vuejs.org/guide/essentials/history-mode.html#nginx
```bash

server {
	server_name vue.mathiasappelmans.be;

    error_log                   /var/www/srv_dev/log/nginx/error.log notice;
    access_log                  /var/www/srv_dev/log/nginx/access.log;

    location    / {

        root                        /var/www/srv_dev/app/vue/dist/spa;
        index index.html;
        include  /etc/nginx/mime.types;
        try_files $uri $uri/ /index.html;
    }




	listen [::]:443 ssl; # managed by Certbot
    listen 443 ssl; # managed by Certbot
    ssl_certificate /etc/letsencrypt/live/vue.mathiasappelmans.be/fullchain.pem; # managed by Certbot
    ssl_certificate_key /etc/letsencrypt/live/vue.mathiasappelmans.be/privkey.pem; # managed by Certbot
    include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot

}

server {
    if ($host = vue.mathiasappelmans.be) {
        return 301 https://$host$request_uri;
    } # managed by Certbot


	listen 							80;
	listen 							[::]:80;
	server_name vue.mathiasappelmans.be;
    return 404; # managed by Certbot
}

```

### Customize the configuration
See [Configuring quasar.config.js](https://v2.quasar.dev/quasar-cli-vite/quasar-config-js).
