\# 📚 Application de Gestion de Bibliothèque



\## 📝 Description du projet



Cette application est une plateforme de \*\*gestion de bibliothèque\*\* permettant de :



\* gérer les livres

\* gérer les utilisateurs

\* gérer les emprunts et retours

\* consulter le catalogue



Le projet est composé de :



\* 🧩 \*\*Backend\*\* : Laravel (API REST)

\* 🎨 \*\*Frontend\*\* : React (Vite)

\* 🐘 \*\*Base de données\*\* : PostgreSQL

\* 🐳 \*\*Conteneurisation\*\* : Docker \& Docker Compose

\* ⚙️ \*\*CI/CD\*\* : Jenkins



---



\## 🏗️ Architecture du projet



```

Utilisateur (Navigateur)

&nbsp;       ↓

Frontend React (port 5173)

&nbsp;       ↓

Backend Laravel API (port 8000 via Nginx)

&nbsp;       ↓

PostgreSQL (port 5432)

&nbsp;       ↓

pgAdmin (port 5050)

```



---



\## 📁 Structure du projet



```

BIBLIOTHEQUE/

├── biblio-backend/       # Laravel API

├── biblio-frontend/      # React (Vite)

├── docker/

│   ├── backend/

│   │   └── Dockerfile

│   ├── frontend/

│   │   └── Dockerfile

│   └── nginx/

│       └── default.conf

├── docker-compose.yaml

├── Jenkinsfile

└── README.md

```



---



\## ⚙️ Prérequis



Avant de lancer le projet, assurez-vous d’avoir :



\* Docker

\* Docker Compose

\* Git



---



\## 🚀 Installation et lancement



\### 1. Cloner le projet



```bash
créer un dossier sur "dossier"
git clone https://github.com/AbK224/Projet_biblio.git

cd nom_du_dossier_créé


```



---



\### 2. Configuration Laravel



Dans le fichier :



```

biblio-backend/.env

```



Configurer la base de données :



```env

DB\_CONNECTION=pgsql

DB\_HOST=db

DB\_PORT=5432

DB\_DATABASE=bibliotheque

DB\_USERNAME=postgres

DB\_PASSWORD=postgres

```



---



\### 3. Lancer les conteneurs



```bash

docker compose up -d --build

```



---



\### 4. Initialiser Laravel



```bash

docker compose exec backend php artisan key:generate

docker compose exec backend php artisan migrate

```



---



\## 🌐 Accès à l'application



| Service  | URL                   |

| -------- | --------------------- |

| Backend  | http://localhost:8000 |

| Frontend | http://localhost:5173 |

| pgAdmin  | http://localhost:5050 |



---



\## 🗄️ Accès à la base de données (pgAdmin)



Identifiants :



\* Email : \[admin@dit.com](mailto:admin@dit.com)

\* Mot de passe : admin123vas



Configuration du serveur PostgreSQL dans pgAdmin :



\* Host : `db`

\* Port : `5432`

\* Database : `bibliotheque`

\* User : `postgres`

\* Password : `postgres`



---



\## 🔄 Pipeline CI/CD (Jenkins)



Le fichier `Jenkinsfile` permet d’automatiser :



1\. Récupération du code (Git)

2\. Build des images Docker

3\. Démarrage des conteneurs

4\. Installation des dépendances backend

5\. Configuration Laravel (clé + migrations)

6\. Installation des dépendances frontend

7\. Exécution des tests



---



\## 🐳 Commandes Docker utiles



\### Démarrer le projet



```bash

docker compose up -d --build

```



\### Arrêter le projet



```bash

docker compose down

```



\### Voir les conteneurs



```bash

docker compose ps

```



\### Accéder au backend



```bash

docker compose exec backend bash

```



\### Accéder à PostgreSQL



```bash

docker compose exec db psql -U postgres -d bibliotheque

```



---



\## ⚠️ Problèmes fréquents



\### Conflit pgAdmin



```bash

docker rm -f pgadmin

```



---



\### Migration échoue



```bash

docker compose exec backend php artisan migrate:fresh

```



---



\### Cache Laravel



```bash

docker compose exec backend php artisan config:clear

```



---



\## 👨‍💻 Auteurs



\* Nom : Groupe 3

\* Projet académique : Gestion de bibliothèque

\* Technologie : Laravel / React / Docker / PostgreSQL



---



\## 📌 Conclusion



Ce projet démontre :



\* la mise en place d’une architecture moderne

\* la conteneurisation avec Docker

\* l’utilisation d’une base PostgreSQL

\* l’automatisation avec Jenkins (CI/CD)



---



