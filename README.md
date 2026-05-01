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
```git status
```

Nota: para ver todos los commits realizados:
```git log
```
Comando: para restaurar un archivo a su estado anterior (si está en seguimiento):
```git restore nombre_archivo
```

- ¿Qué es el .gitignore?  
Es un archivo donde defines qué archivos o carpetas Git debe ignorar y no incluir en el repositorio.  
Puedes usar nombres específicos o extensiones para filtrar archivos.

---

2) Stage (Area):  
Permite seleccionar los archivos que se incluirán en el próximo commit.  
Es decir, Git sabe qué cambios deseas guardar en el historial.

Comandos:
```git add nombre_archivo
```

Para añadir todos los archivos:
```git add .
```
Si quieres sacar un archivo de stage ejecuta este comando:
```git restore --staged <archivo>
```

Nota: para ver commits de forma resumida:
```git log --oneline
```
---

3) Repositorio local:  
Aquí se guardan los cambios que están en el área de stage.

Comando:
```git commit -m "mensaje descriptivo"
```
Nota: para deshacer el último commit:
```git reset --soft HEAD~1
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
```git commit -m "<type>: <descripton>"
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
```git commit
```
Ejemplo:
feat: Add login feature

-Implement basic authentication
-Validate user credentials
-Improve login flow


