a dernière modification enregistrée dans le dépôt est le commit “Harden backend container for production, add entrypoint and env config”. Il inclut :

    ajout d’un entrypoint.sh + Gunicorn,

    ajustements CORS/CSRF/DEBUG,

    ajout des .env.example,

    configuration de VITE_API_URL.

Détails complets visibles dans le dernier commit : git log -1 --stat. (Command exécutée : git log -1 --stat.)

Objectif de la modification (le “but”)

Cette modification vise à rendre le projet prêt pour la production et facilement déployable :

    Backend prêt pour la prod (Docker + Gunicorn)

        Le backend ne démarre plus avec runserver (dev), mais avec un entrypoint prod qui lance les migrations, collecte les fichiers statiques, puis démarre Gunicorn. Cela correspond aux bonnes pratiques de déploiement (Koyeb, etc.).

    Configuration de sécurité via variables d’environnement

        Par défaut, DEBUG est désactivé et les règles CORS/CSRF sont configurables par variables d’environnement. Cela évite d’exposer l’API en prod par défaut et facilite le déploiement sur un domaine Cloudflare Pages/Koyeb.

    Front-end portable (API URL configurable)

        L’URL de l’API n’est plus en dur en local ; elle peut être définie via VITE_API_URL, ce qui permet d’utiliser facilement un backend Koyeb en production.

    Exemples d’environnement




Pourquoi cette modification ?

    Fiabilité en production : runserver est un serveur de développement, non prévu pour la prod. Gunicorn est le standard pour Django en production.

    Sécurité : éviter DEBUG=True et CORS ouvert en production, tout en laissant la configuration via variables d’environnement (Koyeb/CI).

    Déploiement facile : Cloudflare Pages + Koyeb demandent des URLs de prod, donc VITE_API_URL est indispensable pour connecter le front au bon backend.

     
