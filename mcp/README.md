# Connectors (MCP) — herramientas para el arnés

Acá vive el código de los **servidores MCP** que le dan "manos" a Claude. Son servicios **hosteados en internet** que el usuario agrega a su Claude pegando una **URL** (Ajustes → Conectores). La conexión la hace Claude desde la nube de Anthropic, así que el servidor debe ser **alcanzable por internet** (no sirve en red privada/VPN).

El arnés está pensado para **crecer**: cada herramienta que use el equipo se suma acá como un connector. El mismo Skill empieza a usarla apenas está conectada.

## Catálogo de connectors

| Connector | Para qué | Cómo se construye | Estado |
|---|---|---|---|
| `apollo` | Prospección: buscar empresas/contactos por ICP (sector, tamaño, cargo, ciudad) y enriquecer. **Solo lectura.** | API de Apollo → servidor MCP propio. | 🔧 En construcción |
| `taplio` | LinkedIn: programar/encolar posts, ver ideas y métricas de contenido. | Según lo que exponga la API de Taplio; si es limitada, se puentea vía **n8n** (n8n llama a Taplio). | 🔎 Por validar API |
| `n8n` | Disparar **flujos que ya tenemos** (prospección/Apollo-reactivación, LinkedIn Café→post, etc.). | **MCP Server Trigger** de n8n (v2.27.4 en `n8n.digiworld.com.co` ya lo soporta): se expone el workflow existente como herramienta, sin montar servidor aparte. | 🔧 En construcción |
| `google-sheets` | Guardar/leer listas (prospectos, calendario de contenido). | Connector de Google (nativo en Claude) o MCP propio. | ✅ Disponible nativo |

## Qué connector sirve a qué Skill

- **`prospeccion-con-revision`** → usa `apollo` (buscar) + `n8n`/`google-sheets` (cargar lo aprobado).
- **`contenido-linkedin-con-revision`** → usa `taplio` (programar) o entrega listo para pegar.

Mientras los connectors a medida no estén, **los Skills ya funcionan como método** (Claude arma listas/posts de forma conversacional y guarda en Sheets si está conectado). Al enchufar el connector, el mismo Skill empieza a usarlo automáticamente.

## Principios (iguales a los del Skill)

- **Solo lectura por defecto**; cualquier acción que publique, envíe o cargue pasa por aprobación humana en el chat.
- **Secretos (API keys de Apollo/Taplio, tokens de n8n) nunca en el repo** → variables de entorno en el host.
- Credencial/alcance **por usuario** cuando aplique; no cruzar datos entre personas.
- Allowlist explícita de operaciones; nada de acceso total.
