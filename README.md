# whatsapp-bot-for-tickets
Project meant only for this API: https://github.com/briankalid/Ticket-service/tree/dev
This tool did most of the work: https://bot-whatsapp.netlify.app/
----

Como ya se mencionó, este bot de whatsapp parte de la plantilla creada por netlify: https://bot-whatsapp.netlify.app/ . Que posteriormente se modificó para cumplir las necesidades del proyecto.

Antes de adentrarnos en la instalación, necesitarás instalar previamente las herramientas: nginx, uvicorn y chrome ó chromium (El bot está pensado unicamente para estos navegadores). Además de un entendimiento básico de JS y haber instalado npm y docker entre otras herramientas particulares para la API. Tambien es esperable que se necesite instalar eslint mediante npm

·Se sabe que este proyecto funciona en Ubuntu 24.04.3 LTS.

# Cómo usar
----------
Primero que nada, es necesario instalar exitosamente la API y base de datos de el siguiente proyecto, siguiendo el proceso de instalación: https://github.com/briankalid/Ticket-service/tree/dev

Es caso de haber ejecutado la API por primera vez satisfactoriamente, estos son los pasos que se deberán seguir que se quiera inicializar el bot;

Primero, estando en la carpeta del repositorio(/Ticket-service-dev/src/), crea un contenedor con el siguiente comando: ```sudo docker run -d --name my-postgresdb-container1 -p 5433:5432 my-postgres-db```, tal como se muestra en la documentación de https://github.com/briankalid/Ticket-service/tree/dev.

Posteriormente, en la misma carpeta, activa el enviroment de python, si no lo has creado, busca requirements.txt y ejecuta ```python -m venv venv
source venv/bin/activate pip install requirements.txt```. En caso de ya haberlo creado, utiliza: ```source [nombre del enviroment]/bin/activate```

Finalmente, estando en la carpeta src, ejecuta ```uvicorn main:app --reload``` para encender el sistema de tickets.

Si al introducir http://127.0.0.1:8000/docs#/ en tu navegador ves una UI similar a esta:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/09b36a9a-4584-4845-a207-137634453a4b" />
felicidades, seguiste los pasos correctamente.

# Ahora con la parte del bot

Ve a la carpeta donde quieres crear tu bot y ejecuta ```npm create bot-whatsapp@latest```

Ahora responde las siguientes preguntas de esta manera


┌  Vamos a crear un  Chatbot  ✨

│

◇  ¿Quieres continuar?

│  Yes

│

◇  ¿Cuál proveedor de whatsapp quieres utilizar?

│  Bialeys

│ 

◇  ¿Cuál base de datos quieres utilizar?

│  Memory

└

finalmente, descarga el archivo app.js de este repositorio y reemplazalo por el que está en el bot en la carpeta /base-baileys-memory/ con el mismo nombre, ahora ejecuta las lineas ```sudo systemctl start nginx && npm start``` e inicia sesión con el QR de whatsapp de tu celular. Ahora, mientras tanto app.js como la API se estén ejecutando en la consola, si un contacto de Wnatsapp the envía "hola" o alguna variante, el bot contestará y se conectará a la API. Es vital que ambos procesos se estén ejecutando en pestañas/ventanas de la terminal independientemente.

Si hiciste todo correctamente, la misma consola te notificará si está conectado el bot a la API!
