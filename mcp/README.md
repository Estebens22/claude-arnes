# Connectors (MCP) — herramientas para el arnés

Acá vive el código de los **servidores MCP** que le dan "manos" a Claude. Son servicios **hosteados en internet** que el usuario agrega a su Claude pegando una **URL** (Ajustes → Conectores). La conexión la hace Claude desde la nube de Anthropic, así que el servidor debe ser **alcanzable por internet** (no sirve en red privada/VPN).

## Planeados

| Connector | Qué hace | Scopes (solo lo necesario) |
|---|---|---|
| `apollo` | Buscar empresas y contactos por ICP (sector, tamaño, cargo, ciudad); enriquecer. **Solo lectura.** | búsqueda de personas/empresas |
| `n8n-trigger` | Disparar flujos de n8n aprobados (ej. cargar prospectos a una hoja/CRM, encolar correos para envío controlado). | webhook de flujos específicos, no acceso total |

## Principios (iguales a los del Skill)

- **Solo lectura por defecto**; cualquier acción que envíe correos o cargue datos pasa por aprobación humana en el chat.
- **Secretos (API keys de Apollo, tokens de n8n) nunca en el repo** → van como variables de entorno en el host.
- Credencial/alcance **por usuario** cuando aplique; no exponer datos de un comercio/persona a otra.
- Namespacing y allowlist explícita de operaciones.

## Estado

🔧 **En construcción.** El Skill `prospeccion-con-revision` ya funciona como método sin estos connectors (Claude arma lista + correos de forma conversacional y guarda en Google Sheets si está conectado). Cuando `apollo` y `n8n-trigger` estén hosteados, se agregan por URL y el mismo Skill empieza a usarlos automáticamente.
