Readme
# Trabajo individual

Jhoel Rodrigo Alata Cruz

## Clase 1

### ¿Qué es Git?

Es un sistema de control de veriones distribuido (VCS)

### ¿Cómo nació Git?

En 2005 Linus Torvalds tuvo un desacuerdo con BitKEPPER ya que ya no le iba dejar usar su sistema de versiones por lo que se puso a crear git en 3 semanas. 

### ¿Cómo descargar en Git?

Vas a tu navegador favorito y buscas git download , escojes tu S.O y haces click en descargar , una vez descargado
haces correr el instalador en tu compu.

### Comandos basicos para configurar
```
git config --global user.name "Tu Nombre"
git config --global user.email "tu@correo.com"
git config --global core.autocrlf true
```
### Tarea

Crear una carpeta donde sera  tu repositorio para los trabajos individuales
con: 
```
git init
git add README.md
git commit -m "mi primer commit"
```
La carpeta donde hiciste "git init" sera el lugar donde git pueda ver todos los archivos.

## Clase 2

### Los estados de Git:

1) El directorio de trabajo:  
Aquí creas, modificas o eliminas archivos. Git no realiza cambios automáticamente, solo observa y clasifica los archivos como:

- **UNTRACKED**: Archivos nuevos que no tienen seguimiento.
- **MODIFIED**: Archivos existentes que han sido modificados.

Nota: para ver el estado de los archivos:
```
git status
```

Nota: para ver todos los commits realizados:
```
git log
```
Comando: para restaurar un archivo a su estado anterior (si está en seguimiento):
```
git restore nombre_archivo
```

- ¿Qué es el .gitignore?  
Es un archivo donde defines qué archivos o carpetas Git debe ignorar y no incluir en el repositorio.  
Puedes usar nombres específicos o extensiones para filtrar archivos.

---

2) Stage (Area):  
Permite seleccionar los archivos que se incluirán en el próximo commit.  
Es decir, Git sabe qué cambios deseas guardar en el historial.

Comandos:
```
git add nombre_archivo
```

Para añadir todos los archivos:
```
git add .
```
Si quieres sacar un archivo de stage ejecuta este comando:
```
git restore --staged <archivo>
```

Nota: para ver commits de forma resumida:
```
git log --oneline
```
---

3) Repositorio local:  
Aquí se guardan los cambios que están en el área de stage.

Comando:
```
git commit -m "mensaje descriptivo"
```
Nota: para deshacer el último commit:
```
git reset --soft HEAD~1
```

Nota: ¿qué es HEAD?  
Es un puntero que indica en qué commit estás trabajando actualmente.

---

### Buenas prácticas:

1. Realizar commits pequeños y con significado.

2. Escribir los mensajes en inglés usando verbos en imperativo:
   - Add: Significa que se añade un nuevo archivo.
   - Change: Significa que se modifica un archivo existente.
   - Fix: Significa que se arregla un bug.
   - Remove: Significa que se elimina un archivo existente.

3. No usar punto final ni puntos suspensivos.

4. Usar máximo 50 caracteres, siendo claro y conciso.

5. Usar prefijos para mayor claridad:
```
git commit -m "<type>: <descripton>"
```

Prefijos:
- feat: nueva funcionalidad
- fix: corrección de errores
- perf: mejora de rendimiento
- build: cambios en el sistema de build
- ci: integración continua
- docs: documentación
- refactor: cambios internos sin afectar funcionalidad
- style: formato de código
- test: pruebas

6. Añadir más contexto en el cuerpo del commit cuando sea necesario, donde la primera línea será el título y desde la segunda línea
será el cuerpo (donde si hay que aplicar reglas de puntuación)con el comando:
```
git commit
```
Ejemplo:
feat: Add login feature

-Implement basic authentication
-Validate user credentials
-Improve login flow

## Clase 3

### ¿Qué es Github?

GitHub es una plataforma en la nube y una red social para desarrolladores que permite alojar, gestionar y colaborar en proyectos usando Git.

### Git vs Github

- Git: Es el sistema de control de versiones que crea los commits (puntos de guardado).
- Github: Es el servidor donde se almacenan esos commits y se pueden compartir con otros.

Nota: Github usa Git pero no son lo mismo.

---

### SSH vs HTTPS

Cuando trabajamos con repositorios remotos existen 2 formas:

HTTPS
- Pide autenticación cada vez (usuario + token).
- Puede ser incómodo.

SSH
- Usa una clave (key).
- No pide autenticación cada vez.

POR LO TANTO LO RECOMENDABLE ES USAR SSH.

---

### Configuración SSH

En la terminal (Linux o Git Bash en Windows):
```
ssh-keygen -t ed25519 -C "tu-correo@email.com"
```
luego:
```
cat ~/.ssh/id_ed25519.pub
```

Pasos:
- Copiar la clave generada
- Ir a Github → Settings
- SSH and GPG Keys
- Click en "New SSH Key"
- Pegar la clave y guardar

Verificar conexión:
```
ssh -T git@github.com
```

---

### Crear un repositorio en Github

1. Ir a tu perfil → Repositories
2. Click en New
3. Poner nombre y descripción
4. Click en Create Repository

---

### Conectar un repositorio local con Github

```
git remote add origin git@github.com:TuUser/TuRepo.git
```

Nota:
- remote: conexión a servidor externo
- origin: nombre por defecto de esa conexión

Renombrar rama principal:

```
git branch -M main
```

Para subir los cambios:

```
git push -u origin main
```

Nota: Debes tener:
- git init
- al menos un commit

---

### Clonar un repositorio

Con SSH (recomendado):

```
git clone “git@github.com:TuUser/TuRepo.git”
```

Con HTTPS:
```
git clone “https://github.com/TuUser/TuRepo.git”
```

Si usaste HTTPS y quieres cambiar a SSH:

```
git remote set-url origin “git@github.com:TuUser/TuRepo.git”
```
Para ver repositorio remoto:
```
git remote -v
```

---

### Subir y bajar cambios

Subir cambios:
```
git push origin <rama>
```

Significa:
- push: subir commits
- origin: servidor (Github)
- rama: rama que envías

---

Bajar cambios:
```
git pull origin <rama>
```

Significa:
- pull: traer cambios

---

### Ejemplo práctico

```
git add .
git commit -m "feat: Add login system "
git push origin main

```
en otra computadora:
```
git pull origin main
```

## Clase 4

### Git Remote

Permite gestionar conexiones con repositorios remotos (Github).

Comandos:
```
git remove -v
```
Muestra a qué repositorio remoto está conectado tu proyecto.

```
git remote add origin url-del-repositorio
```
Conecta tu repositorio local con uno en Github.

```
git remote set-url origin nueva-url
```

Cambia la URL del repositorio remoto (por ejemplo de HTTPS a SSH).

---

### Múltiples SSH

Sirve cuando tienes más de una cuenta de Github.

Cada cuenta necesita su propia clave SSH.

---

### Configurar múltiples SSH

Generar otra clave:

```
ssh-keygen -t ed25519 -C "tu-correo@email.com" -f ~/.ssh/id_nombre
```
Crea una nueva clave SSH con otro nombre.

Configurar archivo config:

CUENTA PRINCIPAL:

```
Host github.com
HostName github.com
User git
IdentityFile ~/.ssh/id_ed25519
```
CUENTA SECUNDARIA:

```
Host github-nombre
HostName github.com
User git
IdentityFile ~/.ssh/id_nombre
```
Define qué clave usar para cada cuenta.

Verificar:
```
ssh -T git@github-nombre
```
Verifica si la conexión con esa cuenta funciona.

Clonar usando ese host:
```
git clone git@github-nombre:usuario/repositorio.git
```
Clona el repositorio usando la cuenta correcta.

---

### Configuración local

Se aplica solo a un repositorio (sobrescribe la global).

```
git config user.name "Tu Nombre"
git config user.email "tu@correo.com"
```
Define el nombre y correo solo para ese repositorio.

---

### Git Checkout

Permite moverse entre commits o ramas.

Sirve para:
- Ver versiones antiguas
- Recuperar archivos
- Cambiar de rama

---

### Detached HEAD

HEAD apunta directamente a un commit (no a una rama).

- Estás viendo el pasado
- Si haces cambios se pueden perder

---

### Moverse entre commits

Ir a un commit:
```
git checkout hash-del-commit
```
Te lleva a una versión antigua del proyecto.

Volver a la rama:
```
git checkout main
```
Regresa a la versión actual del proyecto.

Guardar cambios hechos en ese estado:
```
git checkout hash-del-commit
```
Y con este comando puedes crear una nueva rama para no perder los cambios:
```
git checkout -b nueva-rama
```
---

### Buenas prácticas

- Hacer commit antes de usar checkout
- No trabajar mucho en detached HEAD
- Mantener limpio el directorio de trabajo
- Usar checkout para aprender del historial


## Clase 5

### ¿Qué son las ramas?

Son bifurcaciones del código que permiten trabajar en paralelo sin afectar la rama principal.

Sirven para:
- Trabajar en nuevas funcionalidades
- Probar cambios sin romper el proyecto
- Organizar el trabajo en equipo

---

### Git Branch

Permite gestionar las ramas del proyecto.
```
git branch
```
Muestra todas las ramas y en cuál estás (HEAD).
```
git branch -D nombre-rama
```
Elimina una rama.

---

### Git Checkout (con ramas)

Permite moverse entre ramas.

```
git checkout nombre-rama
```
Cambia a otra rama.
```
git checkout -b nombre-rama
```
Crea una rama y se mueve a ella directamente.

Nota: No debes tener cambios sin guardar.

---

### Git Checkout vs Git Switch

- git checkout: comando antiguo, hace muchas cosas (ramas, commits, archivos)
- git switch: comando nuevo, solo sirve para ramas (más seguro)

Ejemplo:
```
git switch nombre-rama
```
Cambia de rama de forma más segura.

---

### Gitflow básico

Es una forma de organizar el trabajo con ramas.

Sirve para:
- Mantener orden en el proyecto
- Trabajar en equipo
- Controlar versiones

---

### Ramas principales

main
- Contiene el código final (producción)

develop
- Donde se integran los cambios antes de pasar a main

---

### Ramas de apoyo

feature
- Para nuevas funcionalidades
- Nacen de develop y vuelven a develop

release
- Para preparar versiones
- Nacen de develop y van a main y develop

hotfix
- Para arreglos urgentes en producción
- Nacen de main y vuelven a main y develop

---

### Ejemplos de nombres

feature:
- feature/login
- feature/search-bar

release:
- release/v1.0.0

hotfix:
- hotfix/login-error
- hotfix/security-fix
---

### Resumen

- main → producción
- develop → desarrollo
- feature → nuevas funciones
- release → preparar versión
- hotfix → arreglos urgentes


