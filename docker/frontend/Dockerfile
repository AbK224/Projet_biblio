FROM node:20-alpine

WORKDIR /app

# Copier les dépendances
COPY package*.json ./

RUN npm install

# Copier le reste du projet
COPY . .

EXPOSE 5173

# Lancer Vite en mode dev accessible depuis Docker
CMD ["npm", "run", "dev", "--", "--host", "0.0.0.0"]