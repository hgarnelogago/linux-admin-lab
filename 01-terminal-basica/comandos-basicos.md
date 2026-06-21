# Comandos básicos de Linux

## Objetivo

Aprender los comandos básicos de Linux para moverme por la terminal, consultar información del sistema, crear archivos y carpetas, visualizar contenido y empezar a trabajar como administrador de sistemas desde consola.

---

## Comandos de ubicación y navegación

### pwd

Muestra la ruta completa del directorio actual.

```bash
pwd
```

Ejemplo de salida:

```text
/home/domhector/linux-admin-lab
```

Este comando es útil para saber dónde estoy antes de crear, editar o borrar archivos.

---

### cd

Permite cambiar de directorio.

```bash
cd nombre_directorio
```

Ejemplos:

```bash
cd
cd linux-admin-lab
cd ..
cd /etc
```

Explicación:

* `cd` sin nada me lleva a mi carpeta personal.
* `cd ..` sube un nivel.
* `cd /etc` me lleva al directorio `/etc`.

---

### ls

Lista archivos y directorios.

```bash
ls
```

Opciones útiles:

```bash
ls -l
ls -la
ls -lh
```

Explicación:

* `ls` muestra el contenido del directorio.
* `ls -l` muestra información detallada.
* `ls -la` muestra también archivos ocultos.
* `ls -lh` muestra tamaños en formato legible.

---

## Comandos de información del sistema

### whoami

Muestra el usuario actual.

```bash
whoami
```

Ejemplo:

```text
domhector
```

---

### hostname

Muestra el nombre del equipo.

```bash
hostname
```

Mostrar la IP del equipo:

```bash
hostname -I
```

Este comando es muy útil para saber la IP del servidor antes de conectarme por SSH.

---

### uname

Muestra información del sistema.

```bash
uname
```

Información más completa:

```bash
uname -a
```

---

### lsb_release

Muestra información de la distribución Linux instalada.

```bash
lsb_release -a
```

En Ubuntu Server sirve para comprobar la versión instalada.

---

## Comandos para crear archivos y carpetas

### mkdir

Crea directorios.

```bash
mkdir pruebas
```

Crear varios directorios:

```bash
mkdir docs scripts logs
```

Crear una estructura completa:

```bash
mkdir -p laboratorio/docs
```

La opción `-p` crea también las carpetas intermedias si no existen.

---

### touch

Crea archivos vacíos.

```bash
touch archivo.txt
```

También puede actualizar la fecha de modificación de un archivo existente.

---

### nano

Abre un editor de texto en terminal.

```bash
nano archivo.txt
```

Guardar en nano:

```text
CTRL + O
ENTER
CTRL + X
```

Explicación:

* `CTRL + O` guarda el archivo.
* `ENTER` confirma el nombre.
* `CTRL + X` sale del editor.

---

## Comandos para ver contenido

### cat

Muestra el contenido completo de un archivo.

```bash
cat archivo.txt
```

Ejemplo:

```bash
cat README.md
```

---

### less

Permite ver archivos largos página a página.

```bash
less archivo.txt
```

Controles dentro de `less`:

```text
Espacio    avanzar
b          retroceder
/ palabra  buscar una palabra
q          salir
```

---

### head

Muestra las primeras líneas de un archivo.

```bash
head archivo.txt
```

Mostrar solo las primeras 5 líneas:

```bash
head -n 5 archivo.txt
```

---

### tail

Muestra las últimas líneas de un archivo.

```bash
tail archivo.txt
```

Mostrar las últimas 20 líneas:

```bash
tail -n 20 archivo.txt
```

Ver un archivo en tiempo real:

```bash
tail -f archivo.log
```

Este comando es muy útil para revisar logs.

---

## Comandos para copiar, mover y borrar

### cp

Copia archivos o directorios.

Copiar un archivo:

```bash
cp archivo.txt copia.txt
```

Copiar un archivo a otra carpeta:

```bash
cp archivo.txt docs/
```

Copiar una carpeta completa:

```bash
cp -r docs backup-docs
```

La opción `-r` significa recursivo y se usa para copiar directorios.

---

### mv

Mueve o renombra archivos y carpetas.

Renombrar un archivo:

```bash
mv archivo.txt notas.txt
```

Mover un archivo a otra carpeta:

```bash
mv notas.txt docs/
```

---

### rm

Elimina archivos o directorios.

Eliminar un archivo:

```bash
rm archivo.txt
```

Eliminar una carpeta y su contenido:

```bash
rm -r carpeta
```

Forzar eliminación:

```bash
rm -rf carpeta
```

Importante: `rm -rf` es peligroso porque borra sin preguntar. Antes de usarlo conviene comprobar siempre dónde estoy con:

```bash
pwd
```

---

## Comandos para escribir texto en archivos

### echo

Muestra texto en pantalla o escribe texto en archivos.

Mostrar texto:

```bash
echo "Hola Linux"
```

Crear o sobrescribir un archivo:

```bash
echo "Primera línea" > archivo.txt
```

Añadir contenido al final:

```bash
echo "Segunda línea" >> archivo.txt
```

Diferencia importante:

```text
>  sobrescribe el archivo
>> añade contenido al final
```

---

## Comandos de búsqueda

### grep

Busca texto dentro de archivos o salidas de comandos.

Buscar una palabra dentro de un archivo:

```bash
grep "error" archivo.log
```

Buscar ignorando mayúsculas y minúsculas:

```bash
grep -i "error" archivo.log
```

Buscar de forma recursiva dentro de una carpeta:

```bash
grep -r "ssh" /etc/
```

---

### find

Busca archivos y directorios.

Buscar un archivo por nombre:

```bash
find . -name "archivo.txt"
```

Buscar archivos `.md`:

```bash
find . -name "*.md"
```

Buscar solo directorios:

```bash
find . -type d
```

Buscar solo archivos:

```bash
find . -type f
```

---

## Comandos de ayuda

### man

Muestra el manual de un comando.

```bash
man ls
```

Salir del manual:

```text
q
```

Ejemplos:

```bash
man cp
man grep
man find
```

---

### --help

Muestra ayuda rápida de un comando.

```bash
ls --help
cp --help
mkdir --help
```

---

## Comandos de disco y memoria

### df

Muestra el uso de disco de los sistemas de archivos.

```bash
df -h
```

La opción `-h` muestra los tamaños en formato legible, como MB o GB.

---

### du

Muestra cuánto ocupa un archivo o directorio.

```bash
du -sh carpeta
```

Ejemplo:

```bash
du -sh /var/log
```

La opción `-s` resume y `-h` muestra el tamaño en formato legible.

---

### free

Muestra el uso de memoria RAM.

```bash
free -h
```

---

## Comandos de procesos

### ps

Muestra procesos en ejecución.

```bash
ps
```

Ver más procesos:

```bash
ps aux
```

Buscar un proceso concreto:

```bash
ps aux | grep ssh
```

---

### top

Muestra procesos y consumo del sistema en tiempo real.

```bash
top
```

Salir de `top`:

```text
q
```

---

### htop

Es una versión más cómoda de `top`.

```bash
htop
```

Si no está instalado:

```bash
sudo apt install htop -y
```

Salir de `htop`:

```text
q
```

---

## Otros comandos útiles

### clear

Limpia visualmente la pantalla de la terminal.

```bash
clear
```

No borra archivos ni comandos, solo limpia la pantalla.

---

### history

Muestra el historial de comandos ejecutados.

```bash
history
```

Ejecutar un comando anterior usando su número:

```bash
!25
```

---

### date

Muestra la fecha y hora del sistema.

```bash
date
```

---

### uptime

Muestra cuánto tiempo lleva encendido el sistema.

```bash
uptime
```

También muestra la carga media del sistema.

---

### which

Muestra la ruta de un comando.

```bash
which bash
which nano
which git
```

Ejemplo de salida:

```text
/usr/bin/git
```

---

### file

Muestra el tipo de archivo.

```bash
file README.md
file /bin/bash
```

---

### wc

Cuenta líneas, palabras y caracteres.

```bash
wc archivo.txt
```

Contar solo líneas:

```bash
wc -l archivo.txt
```

---

## Pipes y redirecciones

### Pipe |

El símbolo `|` envía la salida de un comando como entrada de otro.

Ejemplo:

```bash
ps aux | grep ssh
```

Aquí `ps aux` muestra procesos y `grep ssh` filtra los que contienen la palabra `ssh`.

---

### Redirección >

Guarda la salida de un comando en un archivo, sobrescribiendo el contenido anterior.

```bash
ls -la > listado.txt
```

---

### Redirección >>

Añade la salida de un comando al final de un archivo.

```bash
date >> registro.txt
```

---

## Ejercicio práctico

Crear una carpeta de pruebas:

```bash
cd
mkdir -p laboratorio-comandos/{docs,logs,backups}
cd laboratorio-comandos
```

Crear un archivo:

```bash
touch docs/notas.txt
```

Escribir contenido:

```bash
echo "Estoy practicando comandos basicos de Linux" > docs/notas.txt
echo "Segunda linea de prueba" >> docs/notas.txt
```

Ver el contenido:

```bash
cat docs/notas.txt
```

Copiar el archivo:

```bash
cp docs/notas.txt backups/notas-backup.txt
```

Buscar archivos:

```bash
find . -type f
```

Ver estructura:

```bash
tree .
```

Si `tree` no está instalado:

```bash
sudo apt install tree -y
```

---

## Conclusión

Estos comandos son la base para moverme por Linux desde terminal. Me permiten navegar por el sistema, crear archivos y carpetas, visualizar contenido, buscar información, controlar procesos y empezar a administrar un servidor Linux de forma práctica.
