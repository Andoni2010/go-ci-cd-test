# Go CI/CD Example

Este es un ejemplo básico de un proyecto Go configurado con un pipeline de CI/CD utilizando GitHub Actions. En este proyecto se aprenderá cómo configurar un proyecto Go, gestionarlo con Git, y automatizar el proceso de integración y despliegue continuo.

### **Estructura del Proyecto**

  ```bash
go-ci-cd-test/
│
├── .github/
│   └── workflows/
│       └── ci.yml          # Archivo de configuración para GitHub Actions
│
├── main.go                 # Código fuente principal de Go
├── go.mod                  # Archivo de gestión de dependencias de Go
├── .gitignore              # Archivos y directorios a ser ignorados por Git
└── README.md               # Documentación del proyecto
 ```
---

### **Pasos Seguidos en el Proyecto**

---

1. **Inicialización del Proyecto Go**

   Iniciaste el proyecto Go creando un archivo `main.go` con el siguiente contenido básico:

   ```go
   package main

   import "fmt"

   func main() {
       fmt.Println("Hello, CI/CD with Go!")
   }

---

2. **ICreación del Archivo go.mod**

   El archivo go.mod se generó para gestionar las dependencias del proyecto. Esto se hace con el comando:

   ```go
    go mod init go-ci-cd-test

  Esto indica a Go que el proyecto usa módulos, que es un sistema para gestionar las     dependencias.

  Además, después de agregar dependencias (si se necesitaran), el comando go mod tidy puede ser   utilizado para limpiar y actualizar las dependencias.

---

3. **Archivo .gitignore**
   Este archivo contiene reglas para indicarle a Git qué archivos y directorios deben ser ignorados en el repositorio. Un ejemplo de lo que podría contener:
    ```go
    /bin/
    /vendor/
    *.log
    *.exe
    *.test
  Esto asegura que no se suban archivos innecesarios al repositorio, como binarios o archivos temporales.

---

4. **Creación del Repositorio Git**
  Se inicializó un repositorio Git en la carpeta del proyecto con los siguientes comandos:
    ```
    git init
    git add .
    git commit -m "Initial commit with main.go, go.mod, and .gitignore"
    ```
  Esto asegura que no se suban archivos innecesarios al repositorio, como binarios o archivos temporales.
* git init: Inicializa el repositorio local.
* git add .: Añade todos los archivos del proyecto al área de preparación para el commit.
* git commit -m "Initial commit...": Crea un commit con un mensaje descriptivo.

---

5. **Subir al Repositorio Remoto (GitHub)**
  Luego, se configuró un repositorio en GitHub y se conectó el repositorio local con el remoto. Para hacer esto, se usaron los siguientes comandos:
    ```
    git remote add origin https://github.com/Andoni2010/go-ci-cd-test.git
    git push -u origin main
    ```
git remote add origin <url>: Conecta el repositorio local con el repositorio remoto en GitHub.
git push -u origin main: Sube los cambios locales al repositorio remoto.

---

6. **Configuración del Pipeline CI/CD (GitHub Actions)**
  Se configuró un flujo de trabajo de CI/CD usando GitHub Actions. El archivo de configuración se encuentra en .github/workflows/ci.yml. Este archivo define los pasos que se deben ejecutar automáticamente cada vez que se haga un commit o un push al repositorio.

  Un ejemplo básico de un archivo de flujo de trabajo podría ser:
  ```yaml
name: Go CI/CD Workflow

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Check out the repository
        uses: actions/checkout@v2

      - name: Set up Go
        uses: actions/setup-go@v2
        with:
          go-version: '1.19'

      - name: Install dependencies
        run: go mod tidy

      - name: Run tests
        run: go test

      - name: Build the application
        run: go build

      - name: Deploy (optional step)
        run: |
          echo "Deploying to server..."
          # Aquí se pueden agregar pasos para desplegar la app a producción.
  ```
---

##Comandos Git Utilizados##

  A continuación, los comandos de Git utilizados durante este proyecto:

  Iniciar un Repositorio Git

  ```bash
  git init
  ```
  
  Agregar Archivos al Repositorio

  ```bash
  git add .
  ```
  
  Crear un Commit
  
  ```bash
  git commit -m "Mensaje del commit"
  ```
  
  Conectar con un Repositorio Remoto
  
  ```bash
  git remote add origin <URL del repositorio>
  ```
  
  Subir los Cambios al Repositorio Remoto
  
  ```bash
  git push -u origin main
  ```
 
  Ver el Estado del Repositorio
  
  ```bash
  git status
  ```
  
  Ver el Historial de Commits
  
  ```bash
  git log
  ```
  
  Obtener Cambios del Repositorio Remoto
  
  ```bash
  git pull
  ```

---

##Conclusión##

  Con estos pasos, has configurado un proyecto Go básico, lo has versionado con Git y configurado un flujo de trabajo CI/CD utilizando GitHub Actions. Esto te permitirá automatizar el proceso de pruebas y despliegue de tu aplicación cada vez que realices un cambio en el código.

  Ahora puedes continuar explorando más sobre Go, Git y CI/CD, y aplicar estos conocimientos en proyectos más complejos.

  ---
