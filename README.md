# Telegram-to-Gemini AI Bot con n8n & Docker

Este proyecto consiste en un chatbot inteligente para Telegram impulsado por el modelo **Google Gemini AI**, orquestado de manera visual e integrada a través de **n8n** corriendo en un contenedor de **Docker**. Este proyecto lo hice para complementar mis estudios en la carrera de TUDAI en la UNICEN. 
El chatbot está orientado dar soporte a los estudiantes de la carrera, con gemini flash los usuarios obtienen respuestas rápidas y concisas ante cualquier duda.

Agente IA y Soporte para Proyectos de Software:
Un agente inteligente integrado a un bot de Telegram orientado al ciclo de vida del desarrollo.

## 🚀 Tecnologías Utilizadas

* **n8n:** Motor de automatización y orquestación de workflows.
* **Google Gemini API:** IA generativa para procesar y responder consultas.
* **Telegram Bot API:** Plataforma de mensajería para la interfaz de usuario.
* **Docker:** Contenerización de la instancia de n8n para un despliegue ágil.
* **ngrok:** Túnel seguro HTTPS para el consumo de webhooks en entorno local.

## Arquitectura del Flujo

1. **Telegram Trigger:** Escucha eventos de mensajes entrantes mediante un Webhook en tiempo real.
2. **AI Agent (Gemini Chat Model):** Recibe el prompt del usuario y genera una respuesta contextualizada mediante la API de Gemini.
3. **Send Text Message (Telegram):** Envía la respuesta procesada de vuelta al chat del usuario.

----

## Cómo Replicar este Proyecto para ver su funcionamiento:

### 1. Requisitos Previos
* Docker y Docker Desktop instalados.
* ngrok instalado y configurado.
* Una API Key de Google Gemini obtenida en Google AI Studio.
* Un Bot de Telegram creado vía [@BotFather](https://t.me/BotFather).

### 2. Despliegue de n8n con Docker
Ejecutar el contenedor de n8n pasando la URL de tu túnel ngrok:

\`\`\`bash
docker run -it --rm --name n8n \
  -p 5678:5678 \
  -e WEBHOOK_URL=https://TU-SUBDOMINIO.ngrok-free.dev/ \
  -e N8N_SECURE_COOKIE=false \
  -v n8n_data:/home/node/.n8n \
  docker.n8n.io/n8nio/n8n
\`\`\`

### 3. Importar el Workflow
1. Abrir n8n en `http://localhost:5678`.
2. Crear un nuevo flujo y seleccionar **Import from File**.
3. Seleccionar el archivo `telegram-gemini-bot.json` incluido en este repositorio.
4. Configurar las credenciales para la **Telegram API** y **Google Gemini API**.
5. Activar el flujo (**Active**).

---
*Desarrollado como proyecto de automatización e integración de Inteligencia Generativa.*
