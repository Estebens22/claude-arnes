# Guion de clase — "Tu primer arnés agéntico con Claude"

Para: personas que están arrancando (no técnicas). Duración: ~30–40 min.
Objetivo del día: que cada una **suba un Skill a su Claude** y vea a Claude **trabajando con un método**, no solo chateando.

---

## 1. La idea en una frase (2 min)
> "Claude por defecto responde. Con un **Skill** le damos un **método** (cómo hacer algo bien), y con **connectors** le damos **herramientas** (manos). Juntos = un asistente que hace tareas, no solo que conversa."

Analogía: el Skill es la **receta**; el connector es el **brazo** que agarra los ingredientes.

## 2. Mostrar el antes/después (5 min)
- Pedile a Claude (sin skill): *"conseguime clientes"* → respuesta genérica.
- Después de subir el Skill, la misma pregunta → Claude **pregunta el perfil, arma lista, redacta correos y pide revisión**. Ese salto es el "aha".

## 3. Manos a la obra: subir el Skill (10 min)
Que cada una siga `docs/para-no-tecnicos.md` → Parte 1:
1. Descargar la carpeta `skills/prospeccion-con-revision` del repo.
2. Ir a `claude.ai/customize/skills`, activar "code execution".
3. Subir el `.zip` del Skill y prenderlo.

(Ayudar una por una; es el paso donde se traban.)

## 4. Usarlo juntos (10 min)
Cada una le escribe a su Claude un caso real suyo:
> *"Ayudame a conseguir clientes para [mi negocio]. Son [tipo] en [ciudad] y decide el [cargo]."*
Observar cómo Claude: pregunta el ICP → arma lista → redacta → **muestra para revisión**. 
Recalcar: **Claude no mandó nada; esperó tu aprobación.** Esa es la forma correcta de trabajar con un agente.

## 5. Cierre y qué sigue (5 min)
- Hoy: el Skill (el método). ✅
- Esta semana: les conectamos **Apollo + n8n** (las herramientas) con un enlace para pegar → ahí ya busca contactos reales y dispara flujos.
- Más adelante: tareas que corren solas con revisión (eso requiere un motor tipo n8n; lo vemos cuando estén cómodas con lo básico).

## Mensajes clave para dejar sembrados
- **"Un agente bueno no es el que hace todo solo; es el que hace el trabajo y te deja aprobar."** (revisión humana = calidad y control).
- **"Empezamos poco a poco: primero el método, después las herramientas, después la automatización."**
- **"Es tu Claude, en todos tus dispositivos. No hay que mantener nada."**
