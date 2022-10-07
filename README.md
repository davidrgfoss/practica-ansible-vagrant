# practica-ansible-vagrant

Recomiendo usar el comando "vagrant up --no-provision", debido a que la forma de funcionar de vagrant con ansiblo es un poco erratica. Esto se debe a que ejecuta el ansible en las maquinas de froma secuencial seegun las termina de levantar haciendo que la receta pueda fallar si intenta configurar una maquina antes que otra o que todavia no esta levantada.

En caso de tener maquinas diferentes en vagrant, segun la documentación deberiamos ejecutar "playbooks" diferentes para cada una, de esta forma no habria dependencia entre las maquinas y posiblemente ningun error.
