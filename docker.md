# creer un conteneur avec un volume (utiliser des chemins absolus)
sudo docker run --name my-mongo -v /home-dir/tps/bigdata/volume:/mnt/ -d mongo
#tester le volume en creant un fichier depuis la machine virtuelle
touch /home-dir/tps/bigdata/volume/empty.txt
# verifier qu'il est aussi accessible depuis le conteneur
sudo docker exec my-mongo ls /mnt


#Afficher tout les container dispos
sudo docker container ls -a

#arreter un container
sudo docker stop my-mongo

#supprimer un container
sudo docker rm my-mongo

#Run an Existing Container with her name If the container already exists and you want to start it:
docker start -ai my_container           /       docker start my_container
