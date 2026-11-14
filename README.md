# 🦾 Claude Arnés — asistente agéntico para arrancar (sin ser técnico)

Un "arnés" para que cualquiera, con su **Claude Max** (o Pro/Ultra), pase de *chatear* a tener un **asistente que hace tareas con método y revisión** — en web, escritorio y celular, con la misma cuenta.

No hay que programar ni mantener servidores. Subís un **Skill** (un método) y, cuando estén listos, pegás **connectors** (herramientas como Apollo o n8n).

---

## 🚀 Empezá acá — copiá este mensaje y pegalo en tu Claude

Abrí Claude (web, escritorio o celular), **nuevo chat**, y pegá esto tal cual. Claude te va a guiar paso a paso:

```
Hola Claude 👋 Quiero que seas mi guía para instalar unas herramientas (un "arnés")
que me van a ayudar con mi trabajo. No soy técnica, así que llevame DE A UN PASO A LA VEZ,
con palabras simples, y esperá mi "listo" antes de pasar al siguiente. Si algo no me sale,
ayudame con paciencia.

Lo que quiero lograr: tener en vos un asistente que me ayude a CONSEGUIR CLIENTES y a
CREAR CONTENIDO PARA LINKEDIN, mostrándome siempre todo para que yo apruebe antes de
enviar o publicar nada.

Guiame así (un paso a la vez):
1) Cómo activar los "Skills" y la "ejecución de código" en mi cuenta: entrá a
   claude.ai/customize/skills y decime exactamente dónde hacer clic.
2) Voy a descargar archivos de este repositorio:
   https://github.com/Estebens22/claude-arnes
   Decime cómo bajar la carpeta de un Skill (botón verde "Code" → "Download ZIP"),
   cuál carpeta de "skills/" usar primero, y cómo SUBIRLA en esa pantalla de Skills.
3) Cuando el Skill esté subido y encendido, hacemos una PRUEBA juntas con un caso real mío.
4) Más adelante me van a pasar "enlaces de connectors" (Apollo, imágenes, video) —
   cuando los tenga, guiame para pegarlos en Ajustes → Conectores.

Arrancá por el paso 1, explicámelo simple, y esperá mi "listo".
```

> Claude te acompaña en cada paso (los clics de subir el Skill los hacés vos en la pantalla de ajustes; Claude te dice dónde). Cuando termines, ya tenés tu asistente andando.

---

## ⚡ Si ya tenés el connector de n8n conectado — bajá el flujo de LinkedIn con Claude

Si ya conectaste tu n8n a Claude (Ajustes → Conectores), no hace falta importar a mano: pegale esto a Claude y él baja el flujo del repo y lo importa a tu n8n.

**Flujo de marca personal:**
```
Claude, usá el connector de n8n que ya tengo conectado para importar
este flujo de LinkedIn a mi n8n:

https://raw.githubusercontent.com/Estebens22/claude-arnes/main/n8n-flows/marca-personal-linkedin.json

Bajá el JSON de ese link, importalo como un workflow nuevo en mi n8n, y
después decime qué datos tengo que rellenar (los PEGA_AQUI_TU_... y las
credenciales). No lo actives hasta que yo confirme.
```

**Flujo de métricas (opcional):** el mismo prompt, cambiando el link por:
```
https://raw.githubusercontent.com/Estebens22/claude-arnes/main/n8n-flows/eb-linkedin-metrics-read.json
```

> Si tu connector de n8n es **solo lectura** y no puede crear el workflow, el plan B de 10 segundos: en tu n8n → **⋯ → Import from File** y pegás el link o el archivo. Ver [`n8n-flows/README.md`](n8n-flows/README.md).

---

## ¿Qué hay acá?

| Carpeta | Qué es | Estado |
|---|---|---|
| `skills/` | **Skills** = métodos que le enseñás a tu Claude (`SKILL.md`). Se suben en `claude.ai/customize/skills`. | ✅ Listo para usar |
| `mcp/` | **Connectors (MCP)** = herramientas reales (Apollo, Taplio, n8n) que Claude usa por una URL. | 🔧 En construcción |
| `n8n-flows/` | **Flujos de n8n** listos para importar a **tu propio n8n**. Incluye los 3 de **LinkedIn** (publicación de marca, marca personal, lectura de métricas) + 3 de ejemplo. Plantillas limpias (sin secretos). | ✅ Listos para importar |
| `docs/` | Guía para no técnicos + guion de clase + cómo agregar herramientas. | ✅ |

### Skills disponibles

- **`prospeccion-con-revision`** — conseguir clientes: arma lista de prospectos + correos personalizados, con aprobación antes de enviar. (Herramienta: Apollo)
- **`contenido-linkedin-con-revision`** — crear posts/carruseles de LinkedIn en tu voz, con aprobación antes de publicar. (Herramienta: Taplio)

Este catálogo **crece**: cada herramienta que uses (Apollo, Taplio, n8n, tu CRM…) se suma como un Skill y/o un connector. Ver [`docs/como-agregar-herramientas.md`](docs/como-agregar-herramientas.md).

## Empezá por acá

1. Leé **[`docs/para-no-tecnicos.md`](docs/para-no-tecnicos.md)** → cómo subir tu primer Skill en 5 minutos.
2. Probá el Skill **`prospeccion-con-revision`**: le pedís conseguir clientes y Claude arma la lista + los correos, y **te muestra todo para aprobar antes de enviar nada**.
3. (Pronto) Conectás Apollo + n8n con un enlace y Claude ya busca contactos reales y dispara flujos.

## Las 3 capas (para entender el concepto)

- **Skill** = el *cerebro/método* (cómo hacer la tarea bien). → se sube a tu Claude.
- **Connector / MCP** = las *manos* (las herramientas: Apollo, n8n, Sheets). → se pegan por URL.
- **Este repo** = la *distribución* (de acá bajás el Skill y lo compartís).

## Compartirlo

En plan **Max**, cada persona sube el Skill a su propia cuenta (el "compartir skill con un clic" es solo Team/Enterprise). Por eso este repo es la forma de distribuirlo: le pasás el link, baja el Skill, lo sube, y listo — mismo asistente en su Claude.

---

Hecho para arrancar de a poco: **primero el método, después las herramientas, después la automatización.**
