# Configuraciones para docker
# PostgreSQL

Persistencia en datos de un contenedor de PosgreSQL
Para persistir la información del banco de datos hay que crear un contenedor de datos y enlazarlo al contenedor de Postgres.

**docker create -v /var/lib/postgresql/data --name datospg postgres10.13 /bin/true**


> *-v /var/lib/postgresql/data : crea un volumen donde se almacenara la informacion en el equipo local.*     
> *--name datospg : nombre del contenedor 'datospg'.*      
> *postgres:10.13 : nuestro contenedor destino a enlazar, tambien se puede indicar el id del contenedor.*      

Enlazar nuestro volumen de datos a nuestro contenedor de PostgreSQL

**docker run --rm --volumes-from datospg -p 5432:5432 -e POSTGRES_PASSWORD=postgres postgres:10.13**

> *--rm elimina el contenedor al cerrarlo*     
> *--volumes-from datospg : indica utilice el volumen que hemos creado del contenedor.*     
> *-p 5432:5432 : como primer dato indicamos el puerto de nuestra maquina local separado por ':' que indica el puerto del contenedor docker (en este caso postgres)*     
> *Tambien podemos agregar un nombre al contenedor con la instruccion --name nombreContenedor.*   
> *-e POSTGRES_PASSWORD=postgres : indicamos la contraseña del usuario postgres de la base de datos del contnedor*         
