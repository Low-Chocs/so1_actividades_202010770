# Luis Mariano Moreira García 202010770
# Actividad 3 - Control de Accesos


echo "Hice toda esta tarea utilizando los comandos en lugar del md para familiarizarme mas con el entorno linux"
echo "Se crean los usuarios"
sudo useradd usuario1
sudo useradd usuario2
sudo useradd usuario3

echo "Se hacen las contraseñas"
sudo passwd usuario1
echo "Pedira contraseña: 1"
sudo passwd usuario2
echo "Pedira contraseña: 12"
sudo passwd usuario3
echo "Pedira contraseña: 123"

echo "Se eliminaran los usuarios para crearlos con su directorio principal"
sudo userdel usuario1
sudo userdel usuario2
sudo userdel usuario3

echo "Se van a crear con su directorio principal"
sudo useradd -m usuario1
sudo useradd -m usuario2
sudo useradd -m usuario3

echo "Se vuelven a poner las contraseñas"
sudo passwd usuario1
echo "Pedira contraseña: 1"
sudo passwd usuario2
echo "Pedira contraseña: 12"
sudo passwd usuario3
echo "Pedira contraseña: 123"

echo "Se muestra la informacion del usuario 1"
sudo id usuario1


echo "Parte2"
echo "Se crean los grupos"
sudo groupadd grupo1
sudo groupadd grupo2

echo "Se agregan a los grupos"
sudo usermod --append --groups grupo1 usuario1
sudo usermod --append --groups grupo2 usuario2

echo "Se verifican que se hayan agregado correctamente"
sudo groups usuario1
sudo groups usuario2


echo "Se elimina el grupo 2"
sudo groupdel grupo2


echo "Parte3"
echo "Creacion de archivos y directorios"
echo "Se inicia sesión como usuario 1"

sudo login usuario1
echo "Pedira contraseña: 1"

ls
echo "Se crea el archivo txt"
touch archivo1
nano archivo1
echo "Se escribio: Hola mundo"

mkdir directorio1
cd directorio1
touch archivo2.txt
ls -l archivo2.txt
echo "La salida: -rw-rw-r-- 1 usuario1 usuario1 0 ago  4 22:37 archivo2.txt"
ls -ld directorio1
echo "La salida: drwxrwxr-x 2 usuario1 usuario1 4096 ago  4 22:34 directorio1" 

chmod 640 archivo1.txt
$ ls
archivo1  archivo1.txt	archivo2.txt  directorio1
$ chmod 640 archivo1.txt
$ ls -l archivo1.txt
-rw-r----- 1 usuario1 usuario1 0 ago  4 22:30 archivo1.txt
$ cd directorio1
$ chmod u+x archivo2.txt
$ ls -l archivo2.txt
-rwxrw-r-- 1 usuario1 usuario1 0 ago  4 22:47 archivo2.txt
$ 

chgrp grupo1 archivo2.txt
ls -l archivo2.txt

chmod 740 /home/usuario1/directorio1
sudo -u usuario2 -i
cat /home/usuario1/archivo1.txt
cat /home/usuario1/directorio1/archivo2.txt

ls -l /home/usuario1/archivo1.txt
ls -l /home/usuario1/directorio1/archivo2.txt
ls -ld /home/usuario1/directorio1


echo "Reflexion 1"
echo "Me parece importante debido a que podemos establecer limites en nuestra computadora de que cosas o no
pueden hacer los distintos usuarios en ella y esto a nivel servidor es aun mas importante para proteger la informacion
que puede llegar a ser bastante sensible de usuarios que no tienen que verla"
echo "Reflexion 2"
echo "Por mi falta de experiencia solo conozco chmod, pero investigando encontre el comando "chown" que sirve para cambiar grupo de una manera mas ordenada" 

