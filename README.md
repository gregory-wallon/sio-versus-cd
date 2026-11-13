# sio-versus-cd

Exemple pédagogique de développement et de déploiement via Docker. Dépôt public à destination des étudiants en BTS SIO option SISR.

## Procédure de déploiement

### Cloner le dépôt

Déployez les fichiers sur votre serveur de production. Le plus simple est de télécharger l'archive du porjet via `wget` :

```bash
wget "https://codeload.github.com/gregory-wallon/sio-versus-cd/zip/refs/heads/main" -O r.zip && unzip r.zip 
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

### Configurer la NATv6

```bash
ip6tables -t nat -I POSTROUTING -o enp8s0 -s fd80:f871:9a40::/64 -j MASQUERADE
```

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