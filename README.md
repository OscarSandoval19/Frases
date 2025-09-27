El objetivo de esta aplicación es simple pero efectivo:
1.Mostrar Frases Inspiradoras: La aplicación presenta al usuario frases motivacionales.
2.Interacción con el Usuario: Cuenta con un botón que, al ser presionado, busca y muestra una nueva frase.
3.Fuente de Frases (API): Utiliza la API pública de "Zen Quotes" (https://zenquotes.io/api/random) para obtener estas frases de forma dinámica a través de internet.

Componentes Clave del Proyecto:
•MainActivity.java (Lógica de la Aplicación):•Es el cerebro de la aplicación.
•Se encarga de inicializar los elementos de la interfaz de usuario (el TextView para la frase y el Button).
•Define la acción que se ejecuta cuando el usuario presiona el botón.
•Contiene la lógica para realizar la petición a la API de Zen Quotes, procesar la respuesta y actualizar la interfaz.
•activity_main.xml (Interfaz de Usuario):
•Es un archivo XML que define la apariencia visual de la pantalla principal.
•Contiene un TextView (con el ID quote_textview) para mostrar la frase motivacional y el autor.•Incluye un Button (con el ID new_quote_button) que el usuario presiona para obtener una nueva frase.
•Utiliza un ConstraintLayout para organizar estos elementos en la pantalla.
•AndroidManifest.xml (Configuración de la Aplicación):•Es el archivo de manifiesto de la aplicación.
•Declara los componentes esenciales de la app, como la MainActivity.
•Fundamentalmente, aquí es donde se solicitó el permiso android.permission.INTERNET. Este permiso es crucial para que la aplicación pueda realizar peticiones de red y comunicarse con la API de Zen Quotes.Herramientas y Técnicas Utilizadas:1.Llamada a API Externa (Zen Quotes):

•Se utilizó la URL https://zenquotes.io/api/random para obtener una frase aleatoria en formato JSON.2.Conexión de Red (HttpURLConnection):
•Para comunicarnos con la API a través de internet, se usó la clase HttpURLConnection de Java. Esta clase permite establecer una conexión HTTP, enviar una petición (en este caso, un GET) y recibir la respuesta del servidor.3.Manejo de Tareas en Segundo Plano (AsyncTask):
•Las operaciones de red (como llamar a una API) pueden tomar tiempo y no deben realizarse en el hilo principal de la interfaz de usuario (UI thread) porque podrían bloquear la aplicación, haciéndola parecer congelada.
•Se utilizó AsyncTask para realizar la petición de red en un hilo separado (en el método doInBackground).
•Una vez que se obtiene la respuesta y se procesa, el resultado se pasa de nuevo al hilo principal (en el método onPostExecute) para actualizar de forma segura el TextView con la nueva frase.4.Análisis de JSON (org.json.JSONArray y org.json.JSONObject):
•La API de Zen Quotes devuelve la información en formato JSON (JavaScript Object Notation).
•Se usaron las clases JSONArray y JSONObject del SDK de Android para "leer" esta respuesta JSON y extraer los datos específicos que necesitábamos: la frase (identificada por la clave "q") y el autor (clave "a").5.Elementos de Interfaz de Usuario (UI):
•TextView: Para mostrar texto en la pantalla (la frase y el autor).
•Button: Para permitir al usuario interactuar y solicitar una nueva frase.
•Estos se definieron en el archivo XML de layout y se referenciaron en el código Java usando findViewById(R.id.your_element_id).6.Manejo de Eventos (OnClickListener):
•Se implementó un OnClickListener para el botón. Esto permite que la aplicación "escuche" los clics en el botón y ejecute un bloque de código específico (en este caso, iniciar la AsyncTask para buscar una nueva frase) cuando ocurre un clic.7.Permisos de Android:
•Se añadió el permiso android.permission.INTERNET al AndroidManifest.xml. Sin este permiso, el sistema operativo Android impediría que la aplicación acceda a internet por razones de seguridad.
