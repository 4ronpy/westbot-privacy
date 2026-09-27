<div align="center">

# 📜 WestBot — Documentos Legales

<img src="https://img.shields.io/badge/documentos-Español%20%7C%20English-5865F2?style=for-the-badge" alt="Idiomas">

**Política de Privacidad y Términos del Servicio de WestBot, el bot de Discord.**

[ 🇬🇧 English ](README.md) · [ 🇪🇸 Español ](README-ES.md)

</div>

---

## 📄 Documentos

| | Español | English |
| --- | --- | --- |
| **Política de Privacidad** | [PRIVACY-ES.md](PRIVACY-ES.md) | [PRIVACY.md](PRIVACY.md) |
| **Términos del Servicio** | [TERMS-ES.md](TERMS-ES.md) | [TERMS.md](TERMS.md) |

> Estos son los enlaces que se pegan en el **Portal de Desarrolladores de Discord**, en
> `Configuración → Información General`.

---

## 🔗 URLs para el Portal de Desarrolladores

Pega esto en el [Portal de Desarrolladores de Discord](https://discord.com/developers/applications):

| Campo del portal | Valor |
| --- | --- |
| **URL de la Política de Privacidad** | `https://github.com/4ronpy/westbot-privacy/blob/main/PRIVACY.md` |
| **URL de los Términos del Servicio** | `https://github.com/4ronpy/westbot-privacy/blob/main/TERMS.md` |
| URL de endpoint de interacciones | _déjalo vacío — el bot usa Gateway_ |
| URL de verificación de roles vinculados | _déjalo vacío — no se usan roles vinculados_ |

---

## 📋 Resumen

- Los datos se almacenan solo cuando un servidor habilita explícitamente una función
- No se venden, alquilan ni comparten datos de usuario con nadie
- Sin servicios de analítica, publicidad ni rastreo
- Sin uso de datos para entrenar IA ni para decisiones automatizadas
- El contenido de los mensajes se lee únicamente del personal de moderación, y solo en el canal de moderación configurado
- Todos los datos se pueden borrar a petición del usuario o del dueño del servidor

---

## 🤖 Tratamiento de datos

| Área | Detalle |
| --- | --- |
| **Almacenamiento** | PostgreSQL en Heroku, cifrado en reposo con AES-256 |
| **Intents privilegiados** | Solo `Server Members` y `Message Content` |
| **No solicitado** | `Presence Intent` — nunca se usa |
| **Retención** | Por función; el estado AFK y los prebanos son de corta duración |
| **Terceros** | Discord, Spotify, Tenor, Heroku |

---

## 📬 Contacto

- **@zFons_**
- **@YvngxSanty**

Las solicitudes de eliminación de datos se pueden hacer por mensaje directo en Discord.

---

<div align="center">

<sub>WestBot es una aplicación de terceros y no está afiliada a Discord, Inc. ni a Spotify AB.</sub>

</div>
