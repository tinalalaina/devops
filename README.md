git clone 
ls
cd backend
source .venv/bin/activate
ajout .env
python manage.py runserver

cd ..
cd frontend
npm install
npm run dev

++++++++++++++++++++
cloudflare.com
frontend:
clique sur 
computer & ai => workers & pages => create application => Looking to deploy Pages? Get started => clique sur get startedd => import an existing git repository => deploy a site from your account (connect github) => confirm access => il va te diriger vers ton github est tu vois "cloudflare workers and pages" : laisse all repositories (ou ony select repositories ici on a choisir only slect et choisi websocket)=> clique save => l’accès est bien enregistré, mais il faut cliquer de nouveau sur “Connect GitHub” pour que la liste des repos se charge.=>   Clique Connect GitHub (au milieu de la page).=> Si on te demande de choisir un compte GitHub → sélectionne devworkshop26-web.=>Tu verras une liste de repos → choisis websocket.=>Tu verras enfin le formulaire Root directory.
Root directory : frontend
Build command : npm ci && npm run build
Build output directory: dist

Va dans ton projet Pages → Settings → Environment variables ou dans le variables and secrets =>
type: text
variable name: VITE_API_URL
value: https://websocket-vp66.onrender.com/api

CORS_ALLOWED_ORIGINS=https://websocket-djo.pages.dev
CSRF_TRUSTED_ORIGINS=https://websocket-djo.pages.dev

CORS_ALLOW_ALL_ORIGINS=False
 
Save, rebuild, and deploy.
+++++++++++++++++++++++++++++++++++++
render 
backend

1) Créer un projet Render
Sur l’écran “Projects” :
    Clique + Create new project
    Donne un nom (ex : my-app)
    Ouvre le projet
2) Créer ta base de données PostgreSQL

Dans ton projet :
    Clique + New (en haut à droite)
   Sur l’écran “New Postgres” (ta capture) :
    Name → mets un nom (ex: agri-db)
    Project → choisis ton projet
    Region → choisis la même région que ton backend
    PostgreSQL Version → laisse 16 ou 15
    Plan Options → choisis “Free”
    👉 Sur ta capture c’est Basic (payant). Clique bien Free.
    Clique Create Database


➡️ Une fois créé, Render te donne :
    Host
    Database
    User
    Password
    Internal URL
    External URL
Garde ces infos.


avec:   Port: 5432

    Host: dpg-d60lsufpm1nc73cr1vr0-a

    Database: mydatabase_tsps

    Username: mydatabase_tsps_user

    Password: 4dl71kaUUvPn4ICVk37tqe3eJIzZDOYB

    Internal URL: postgresql://mydatabase_tsps_user:4dl71kaUUvPn4ICVk37tqe3eJIzZDOYB@dpg-d60lsufpm1nc73cr1vr0-a/mydatabase_tsps

    External URL: postgresql://mydatabase_tsps_user:4dl71kaUUvPn4ICVk37tqe3eJIzZDOYB@dpg-d60lsufpm1nc73cr1vr0-a.oregon-postgres.render.com/mydatabase_tsps

Dans ton Web Service Render :
    Ouvre Settings
    Root Directory → mets : backend


    Ouvre ton Web Service (pas la base)
    Va dans Settings → Environment
    Clique Add Environment Variable
    Ajoute ceci (une par une) :

DB_HOST=dpg-d60lsufpm1nc73cr1vr0-a
DB_PORT=5432
DB_NAME=mydatabase_tsps
DB_USER=mydatabase_tsps_user
DB_PASS=4dl71kaUUvPn4ICVk37tqe3eJIzZDOYB
DEBUG=False
SECRET_KEY=ta_cle_secrete


Dans la ligne SECRET_KEY :
    Clique sur le bouton “Generate” (à droite)
    Render va créer automatiquement une clé sécurisée
    Clique Save, rebuild, and deploy

teste: https://websocket-vp66.onrender.com
