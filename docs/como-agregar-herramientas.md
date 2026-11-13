# Cómo agregar una herramienta nueva al arnés

El arnés está hecho para **crecer**. Cada vez que el equipo empiece a usar una herramienta nueva (Apollo, Taplio, un CRM, Google Calendar, lo que sea), se suma en dos capas posibles:

## 1. ¿Agrego un Skill, un Connector, o los dos?

- **Skill (método)** → cuando querés enseñarle a Claude *cómo hacer bien una tarea* (el playbook, con su paso de revisión). No necesita hosting. Se sube a `claude.ai/customize/skills`.
- **Connector / MCP (herramienta)** → cuando Claude necesita *tocar un sistema externo* (buscar en Apollo, programar en Taplio, disparar n8n). Es un servidor hosteado que se agrega por URL.
- La mayoría de casos buenos = **Skill + Connector**: el método + las manos.

## 2. Para agregar un Skill (lo más rápido)

1. Creá una carpeta en `skills/<nombre-del-skill>/` con un archivo `SKILL.md`.
2. El `SKILL.md` empieza con este encabezado y luego las instrucciones:
   ```
   ---
   name: nombre-del-skill
   description: cuándo usar este skill (frases que lo disparan) + qué hace, con revisión humana.
   ---
   # instrucciones del método...
   ```
3. Reglas de oro para que quede bien:
   - **Nada externo sin aprobación humana** (siempre un paso de "mostrá y esperá el sí").
   - **No inventar datos** (contactos, cifras, logros). Si falta, preguntar.
   - **Calidad > cantidad.** Sonar a la persona, no a la máquina.
4. Commit + push. Cada persona lo descarga y lo sube a su Claude.

## 3. Para agregar un Connector (herramienta)

1. Mirá si la herramienta **ya tiene un MCP oficial** (muchas SaaS lo están sacando) → si sí, se agrega directo por URL, sin código.
2. Si no, dos caminos:
   - **API propia → servidor MCP** en `mcp/<herramienta>/` (hosteado en nuestra infra, alcanzable por internet).
   - **Vía n8n**: si la herramienta no tiene MCP pero sí API, se arma un workflow en n8n y se expone con el **MCP Server Trigger** (así reusamos lo que ya corre en `n8n.digiworld.com.co`).
3. Secretos (API keys/tokens) **nunca en el repo** → variables de entorno en el host.
4. Documentá en `mcp/README.md` qué hace, qué scopes (solo lo necesario) y cómo se agrega.

## 4. Conectar Skill ↔ Connector

En el `SKILL.md`, escribí: *"Si hay un connector de X conectado, usalo para [acción]; si no, hacelo de forma conversacional / entregá listo para pegar."* Así el Skill **funciona desde el día 1** (como método) y **mejora solo** cuando se enchufa la herramienta.

---

Regla de diseño del arnés: **primero el método (Skill), después las herramientas (Connectors), después la automatización (n8n/recurrencia).** Siempre con revisión humana en los pasos que tocan el mundo real.
