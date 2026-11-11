# sio-versus-cd

Exemple pédagogique de développement et de déploiement via Docker. Dépôt public à destination des étudiants en BTS SIO option SISR.

## Procédure de déploiement

### Cloner le dépôt

Déployez les fichiers sur votre serveur de production. Le plus simple est d'utiliser la commande `git clone` :

```bash
git clone https://github.com/gregory-wallon/sio-versus-cd.git
```

> NB : une amélioration possible serait de déployer ces fichiers via Ansible.

### Configurer le fichier `.env`

Vous devez ensuite déclarer les variables d'environnement. Pour cela, basez-vous sur le fichier d'exemple `.env.example` :

```bash
cp .env.example .env
vim .env
```

Adaptez les variables déclarées dans le fichier `.env`.

> NB : une amélioration possible serait de mieux protéger le jeton (token), qui constitue une donnée sensible, par exemple en utilisant un secret Docker.

### Adapter le port

Dans le fichier `docker-compose.yml`, adaptez le port public selon vos besoins.

> NB : il est possible d'automatiser le choix du port via Ansible.

### Lancer le projet

Pour lancer le projet :

```bash
docker-compose up -d
```

Pour lancer le projet en arrière-plan tout en affichant les logs :

```bash
docker-compose up -d && docker-compose logs -f
```

Bon match !