
[![GitHub watchers](https://img.shields.io/github/watchers/Naereen/StrapDown.js.svg?style=social&label=Watch&maxAge=2592000)](https://github.com/superpollo2/workshp-github)
[![GitHub stars](https://img.shields.io/github/stars/Naereen/StrapDown.js.svg?style=social&label=Star&maxAge=2592000)](https://github.com/superpollo2/workshp-github)

# 🌟 workshop-github 🌟
¿Sabías que tu perfil de GitHub puede ser mucho más que una simple lista de repositorios? es tu portafolio profesional, en este workshop, aprenderás a transformar tu perfil de GitHub en una verdadera carta de presentación. Te mostraremos cómo personalizar tu perfil para visualizar tus habilidades, proyectos y logros.

[![forthebadge made-with-markdown](http://ForTheBadge.com/images/badges/made-with-markdown.svg)]([https://www.python.org/](https://www.markdownguide.org/getting-started/))

## Crea un nuevo repo secreto 🔐
1. Crear un nuevo repositorio (parte superior derecha dentro la navegación)
<img src="https://github.com/user-attachments/assets/70a74d1d-7913-4c6c-a80e-f34b4173345f" alt="new repo" width="200">

2. En el nombre de repositorio colocar el mismo nombre de usuario que tenemos
Al colocarlo te aparece el mensaje de que el owner/owner es un repositorio especial
que se puede usar para agregar un README a tu perfil de GitHub
***Es importante que selecciones las opciones de:
- Public
- Add a README file***
    
![image](https://github.com/user-attachments/assets/f5ee47ac-0359-48cf-a7cc-38df5dd7a415)

1. Vuelve al inicio de tu perfil para ver el resultado
   
![image](https://github.com/user-attachments/assets/b0355506-77c3-4af9-9729-f324648f79f8)

## Usemos Git Actions para construir metricas

### Crear nuevo token
1. Ve a **Settings** (Configuración) desde tu perfil.
2. Selecciona **Developer settings** en la barra lateral.
3. Haz clic en **Personal access tokens** y luego en **Tokens (classic)**.
4. Haz clic en **Generate new token**.
5. Escribe una descripción, selecciona permisos para `repo`.
6. Haz clic en **Generate token**.
7. Copia el token y guárdalo en un lugar seguro.

### Crea una nueva Variable de actions en el repositorio

1. Ve a tu **repositorio** en GitHub.
2. Haz clic en **Settings** (Configuración) en la parte superior del repositorio.
3. En la barra lateral izquierda, selecciona **Secrets and variables** y luego **Actions**.
4. Haz clic en **New repository secret**.
5. En el campo **Name**, escribe `METRICS_TOKEN`.
6. En el campo **Value**, pega el token que creaste.
7. Haz clic en **Add secret** para guardar el secreto.



### Workflow base
Usa este workflow base para crear un nuevo actions generico

> [!IMPORTANT]
> Yaml es un lenguaje en el que debes cuidar mucho la identación,
> un solo espacio mal puesto te generara problemas.

 ```yaml
name: Half-year calendar

on:
  schedule:
    - cron: "0 0 * * *" 
  workflow_dispatch:
  push:
    branches:
      - main
      
jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      # Checkout the repository
      - name: Checkout repository
        uses: actions/checkout@v3
 ```
### Explicación del cron ⏲️
Esta tarea la ejecutaremos con constancia puesto que las estadisticas iran cambiando
y queremos que los plugins esten actualizados

> [!NOTE]
> un Cron es una tarea automatica.

 ```Scss
└── * * * * * * 
    ├── minute (0-59)
    ├── hour (0-23)
    ├── day_of_month (1-31)
    ├── month (1-12)
    ├── mday_of_week (0-6)
    └── year (1970-2199)
 ```

## Agreguemos cositas bonitas a tu readme 🤟🫀
Usaremos actions para construir plugins basados en las estadisticas
e información de tus repositorios (publicos), interacciones, contribuciones
y otros. 
Cada uno de las siguientes tareas las agregaremos en el Actions en steps luego del primero.

### Plantilla básica 🐿️

<img src="https://github.com/user-attachments/assets/b5a4e232-4f81-4610-9b25-1a380766e262" alt="calendar full year" width="320">

 ```yaml
      # Generate basic profile
      - name: Generate basic profile
        uses: lowlighter/metrics@latest
        with:
          filename: basicprofile.plugin.classic.svg
          token: ${{ secrets.METRICS_TOKEN }}
          template: classic
          base: header, activity, community, repositories, metadata
          config_timezone: America/Bogota
          plugin_introduction: yes
          plugin_introduction_title: yes
          
          
 ```
### Pinned Repositorios 💘

<img width="396" alt="image" src="https://github.com/user-attachments/assets/7479658a-b30d-409d-b011-b744367df329">

```yaml
      # Generate repositories
      - name: Pinned repositories
    	uses: lowlighter/metrics@latest
    	with:
    	  filename: repositories.pinned.svg
    	  token: ${{ secrets.METRICS_TOKEN }}
    	  base: ""
    	  plugin_repositories: yes
    	  plugin_repositories: yes
    	  plugin_repositories_featured:  sistema-gestion-inventarios,  hoja_de_vida 
    	  plugin_repositories_order: featured, pinned, starred, random
    	  plugin_repositories_pinned: 6
    	  plugin_repositories_affiliations: owner, collaborator, organization_member      
```	

### Calendar 📆

<img src="https://github.com/user-attachments/assets/a0704532-5401-44d5-ac0f-019ecd477ed0" alt="calendar full year" width="320">

 ```yaml
      # Generate full calendar
      - name: Generate full year calendar
        uses: lowlighter/metrics@latest
        with:
          filename: calendar.plugin.isocalendar.fullyear.svg
          token: ${{ secrets.METRICS_TOKEN }}
          base: ""
          plugin_isocalendar: yes
          plugin_isocalendar_duration: full-year
       
 ```

### Lenguajes 👅
<img src="https://github.com/user-attachments/assets/19b8cd32-03d7-4a10-89f8-e62f43307956" alt="calendar full year" width="320">

```yaml
      # Generate Lenguage activity
      - name: Generate half-year calendar
        uses: lowlighter/metrics@latest
        with:
          filename: leguages.plugin.svg
          token: ${{ secrets.METRICS_TOKEN }}
          base: ""
          plugin_languages: yes
          plugin_languages_analysis_timeout: 15
          plugin_languages_sections: recently-used, most-used
          plugin_languages_colors: github
          plugin_languages_limit: 8
```
### Contribuciones ➕
<img src="https://github.com/user-attachments/assets/b5aed1b0-25b4-46e0-8ecc-faa7eff5c4be" alt="calendar full year" width="320">


```yaml
      # Generate contribution activity
      - name: Generate Contributions
        uses: lowlighter/metrics@latest
          with:
            filename: contribution.plugin.contributors.categories.svg
            token: ${{ secrets.METRICS_TOKEN }}
            base: ""
            template: repository
            repo: metrics
            plugin_contributors_sections: categories
            plugin_contributors: yes
            plugin_contributors_categories: |
              {
                "📚 Documentation": ["README.md", "docs/**"],
                "💻 Code": ["source/**", "src/**"],
                "#️⃣ Others": ["*"]
              }
```
Si quieres cacharrear más 
https://github.com/lowlighter/metrics?tab=readme-ov-file

y acá esta el workflow con los plugins ya
https://github.com/superpollo2/workshp-github/blob/main/.github/workflows/commits.yml
Para insertar las imagenes creadas usa, recuerda cambiar la etiqueta
y el nombre del svg
```
![Languages Classic](images/languages.classic.svg)
```
![Languages Classic](lenguages.classic.svg)

> [!TIP]
> También puedes poder uno al lado del otro para optimizar espacio o como tu
> quieras que se vea o como quieras que te queden usando etiquetas html
> y todos los recursos que ofrece markdown
https://www.markdownguide.org/getting-started/


## Otros recursos

### Pinned repos
```
[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=superpollo2&repo=administrator-console)](https://github.com/superpollo2/administrator-console)
```
|                                      |                                      |
|--------------------------------------|--------------------------------------|
|[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=Integradorl-UdeA&repo=frontend_administrator-console)](https://github.com/Integradorl-UdeA/frontend_administrator-console)        | [![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=superpollo2&repo=hoja_de_vida)](https://github.com/superpollo2/hoja_de_vida) |
| [![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=superpollo2&repo=AutomataFinitoDeterministicoPractica)](https://github.com/superpollo2/AutomataFinitoDeterministicoPractica) | [![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=superpollo2&repo=weatherApp)](https://github.com/superpollo2/weatherApp) |
| [![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=superpollo2&repo=workshp-github)](https://github.com/superpollo2/workshp-github) | [![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=Integradorl-UdeA&repo=backend_administrator-console)](https://github.com/Integradorl-UdeA/backend_administrator-console)                                  |


### Iconos tecnologías o saberes
https://github.com/tandpfun/skill-icons 
```
[![My Skills](https://skillicons.dev/icons?i=java,kotlin,nodejs,figma&theme=light)](https://skillicons.dev)
```

[![My Skills](https://skillicons.dev/icons?i=java,kotlin,nodejs,figma&theme=light)](https://skillicons.dev)

```
[![My Skills](https://skillicons.dev/icons?i=js,html,css,wasm)](https://skillicons.dev)
```
[![My Skills](https://skillicons.dev/icons?i=js,html,css,wasm)](https://skillicons.dev)

### Badges
https://github.com/VishwaGauravIn/pretty-readme-badges
```
![Pug](https://img.shields.io/badge/Pug-FFF?logo=pug&logoColor=A86454)
```
![Pug](https://img.shields.io/badge/Pug-FFF?logo=pug&logoColor=A86454)
![Canva](https://img.shields.io/badge/Canva-%2300C4CC.svg?logo=Canva&logoColor=white)
![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?logo=jupyter&logoColor=white)
![Git](https://img.shields.io/badge/git-%23F05033.svg?logo=git&logoColor=white)

https://github.com/Naereen/badges
```
[![NuGet latest version](https://badgen.net/nuget/v/newtonsoft.json/latest)](https://nuget.org/packages/newtonsoft.json)
```
[![PR welcome issues still open](https://badgen.net/https/pr-welcome-badge.vercel.app/api/badge/fastify/help)](https://github.com/sinchang/pr-welcome-badge)
[![NuGet latest version](https://badgen.net/nuget/v/newtonsoft.json/latest)](https://nuget.org/packages/newtonsoft.json)
[![GitHub commits](https://badgen.net/github/commits/Naereen/Strapdown.js)](https://GitHub.com/Naereen/StrapDown.js/commit/)
[![NuGet stable version](https://badgen.net/nuget/v/newtonsoft.json)](https://nuget.org/packages/newtonsoft.json)

[![GitHub followers](https://img.shields.io/github/followers/Naereen.svg?style=social&label=Follow&maxAge=2592000)](https://github.com/Naereen?tab=followers)
[![GitHub watchers](https://img.shields.io/github/watchers/Naereen/StrapDown.js.svg?style=social&label=Watch&maxAge=2592000)](https://GitHub.com/Naereen/StrapDown.js/watchers/)

https://github.com/alexandresanlim/Badges4-README.md-Profile

> [!NOTE]
> Puedes crear tus propios badges
https://shields.io/badges


### Emojis
```
:name
```
🏆 📰 🌸 📆 ♐ 🧠 ♟️ 🪙 🥠 💉 💩 📸 🦑 💹 💬 🎟️ 🎫 💡 🙋 📅 🈷️ 🗳️ 👨‍💻 🎼 🎩 ⏱️ 🧑‍🤝‍🧑 ✒️ 🗂️ 🎭 📓 🗼 🌇 💕 💝 🗨️ ✨ 💫 🌟 🕹️ 💭 📌 🧮 🐤 ⏰
https://gist.github.com/rxaviers/7360908


### Como ñapa si quieren usar esta animación 
te dejo el workflow que lo crea (esta en este repo) 
https://github.com/superpollo2/workshp-github/blob/main/.github/workflows/snake.yml
```
![Languages Classic](dist/github-contribution-grid-snake.svg)
```
![Languages Classic](dist/github-contribution-grid-snake.svg)
