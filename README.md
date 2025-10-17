 Flujo de Git con Ramas y Conflictos

Estudiante:Esteban Marenco y Dereck vallejos 
Curso: Programación 2  


 Objetivo
Aplicar el flujo de trabajo con Git y GitHub, creando ramas que simulen ambientes de desarrollo (DEV, QA, UAT, PROD), y aprender a resolver conflictos de código durante los merges.



 Configuración 

1 Creación de cuenta GitHub
Se creó una cuenta en gitHub bajo el usuario esteban23b. 


2 Configuración de Git local
Se configuró el nombre y correo

git config --global user.name "Esteban Marenco"
git config --global user.email "jorgeortegamarenco@gmail.com"


3 Creación del repositorio en GitHub
Se creó el repositorio practica-flujo-git.


Luego se clonó localmente

git clone https:
 Creación de ramas de ambientes
Se crearon y subieron las ramas correspondientes


git checkout -b dev
git push -u origin dev

git checkout -b qa
git push -u origin qa

git checkout -b uat
git push -u origin uat

git checkout -b main
git push -u origin main

Nueva funcionalidad
Se creó una rama feature/nueva-funcionalidad para agregar una mejora al archivo README.md 


git checkout -b feature/nueva-funcionalidad
Se editó el archivo con una breve descripción del cambio.


 Flujo de merges
Los cambios se llevaron progresivamente por los ambientes:


# 1. De feature → dev
git checkout dev
git merge feature/nueva-funcionalidad

# 2. De dev → qa
git checkout qa
git merge dev

# 3. De qa → uat
git checkout uat
git merge qa

# 4. De uat → main
git checkout main
git merge uat


 Simulación de conflicto
Se editó el mismo archivo (README.md) en dos ramas distintas (dev y feature/nueva-funcionalidad) para provocar un conflicto.

conflicto

# 1. Modificar el mismo archivo en dev
git checkout dev
echo "Cambio en DEV" >> README.md
git add .
git commit -m "Cambio en DEV"
git push origin dev

# 2. se modifico el mismo archivo en feature
git checkout feature/nueva-funcionalidad
echo "Cambio en feature" >> README.md
git add .
git commit -m "Cambio en feature"
git push origin feature/nueva-funcionalidad

# 3. Intentar merge
git checkout dev
git merge feature/nueva-funcionalidad
# Aquí verás el conflicto

git merge feature/nueva-funcionalidad
Aparecieron los marcadores de conflicto:
solución 

<<<<<<< HEAD
cambio en dev
=======
cambio en feature
>>>>>>> feature/nueva-funcionalidad
lo se resolví editando el bloc


# 2. 
Cambio en DEV
Cambio en feature

# 3. 
git add README.md
git commit -m "fix: resolver conflicto entre dev y feature"
git push origin dev

# 4. 
git checkout qa
git merge dev
git push origin qa

git checkout uat
git merge qa
git push origin uat

git checkout master
git merge uat
git push origin master




https://github.com/Dereck-Vallejos26/practica-flujo-git.git

