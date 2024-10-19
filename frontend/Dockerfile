# Utiliser une image de base Node.js pour construire l'application
FROM node:18 AS build

# Définir le répertoire de travail
WORKDIR /app

# Copier package.json et package-lock.json
COPY package*.json ./

# Installer les dépendances
RUN npm install

# Copier le reste de l'application
COPY . .

# Construire l'application Angular
RUN npm run build --prod

# Étape pour servir l'application avec un serveur léger
FROM nginx:alpine
COPY --from=build /app/dist/frontend /usr/share/nginx/html

# Exposer le port
EXPOSE 80

# Commande pour démarrer Nginx
CMD ["nginx", "-g", "daemon off;"]
