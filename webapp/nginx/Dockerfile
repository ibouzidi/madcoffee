# Dockerfile for Nginx
FROM nginx:alpine

# Copy custom Nginx configuration
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

# Remove symbolic links and create log files
RUN rm /var/log/nginx/access.log /var/log/nginx/error.log && \
    touch /var/log/nginx/access.log /var/log/nginx/error.log && \
    chmod 644 /var/log/nginx/access.log /var/log/nginx/error.log && \
    chown nginx:nginx /var/log/nginx/access.log /var/log/nginx/error.log

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

