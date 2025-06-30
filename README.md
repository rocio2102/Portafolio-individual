# CLASE 5: Teoría sobre Staging, Gitflow, Ramas y Merge

## ¿Qué es el Staging?

Cuando usamos `git init`, se crea el repositorio Git en la carpeta actual. A partir de ese momento, Git maneja tres zonas:

- **Área de trabajo (Working Directory):** donde editamos los archivos (por ejemplo, `historia.txt`).
- **Área de Staging (Index):** una zona temporal en memoria RAM. Allí colocamos los archivos que queremos guardar en el próximo commit usando `git add`.
- **Repositorio (.git):** cuando hacemos `git commit`, los archivos en staging se guardan con un hash en el historial del proyecto.

### Flujo de trabajo

```bash
git add historia.txt    # Pasa el archivo al staging
git commit -m "Mensaje" # Crea un commit en el repositorio con lo que estaba en staging
```

---

# CLASE 6: Reset y Checkout

En esta clase aprendimos a:

- Volver a versiones anteriores de nuestro repositorio usando `git reset` (suave y duro).
- Visualizar los cambios con `git diff`.
- Explorar versiones específicas con `git checkout`.
- Crear, usar y borrar ramas para organizar el trabajo.
- La importancia de usar ramas secundarias para evitar errores en la rama principal.

## Comandos usados

```bash
git reset --soft <hash>
git reset --hard <hash>
git checkout <hash>
git branch <nombre>
git branch -d <nombre>
```

---

# CLASE 7: Git reset vs Git rm

## Git Reset

- Permite deshacer cambios y mover la historia del repositorio a commits anteriores.
- Modos:
  - `--soft`: mantiene los cambios en staging para un nuevo commit.
  - `--mixed`: elimina los cambios de staging pero los mantiene en working directory.
  - `--hard`: elimina todos los cambios y resetea el repositorio completamente.
- `git reset HEAD <archivo>` quita un archivo del área de staging sin perder los cambios.

## Git rm

- Elimina archivos del repositorio y opcionalmente del disco.
- Modos principales:
  - `git rm --cached <archivo>` elimina el archivo solo de git, pero lo deja en disco.
  - `git rm --force <archivo>` elimina el archivo de git y del disco.

## Diferencias clave

- `git reset` mueve cambios dentro del control de versiones sin borrar archivos.
- `git rm` elimina archivos del repositorio (y del disco si se usa `--force`).

---

# CLASE 8: Flujo de trabajo básico con un repositorio remoto

## ¿Qué es un repositorio remoto?

Un **repositorio remoto** es una copia de tu proyecto que está alojada en servidores como:

- GitHub
- GitLab
- BitBucket

Gracias a estos servidores, tu equipo puede:

- Descargar los archivos del proyecto.
- Hacer cambios y subirlos.
- Colaborar en simultáneo.

## Comandos básicos

```bash
git clone url_del_servidor_remoto
git push
git fetch
git merge
git pull
```

---

# CLASE 9A: Introducción a las ramas o branches de Git

## ¿Qué son las ramas en Git?

Permiten trabajar en nuevas funcionalidades o experimentar sin afectar la rama principal `master` o `main`.

### Conceptos clave

- **HEAD**: indica en qué rama y commit estamos trabajando.
- Al crear una nueva rama, todos los commits de `main` se copian.
- Hasta que no se haga un merge, los cambios no impactan la rama principal.

## Comandos

```bash
git branch nombre-rama
git checkout nombre-rama
git checkout -b nueva-rama
git reset id-commit
git checkout rama-o-id-commit
```

---

# CLASE 9B: Fusión en Git con merge

## ¿Qué es un Merge en Git?

El comando `git merge` permite integrar ramas paralelas dentro de una sola rama.

### Cómo funciona

- Busca un commit base común
- Crea un nuevo commit de fusión
- En caso de conflicto, se deben resolver manualmente

## Comandos

```bash
git checkout master
git merge segunda
```

---

# CLASE 10A: Resolución de conflictos al hacer merge

## ¿Qué es un conflicto?

Cuando dos ramas hacen cambios distintos en la misma línea de un archivo. Git no puede decidir automáticamente.

## ¿Cómo resolverlo?

1. Realizar el `merge`
2. Git marca los archivos como `Unmerged`
3. Editar manualmente
4. Ejecutar:

```bash
git add .
git commit -m "Conflicto resuelto"
```

---

# CLASE 10B: Cómo funcionan las llaves públicas y privadas

## ¿Qué son?

Sistema de cifrado asimétrico que permite enviar mensajes seguros.

### ¿Cómo funciona?

- Se generan dos llaves: pública y privada.
- Se cifra con la pública y se descifra con la privada.

> La llave **privada** nunca se comparte.

---

# CLASE 11: Configura tus llaves SSH en local

## ¿Por qué usar SSH?

Para mayor seguridad y evitar contraseñas cada vez que interactuás con GitHub.

## ¿Cómo funciona?

Se sube la llave pública a GitHub. Git verifica la conexión con tu llave privada.

## Comandos

```bash
git config -l
```

---

# CLASE 12: Tarea

Agregar esta clase al README.md y hacer commit + push:

```bash
git add README.md
git commit -m "Clase 12: Llaves públicas y privadas"
git push
```
