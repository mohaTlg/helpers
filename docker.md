# Guide d'utilisation Docker : Démarrage et Gestion de Conteneurs

Ce guide regroupe les commandes essentielles pour démarrer, créer et gérer des conteneurs Docker.

---

## 1. Démarrer un conteneur existant

Si le conteneur a déjà été créé auparavant et se trouve actuellement à l'état arrêté :

```bash
docker start <nom_ou_id_du_conteneur>
```

* **Exemple :**
  ```bash
  docker start mon_serveur_web
  ```
* **Lister tous les conteneurs (actifs et arrêtés) :**
  ```bash
  docker ps -a
  ```

---

## 2. Créer et démarrer un nouveau conteneur

Pour récupérer une image depuis un registre (comme Docker Hub) et instancier immédiatement un nouveau conteneur, utilisez la commande `docker run` :

```bash
docker run [OPTIONS] <nom_de_l_image>
```

### Options courantes pour `docker run`

| Option | Description |
| :--- | :--- |
| `-d` | Exécute le conteneur en arrière-plan (*détaché*). |
| `--name <nom>` | Attribue un nom personnalisé au conteneur. |
| `-p <port_hote>:<port_conteneur>` | Redirige un port de la machine hôte vers le conteneur. |
| `-it` | Ouvre une session interactive avec un terminal pseudo-TTY. |
| `--rm` | Supprime automatiquement le conteneur lorsqu'il s'arrête. |

### Exemples pratiques

* **Lancer un serveur web Nginx en arrière-plan sur le port 8080 :**
  ```bash
  docker run -d --name mon_nginx -p 8080:80 nginx
  ```

* **Lancer un conteneur Ubuntu et ouvrir directement son terminal `bash` :**
  ```bash
  docker run -it ubuntu bash
  ```

---

## 3. Commandes utiles de gestion au quotidien

* **Voir les conteneurs en cours d'exécution :**
  ```bash
  docker ps
  ```

* **Stopper un conteneur actif proprement :**
  ```bash
  docker stop <nom_ou_id>
  ```

* **Redémarrer un conteneur :**
  ```bash
  docker restart <nom_ou_id>
  ```

* **Consulter les logs d'un conteneur :**
  ```bash
  docker logs -f <nom_ou_id>
  ```

* **Exécuter une commande à l'intérieur d'un conteneur en cours d'exécution :**
  ```bash
  docker exec -it <nom_ou_id> bash
  ```

# creer un conteneur avec un volume (utiliser des chemins absolus)
sudo docker run --name my-mongo -v /home-dir/tps/bigdata/volume:/mnt/ -d mongo
# tester le volume en creant un fichier depuis la machine virtuelle
touch /home-dir/tps/bigdata/volume/empty.txt
# verifier qu'il est aussi accessible depuis le conteneur
sudo docker exec my-mongo ls /mnt


# Afficher tout les container dispos
sudo docker container ls -a

# arreter un container
sudo docker stop my-mongo

# supprimer un container
sudo docker rm my-mongo

# Run an Existing Container with her name If the container already exists and you want to start it:
docker start -ai my_container           /       docker start my_container
