FROM nginx:1.27-alpine

# Statische Website in den Web-Root kopieren
COPY . /usr/share/nginx/html

# Eigene nginx-Konfiguration (Port 8080 für Cloud Run, korrekte .mjs-MIME)
COPY nginx.conf /etc/nginx/nginx.conf

# Build-/Config-Dateien nicht mit ausliefern
RUN rm -f /usr/share/nginx/html/Dockerfile \
          /usr/share/nginx/html/nginx.conf \
          /usr/share/nginx/html/.dockerignore \
          /usr/share/nginx/html/README.md

EXPOSE 8080
CMD ["nginx", "-g", "daemon off;"]
