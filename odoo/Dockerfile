### Estructura mínima para desplegar Odoo 16 + PostgreSQL en Render usando Docker

# Dockerfile (para Odoo)
FROM odoo:16.0

LABEL maintainer="donvito.erp@universidad.edu"

# Puedes agregar addons personalizados aquí si querés:
# COPY ./custom-addons /mnt/extra-addons

EXPOSE 8069

# docker-compose.yml
version: '3.1'

services:
  db:
    image: postgres:13
    environment:
      - POSTGRES_DB=postgres
      - POSTGRES_USER=odoo
      - POSTGRES_PASSWORD=odoo
    restart: always
    volumes:
      - db-data:/var/lib/postgresql/data

  web:
    build: .
    depends_on:
      - db
    ports:
      - "8069:8069"
    environment:
      - HOST=db
      - USER=odoo
      - PASSWORD=odoo
    restart: always
    volumes:
      - odoo-data:/var/lib/odoo

volumes:
  db-data:
  odoo-data:
