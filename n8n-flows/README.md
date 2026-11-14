# Flujos de n8n (para importar a TU propio n8n)

Acá están los **workflows de ejemplo** listos para que los lleves a **tu propia cuenta de n8n** y los adoptes. Son plantillas limpias (sin secretos): solo rellenás tus datos y los activás.

> ¿Qué es n8n? Una herramienta (gratis, se puede auto-hospedar) para **automatizar tareas**: "cuando pase X, hacé Y". Es el motor de lo que corre **solo/recurrente**. Si no tenés n8n todavía, se puede instalar gratis — pedí ayuda al equipo.

## 🔵 Flujos de LinkedIn (el foco de la clase)

Estos dos automatizan tu LinkedIn de punta a punta: redactan, publican y aprenden de las métricas. Importalos a **tu** n8n y conectá tus credenciales.

| Archivo | Qué hace | Qué necesitás llenar |
|---|---|---|
| `marca-personal-linkedin.json` | **Marca personal.** Mira tu historial de posts + directrices, genera una publicación en tu voz para tu **perfil** y la deja lista/publicada; recibís y aprobás desde Telegram. | Tu **perfil** (`[tu profesión y especialidad]`, `[tu ciudad/país]`), tu `TU_TELEGRAM_CHAT_ID`, y las **credenciales**: LinkedIn, IA (Gemini/Anthropic) y Telegram. |
| `eb-linkedin-metrics-read.json` | **Lectura de métricas (recon).** Lee el rendimiento de tus publicaciones de LinkedIn para alimentar al flujo de contenido (qué funcionó). **Solo lectura.** | `PEGA_AQUI_TU_TOKEN_LINKEDIN`. |

> Cada una conecta **su propio** LinkedIn, su propia IA y su propio Telegram: los flujos son la receta, los datos son tuyos. ¿No sabés sacar un dato (token, chat de Telegram)? Pegale a tu Claude el prompt de abajo y te guía.

### 🤖 Que Claude te ayude a llenar los datos

Después de importar el flujo, pegale esto a tu Claude (con el connector de n8n conectado) y te va pidiendo tus datos de a uno y los deja puestos:

```
Claude, ya importé el flujo "Marca Personal LinkedIn (plantilla)" en mi n8n.
Ayudame a completarlo con MIS datos, de a un paso a la vez y con palabras
simples. Pedime cada cosa, yo te la paso, y vos la dejás puesta en el nodo
que corresponde. Lo que hay que llenar:

1) MI PERFIL (va en los prompts de IA): mi profesión y especialidad, mis años
   de experiencia y 1-2 logros, mi ciudad/país. Preguntámelo y reemplazá los
   [tu profesión y especialidad] y [tu ciudad/país].
2) MI TELEGRAM: ayudame a conseguir mi "chat id" (decime cómo, con el bot
   @userinfobot) y reemplazá TU_TELEGRAM_CHAT_ID en todos los nodos.
3) MIS CREDENCIALES en n8n: LinkedIn, un modelo de IA (Google Gemini o
   Anthropic) y Telegram. Decime cómo conectar cada una con el botón de
   credenciales de n8n.
Al final, NO lo actives: mostrámelo para que yo lo revise y confirme.
```

> El flujo de métricas solo pide `PEGA_AQUI_TU_TOKEN_LINKEDIN` (token de tu app de LinkedIn Developers). Mismo truco: pedile a Claude que te guíe a sacarlo y lo deje puesto.

## Flujos de ejemplo (genéricos)

| Archivo | Qué hace | Qué necesitás llenar |
|---|---|---|
| `whatsapp-bot-ia.json` | **WhatsApp responde solo con IA.** Llega un mensaje a tu WhatsApp Business → una IA responde según tu negocio. | `PEGA_AQUI_TU_TOKEN` (WhatsApp), `PEGA_AQUI_TU_PHONE_ID`, `PEGA_AQUI_TU_OPENAI_KEY`, y el texto de "quién es tu negocio". |
| `lead-nuevo-sheets-correo.json` | **Lead nuevo → Google Sheets + correo de bienvenida.** Entra un lead (formulario/webhook) → se guarda en tu hoja → se le manda un correo de bienvenida. | Tu conexión de **Google Sheets** y de **correo** (en los nodos que lo piden). |
| `reporte-ventas-semanal.json` | **Reporte de ventas semanal automático.** Cada lunes 8am → lee tus ventas → calcula totales → te manda el reporte por correo. | Tu conexión de **Google Sheets/datos** y de **correo**. |

## Cómo importarlo a tu n8n (paso a paso, sin tecnicismos)

1. Descargá el archivo `.json` del flujo que quieras (botón **Code → Download ZIP** del repo, o clic en el archivo → **Download raw**).
2. Entrá a **tu n8n** → arriba a la derecha, menú **⋯ → Import from File** (Importar desde archivo).
3. Elegí el `.json`. El flujo aparece en tu lienzo.
4. Abrí el nodo **"Configuración"** (o los que estén marcados) y **reemplazá los `PEGA_AQUI_TU_...`** por tus datos reales.
5. Donde pida **credenciales** (Google, correo, WhatsApp), conectá las tuyas con el botón de credenciales de n8n.
6. Tocá **Save** y después el interruptor **Active** (arriba a la derecha) para encenderlo.
7. ¡Listo! El flujo ya corre en **tu** cuenta.

> Cada flujo trae una nota **"Léeme"** adentro con la explicación. Abrila primero.

## Seguridad

- Estas plantillas **no traen claves ni tokens reales** — vos ponés los tuyos.
- Tus secretos viven **en tu n8n**, nunca en este repo.
- Si querés que Claude pueda **disparar** uno de estos flujos desde tu app (sin que entres a n8n), se puede exponer con el **MCP Server Trigger** de n8n y agregarlo como connector. Ver `../mcp/README.md`.
