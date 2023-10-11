# Usa una imagen base de Nginx
FROM nginx:latest

# Copia la configuración personalizada de Nginx al contenedor
COPY nginx.conf /etc/nginx/nginx.conf

# Expon el puerto 80 para Nginx
EXPOSE 80

# Comando para iniciar Nginx en segundo plano
CMD ["nginx", "-g", "daemon off;"]
