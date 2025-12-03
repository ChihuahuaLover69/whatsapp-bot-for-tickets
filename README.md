# whatsapp-bot-for-tickets
Very first whatsapp bot ever made by myself. Little only for this API: https://github.com/briankalid/Ticket-service/tree/dev
This tool did most of the work: https://bot-whatsapp.netlify.app/

--------------------------
# ESP
-------------------------

Como ya se mencionó, este bot de whatsapp parte de la plantilla creada por netlify: https://bot-whatsapp.netlify.app/ . Que posteriormente se modificó para cumplir las necesidades del proyecto.

Antes de adentrarnos en la instalación, necesitarás instalar previamente las herramientas: nginx, uvicorn y chrome ó chromium (El bot está pensado unicamente para estos navegadores). Además de un entendimiento básico de JS y haber instalado npm y docker entre otras herramientas particulares para la API.

# Cómo usar
----------
Despúes de instalar exitosamente la API y base de datos creadas para este proyecto: https://github.com/briankalid/Ticket-service/tree/dev

Deberás ejecutar el API por lo menos una vez estando dentro de la carpeta del repositorio descargado. Primero, estando en la carpeta del repositorio, crea un contenedor con el siguiente comando: sudo docker run -d --name my-postgresdb-container12 -p 5433:5432 my-postgres-db, tal como se muestra en la documentación de https://github.com/briankalid/Ticket-service/tree/dev, posteriormente activa el enviroment de python (si no lo has creado, busca requirements.txt y ejecuta python -m venv venv
source venv/bin/activate pip install requirements.txt)

Finalmente, estando en la carpeta src, ejecuta uvicorn main:app --reload para encender el sistema de tickets

Si al introducir http://127.0.0.1:8000/docs#/ en tu navegador ves una UI, felicidades, seguiste todos los pasos correctamente.

# Ahora con la parte del bot

Ve a la carpeta donde quieres crear tu bot y ejecuta npm create bot-whatsapp@latest

Ahora responde las siguientes preguntas de esta manera


┌  Vamos a crear un  Chatbot  ✨
│
◇  ¿Quieres continuar?
│  Yes
│
◇  ¿Cuál proveedor de whatsapp quieres utilizar?
│  Whatsapp-web.js
│ 
◇  ¿Cuál base de datos quieres utilizar?
│  Memory
└

finalmente, descarga el archivo app.js de este repositorio y reemplazalo por el que está en el bot, ahora ejecuta las lineas sudo systemctl start nginx && npm start y inicia seción con el QR de whatsapp de
tu celular (provisionalmente).

Si hiciste todo correctamente, la misma consola te notificará si está conectado el bot a la API!


---
# ENG (outdated)
----

Hopefully this whatsapp bot will make it easier to create a ticket for my university ticket system.

# How to use

To run locally:

After succesfully installed this API https://github.com/briankalid/Ticket-service/tree/dev
create a Docker, so you can use the API, here is an example of how I do it: "sudo docker run -d --name my-postgresdb-container12 -p 5433:5432 my-postgres-db", if ran succesfully, then create a python
enviroment and turn it on, the one in the file "ticket-file/Ticket-service-dev/src" named botw-enviroment might work but I am not sure, You are free to try, using "source botw-enviroment" might do something
While on that same file, intall uvicorn and run: "uvicorn main:app --reload". You should have a working API locally hosted now.

Just install nginx and initiate using: "sudo systemctl start nginx" if you are on linux, of course.
then open the main file and run "App.js" using "npm start" and you are done :D

If something doesnt work, make sure you have chromium installed, otherwise might not work.
-------------------

# Where to find stuff
Inside App.js
You will probably have to manually change the Url you want to conect to, you can do it by modifing the App.js file, then search for the .AddAction functions and see if they have any Url in them, just change it to whatever you want.

ctx contains a lot of useful information about the message the bot reacts to.

.addKeyword allows you to create a list of string the bot will look after, if it detects one, u can say something by adding .AddAnswer(), then add the reponse, the last parameter of AddAnswer allows you to "create" a conversation flow, useful for creating tickets.

Just read the https://bot-whatsapp.netlify.app/ documentation if you plan to make it work.
