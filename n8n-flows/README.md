# Flujos de n8n (para importar a TU propio n8n)

Acá están los **workflows de ejemplo** listos para que los lleves a **tu propia cuenta de n8n** y los adoptes. Son plantillas limpias (sin secretos): solo rellenás tus datos y los activás.

> ¿Qué es n8n? Una herramienta (gratis, se puede auto-hospedar) para **automatizar tareas**: "cuando pase X, hacé Y". Es el motor de lo que corre **solo/recurrente**. Si no tenés n8n todavía, se puede instalar gratis — pedí ayuda al equipo.

## 🔵 Flujos de LinkedIn (el foco de la clase)

Estos tres son los que automatizan tu LinkedIn de punta a punta: redactan, publican y aprenden de las métricas. Importalos a **tu** n8n y conectá tus credenciales.

| Archivo | Qué hace | Qué necesitás llenar |
|---|---|---|
| `marca-personal-linkedin.json` | **Marca personal.** Mira tu historial de posts + directrices, genera una publicación nueva en tu voz para tu **perfil** y la deja lista/publicada. | `PEGA_AQUI_TU_TOKEN_LINKEDIN`, `TU_SHEET_ID` (historial), y tus credenciales de IA. |
| `eb-linkedin-metrics-read.json` | **Lectura de métricas (recon).** Lee el rendimiento de tus publicaciones de LinkedIn para alimentar a los otros flujos (qué funcionó). **Solo lectura.** | `PEGA_AQUI_TU_TOKEN_LINKEDIN`, `TU_ORG_ID`. |

> Cada una conecta **su propio** LinkedIn y su propia cuenta de IA: los flujos son la receta, los datos son tuyos. El token de LinkedIn se saca de tu app de LinkedIn Developers; si no sabés cómo, pedile ayuda a Claude con el Skill.

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
