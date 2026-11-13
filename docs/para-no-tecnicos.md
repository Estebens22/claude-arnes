# Cómo activar tu "arnés" en Claude (guía sin tecnicismos)

Vas a enseñarle a tu Claude un **Skill** (una habilidad: un manual de cómo hacer una tarea bien) y, más adelante, conectarle **herramientas** (como Apollo o n8n). Funciona en Claude web, app de escritorio y celular — **la misma cuenta en todos tus dispositivos**.

> Requisito: tener **Claude Max** (o Pro/Ultra). Ya lo tienes. ✅

---

## Parte 1 — Subir el Skill (5 minutos, se hace una vez)

1. **Descargá el Skill de este repositorio.**
   - Entrá al repo en GitHub → carpeta `skills/prospeccion-con-revision`.
   - Descargá esa carpeta (o el repo completo con el botón verde **Code → Download ZIP** y abrí la carpeta `skills/prospeccion-con-revision`).
   - Dentro está el archivo `SKILL.md`. Comprimí esa **carpeta** en un `.zip` (clic derecho → Comprimir).

2. **Prendé los Skills en tu Claude.**
   - Abrí Claude en el navegador → entrá a **`claude.ai/customize/skills`**.
   - Si te pide, activá **"Code execution and file creation"** (ejecución de código). Es necesario para los Skills.

3. **Subí tu Skill.**
   - En esa misma pantalla (Skills), tocá **"Upload skill" / "Subir habilidad"** y elegí el `.zip` de `prospeccion-con-revision`.
   - Activá el interruptor del Skill (que quede en "on").

¡Listo! Ya tenés la habilidad. Claude la va a usar **solo cuando aplique** (cuando le pidas prospectar/conseguir clientes).

---

## Parte 2 — Usarlo (en cualquier dispositivo)

Abrí Claude (web, escritorio o celular) y escribile normal, por ejemplo:

> *"Ayudame a conseguir clientes para [lo que vendés]. Son [tipo de empresa] en [ciudad/país] y decide el [cargo]."*

Claude va a:
1. Preguntarte a quién le vendés (perfil de cliente).
2. Armar una **lista de prospectos**.
3. Redactar un **correo de acercamiento** personalizado para cada uno.
4. **Mostrarte todo para que lo revises** — no envía ni carga nada sin tu "sí".
5. Ejecutar solo lo que aprobaste.

> La regla de oro del Skill: **nada sale sin tu aprobación.** Primero revisás, después se envía.

---

## Parte 3 — Conectar herramientas (Apollo, n8n) — *lo agregamos esta semana*

Cuando tengamos listas las herramientas, te vamos a pasar un **enlace (URL) de connector**. Para conectarlo:

1. En Claude → **Ajustes → Conectores** (Settings → Connectors).
2. Tocá **"Agregar connector personalizado"** y pegá la URL que te demos.
3. Autorizá. Listo: ahora Claude puede **buscar en Apollo** y **disparar tus flujos de n8n** cuando se lo pidas.

No tenés que instalar nada ni mantener ningún servidor: la conexión la maneja Claude por vos.

---

## Preguntas rápidas

- **¿Tengo que saber programar?** No. Subís un archivo y pegás un enlace. Nada más.
- **¿Funciona en mi celular?** Sí, con la misma cuenta.
- **¿Claude va a mandar correos solo?** No. El Skill está hecho para **mostrarte todo y esperar tu aprobación** antes de cualquier envío.
- **¿Se puede compartir con otra persona?** Sí: le pasás este repo, baja el Skill y lo sube a su propio Claude igual que vos.
