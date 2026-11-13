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
| `imagen` | Generar **imágenes AI** (fotos/ilustraciones) para posts — **gratis**. | Motor gratuito hosteado por nosotros (Flux/SD open-source o API gratis) → MCP. Las usuarias solo pegan la URL. | 🔧 En construcción ($0) |
| `video` | Generar **video** para posts — **gratis**. | **HyperFrames** propio (HTML→video en vps-ai, **$0**) expuesto como connector. | 🔧 En construcción ($0) |

> **Meta del arnés: todo GRATIS y desde el app de Claude (web/escritorio/móvil), sin Claude Code.** Las usuarias no programan ni usan terminal: solo **pegan URLs de connectors** una vez.
>
> **Reparto de lo visual (todo $0):**
> - **Gráficos/carruseles/tarjetas/infografías/charts/slides** → Claude los hace **ya, nativo** con *code execution* (sin connector).
> - **Fotos/ilustraciones AI** → connector `imagen` a un **motor gratuito que hosteamos** (no pagan por imagen).
> - **Video** → connector `video` a **HyperFrames** (nuestro, $0).
>
> Nota de expectativa honesta: lo gratis da calidad "muy buena", no nivel Midjourney/Veo. Para realismo tope habría que pagar — pero **no es necesario** para el objetivo.

## Qué connector sirve a qué Skill

- **`prospeccion-con-revision`** → usa `apollo` (buscar) + `n8n`/`google-sheets` (cargar lo aprobado).
- **`contenido-linkedin-con-revision`** → usa `taplio` (programar) o entrega listo para pegar.

Mientras los connectors a medida no estén, **los Skills ya funcionan como método** (Claude arma listas/posts de forma conversacional y guarda en Sheets si está conectado). Al enchufar el connector, el mismo Skill empieza a usarlo automáticamente.

## Principios (iguales a los del Skill)

- **Solo lectura por defecto**; cualquier acción que publique, envíe o cargue pasa por aprobación humana en el chat.
- **Secretos (API keys de Apollo/Taplio, tokens de n8n) nunca en el repo** → variables de entorno en el host.
- Credencial/alcance **por usuario** cuando aplique; no cruzar datos entre personas.
- Allowlist explícita de operaciones; nada de acceso total.
