### 1. Sistema de archivos GNU/Linux

1.1 Crear un repositorio "INFO133" en su carpeta de usuario (/home/REEMPLAZAR_CON_SU_NOMBRE_DE_USUARIO) con el comando mkdir

~~~bash
mkdir INFO133
~~~

1.2 Crear un archivo texto vacio llamado mis_comandos.txt con el comando touch

~~~bash
touch mis_comandos.txt
~~~

1.3 Escribir "Hola" en el archivo mis_comandos.txt

~~~bash
echo "Hola" > mis_comandos.txt
~~~

1.4 Utilizar el comando cat para mostrar el contenido de mis_comandos.txt

~~~bash
cat mis_comandos.txt
~~~

### 2. Gestión de permisos en el sistema de archivos

2.1 Crear un usuario llamado juan y darle como password juan2019

~~~bash
adduser juan && passwd juan
juan2019
~~~

2.1 En su carpeta de trabajo 'INFO133', crear un archivo llamado test.txt que el usuario juan podrá leer pero no modificar.

~~~bash
touch INFO133/test.txt
~~~