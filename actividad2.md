# Luis Mariano Moreira García 202010770
# Actividad 2 - Scripting


Obtenemos la respuesta de la api
response=$(wget -qO- "https://api.github.com/users/Low-Chocs")

Se obtienen los datos:

name=$(echo $response | jq -r '.login')

id=$(echo $response | jq -r '.id')

dates=$(echo $response | jq -r '.created_at')

Se escribe el mensaje:
message="Hola ${name}  User ID: ${id}  Cuenta fue creada el: ${dates} "

Se crea el archivo y la carpeta nueva con la fecha:

destination="/home/chocs/Desktop/temp"

date=$(date +'%Y%m%d%H%M%S')

directory="${destination}/${date}"

file="${directory}/saludos.log"

mkdir -p "$directory"

touch "$file"


echo $message >> $file

