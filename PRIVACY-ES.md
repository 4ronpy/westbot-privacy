# Política de Privacidad — WestBot

**Última actualización:** 26 de septiembre de 2026

Esta política explica qué datos recopila WestBot, por qué los recopila y qué hace con ellos. WestBot es un bot de Discord. No está operado por Discord, Inc., y su uso se rige por los Términos del Servicio y la Política de Privacidad de Discord, así como por la Política de Desarrolladores de Discord.

## Resumen

WestBot es un bot de utilidad comunitaria para servidores de Discord. Almacena datos solo cuando un servidor configura explícitamente una función, y solo mientras esa función esté en uso. No vende, alquila, ni comercializa ni comparte tus datos con nadie. No crea perfiles publicitarios y no usa tus datos para la toma de decisiones automatizada ni para entrenar IA.

## Quién opera WestBot

WestBot es operado por sus mantenedores individuales. Contacto: **zFons** o **YvngxSanty** (usuarios de Discord). Para cualquier solicitud relacionada con privacidad, abre un ticket en el servidor de soporte del bot o contacta directamente a un mantenedor por Discord.

## Datos que almacenamos

WestBot funciona sobre una base de datos de aplicación (alojada en el servicio PostgreSQL de Heroku). No hace scraping de Discord, y no lee el contenido de los mensajes salvo lo descrito en la sección "Contenido de los mensajes".

### 1. Configuración del servidor

Cada servidor de Discord que usa WestBot almacena su propia configuración: ID del servidor, IDs de canales de registro/moderación/tickets/sugerencias configurados, IDs de roles de moderación configurados, interruptores de funciones y umbrales de infracciones. Esto identifica al servidor, no a sus miembros.

### 2. Registros de moderación

Cuando se toma una acción de moderación a través de WestBot, almacenamos un registro de caso: ID del servidor, tipo de acción, el usuario sobre el que se actuó (ID de usuario de Discord), el moderador que la ejecutó (ID de usuario de Discord) y el texto del motivo que proporcionó el moderador. Las apelaciones presentadas contra esos casos almacenan el ID del usuario que apela, el texto de la apelación y el moderador revisor.

Estos registros se conservan por responsabilidad del servidor y son visibles para el personal de moderación de ese servidor. Los datos de un servidor dado pueden borrarse a petición del dueño del servidor o de un moderador.

### 3. Registro de actividad del staff

WestBot mantiene un registro de auditoría de las acciones del staff para que los dueños de servidor puedan revisar la conducta de los moderadores. Registra: el ID de usuario de Discord y el nombre visible del miembro del staff, la acción realizada, el usuario objetivo, el texto del motivo, el canal y una marca de tiempo.

Este registro es el motivo por el que WestBot solicita el **Intent de Miembros del Servidor** y el **Intent de Contenido de Mensajes** (ver más abajo), y es accesible únicamente para el staff configurado de ese servidor.

### 4. Datos de preferencias y funciones sociales

Las funciones comunitarias opcionales almacenan estado por usuario, como: estado AFK y su marca de tiempo (se borra en cuanto envías un mensaje), registros de relaciones/"matrimonio" opcionales, estadísticas de interacción (por ejemplo, contadores de abrazos/besos), entradas de usuarios bloqueados y apuestas de partidos de fútbol. Cada uno de estos es opcional y está vinculado a tu ID de usuario de Discord. Se almacena localmente en la base de datos del bot y no se transmite a ningún otro sitio.

### 5. Tokens de autorización de Spotify

Si usas la integración de Spotify, la autorizas mediante el propio flujo OAuth de Spotify. Para reproducir una pista en tu nombre, WestBot debe almacenar tu token de acceso y tu token de actualización de Spotify, junto con los permisos concedidos y la hora de vencimiento, asociados a tu ID de usuario de Discord.

Estos tokens se usan **únicamente** para llamar a la Web API de Spotify en tu nombre y controlar tu propia reproducción. Nunca son leídos por una persona, nunca se muestran públicamente, nunca se venden y nunca se comparten con terceros. Si revocas el acceso en la configuración de tu cuenta de Spotify, los tokens simplemente caducan y dejan de ser utilizables. También puedes pedir a los mantenedores que eliminen tus tokens almacenados.

### 6. Datos efímeros y técnicos

Los datos operativos de corta duración, como el estado de los límites de tasa, los tiempos de espera y el contenido de un asistente de configuración sin confirmar (el token de confirmación de Discord), se mantienen solo en memoria mientras el bot está en ejecución. No se escriben en la base de datos.

Las copias de seguridad de la base de datos las conserva nuestro proveedor de alojamiento durante un periodo limitado y luego se eliminan.

## Contenido de los mensajes

WestBot solicita el **Intent de Contenido de Mensajes** únicamente para dos fines concretos:

1. **Comandos con prefijo.** Todos los comandos de WestBot son comandos *híbridos* de Discord, lo que significa que cada comando se registra tanto como comando slash como como comando con prefijo (texto), como `w.help`. La forma con prefijo solo funciona si el bot puede leer el texto del mensaje. Sin este intent, todos los comandos de WestBot perderían su forma con prefijo.
2. **Auditoría de la actividad del staff.** En el canal de moderación configurado de un servidor, cuando un miembro del staff ejecuta un comando de moderación que es gestionado por un bot de moderación *distinto y de terceros*, WestBot lee ese mensaje para registrar quién ejecutó qué acción de moderación, contra quién y con qué motivo, en el registro unificado de actividad del staff descrito arriba. Analiza únicamente el propio comando de moderación y su motivo. No conserva el texto completo del mensaje.

WestBot **no** lee, almacena ni analiza el contenido de conversaciones ordinarias, no crea perfiles a partir del contenido de los mensajes y no usa el contenido de los mensajes para ningún fin distinto de estas dos funciones. Las funciones que no necesitan el texto de un mensaje (por ejemplo, el sistema AFK y el gestor de recordatorios con imagen adjunta) están escritas deliberadamente para funcionar sin este intent.

## Datos de miembros

WestBot solicita el **Intent de Miembros del Servidor** con un único propósito: recibir el evento de baneo para que el canal de registro de un servidor pueda anotar quién fue baneado, cuándo y con qué motivo. Discord entrega este evento únicamente a las aplicaciones que tengan ese intent.

WestBot **no** usa este intent para enviar notificaciones de entrada o salida, ni para enumerar o almacenar una lista de miembros, ni para ninguna forma de perfilado. Los datos de miembros recibidos en un evento de baneo se usan únicamente para generar esa entrada de registro y no se almacenan por separado. Cuando WestBot necesita buscar a un usuario por nombre, utiliza el endpoint de búsqueda propio de Discord que no está restringido, y lee el resultado solo para mostrarlo en el mensaje resultante. Cuando necesita un total de miembros, usa el recuento incluido en los datos del servidor.

WestBot **no** solicita el **Intent de Presencia**. Nunca lee el estado en línea, el estado personalizado ni la actividad de juego de los usuarios.

## Permisos que solicita el bot

Además de los dos intents privilegiados anteriores, WestBot solicita únicamente los permisos estándar de Discord que necesita para sus funciones: Gestionar Mensajes, Gestionar Roles (solo para aplicar los roles de castigo configurados), Banear Miembros, Expulsar Miembros, Moderar Miembros, Leer Historial de Mensajes, Enviar Mensajes, Insertar Embeds, Adjuntar Archivos y Añadir Reacciones. El dueño del servidor puede configurar los niveles de permiso por servidor.

## Terceros

Los únicos flujos de datos hacia terceros de WestBot son:

- **Discord** — la propia plataforma, regida por su política de privacidad.
- **Spotify** — solo para usuarios que autorizan explícitamente la integración de Spotify, regida por la política de privacidad de Spotify.
- **Tenor** — búsqueda de imágenes/GIF, utilizada para convertir en una URL multimedia un término de búsqueda solicitado por el usuario. Los términos de búsqueda solo se envían a Tenor cuando un usuario invoca un comando de GIF.
- **Heroku** — alojamiento de la aplicación y base de datos PostgreSQL, regido por la política de privacidad de Heroku.

WestBot no envía datos de usuario a ningún servicio de analítica, publicidad o rastreo.

## Conservación y eliminación de datos

- Los datos de moderación y de actividad del staff de cada servidor se conservan mientras el servidor use la función correspondiente, y pueden borrarse a petición del dueño del servidor o de un moderador.
- El estado AFK se elimina automáticamente cuando envías tu siguiente mensaje.
- Los datos sociales y de preferencias persisten hasta que tú o un moderador del servidor los elimines mediante el comando correspondiente, o hasta que solicites su eliminación.
- A petición de un usuario, eliminaremos los datos asociados a su ID de usuario de Discord. A petición del dueño de un servidor, eliminaremos la configuración y los registros de ese servidor.
- Los datos se eliminan de la base de datos activa en un plazo razonable tras una solicitud verificada. Pueden quedar copias residuales en las copias de seguridad durante un periodo adicional breve antes de ser rotadas.

### Periodos de conservación

No todos los datos son de corta duración. Se aplican los siguientes periodos:

| Dato | Conservación |
| --- | --- |
| Estado AFK | Hasta que envías tu siguiente mensaje; entonces se elimina de inmediato |
| Advertencias previas a baneo | 5 días; luego expiran automáticamente |
| Registro de actividad del moderador (comando, usuario objetivo, texto del motivo tomado de un mensaje) | Se conserva mientras el servidor use la función de staff, ya que existe para que los dueños de servidor revisen la conducta de los moderadores |
| Casos de moderación y apelaciones | Se conservan mientras el servidor use la función de moderación, ya que son el registro de responsabilidad del servidor |
| Metadatos de tickets (recuentos, participantes, marcas de tiempo) | Se conservan mientras el servidor use la función de tickets; no se almacena texto de mensajes |
| Estado social opcional (relaciones, contadores de interacción) | Hasta que tú o un moderador del servidor lo elimine |
| Tokens de Spotify | Hasta que revoques el acceso en Spotify o solicites la eliminación |
| Configuración del servidor | Hasta que el dueño del servidor elimine la función o el bot |

El texto derivado del contenido de los mensajes se conserva únicamente en el registro de actividad del staff descrito arriba, accesible solo para los administradores de ese servidor, y que estos o el dueño del servidor pueden borrar en cualquier momento.

Los casos de moderación y las apelaciones se conservan intencionadamente más de 30 días porque su propósito es la responsabilidad del servidor: una ventana de conservación corta impediría revisar la conducta del staff. Estos registros son accesibles únicamente para los administradores de ese servidor, y un dueño o moderador puede borrarlos en cualquier momento.

## Seguridad

Los tokens de Discord y las credenciales de la base de datos se almacenan únicamente como variables de entorno en la plataforma de alojamiento y nunca se suben al repositorio de código fuente. La aplicación se sirve por HTTPS, y las conexiones a la base de datos requieren TLS (`sslmode=require`). La base de datos está alojada en Heroku Postgres, que cifra todos los datos en reposo con cifrado de almacenamiento a nivel de bloque AES-256 en todos los niveles de plan, y almacena también cifradas las copias de seguridad físicas. El acceso a los datos de producción está limitado a los mantenedores del bot.

## Niños

WestBot no está dirigido a menores de 13 años ni está pensado para su uso por ellos. Los servidores que no estén destinados principalmente a una audiencia adulta no deberían invitar al bot.

## Cambios en esta política

Si esta política cambia de forma sustancial, la versión actualizada se publicará en la misma URL pública, y la fecha de "Última actualización" de la cabecera se modificará. El uso continuado de WestBot tras un cambio constituye la aceptación de la política actualizada.

## Código fuente

WestBot es un proyecto de **código cerrado**. Su código fuente no se publica ni se distribuye a terceros. Este documento es la única página pública del proyecto.

## Documentos relacionados

- [Terms of Service](TERMS.md) / [Términos del Servicio](TERMS-ES.md)
