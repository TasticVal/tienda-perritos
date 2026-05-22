FROM nginx:alpine

# Limpia contenido por defecto
RUN rm -rf /usr/share/nginx/html/*

# Copia los archivos del frontend
COPY index.html app.js /usr/share/nginx/html/

# Copia la configuración custom de Nginx
COPY default.conf /etc/nginx/conf.d/default.conf

# Ajuste de permisos para ejecutar como usuario non-root (nginx)
RUN chown -R nginx:nginx /usr/share/nginx/html && \
    chown -R nginx:nginx /var/cache/nginx && \
    chown -R nginx:nginx /var/log/nginx && \
    touch /var/run/nginx.pid && \
    chown -R nginx:nginx /var/run/nginx.pid

# Cambiar al usuario nginx
USER nginx

EXPOSE 80