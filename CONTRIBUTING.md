# Cómo contribuir a auditoria-skills

¡Gracias por tu interés en mejorar este catálogo! Este repositorio es mantenido por y para la comunidad de auditores que usan agentes de IA en su trabajo. Cada SKILL representa conocimiento profesional que muchos pueden reutilizar.

## Formas de contribuir

1. **Reportar un error o desactualización normativa** — abrir un *issue* con la plantilla `mejora-skill`.
2. **Proponer una nueva SKILL** — abrir un *issue* con la plantilla `nueva-skill`, esperar discusión, y luego abrir un PR.
3. **Mejorar documentación** — correcciones de README, guías en `docs/`, ejemplos en `examples/`.
4. **Aportar casos de uso reales** — añadir un nuevo escenario en `examples/`.

## Filosofía editorial

- **Precisión normativa por encima de extensión.** Es preferible un párrafo correcto que tres párrafos imprecisos. Citar siempre la versión vigente del estándar.
- **Lenguaje neutro.** Las SKILLs deben ser útiles para auditores en cualquier país hispanohablante. Evitar referencias a una sola jurisdicción salvo cuando el estándar lo exige (p. ej. SOX, FCPA).
- **Independencia de proveedor.** Las SKILLs no deben recomendar un software comercial específico salvo que sea referencia obligada (ACL, IDEA, SAP, etc., como ejemplos, no como prescripción).
- **Sin información confidencial.** Nunca incluir datos de clientes, papeles de trabajo reales, ni información que pudiera identificar un engagement específico.

## Flujo para proponer una nueva SKILL

1. Abrir un *issue* con la plantilla `nueva-skill` describiendo:
   - Nombre propuesto (kebab-case, prefijo `auditoria-` para especialidades).
   - Tipo: proceso (transversal) o especialidad (dominio).
   - Estándares ancla (mínimo 2).
   - Brecha que cubre frente al catálogo actual.
2. Esperar respuesta del equipo mantenedor (etiqueta `accepted` o discusión).
3. Crear un fork y una rama: `feature/skill-<nombre>`.
4. Añadir la carpeta en `skills/procesos/<nombre>/` o `skills/especialidades/<nombre>/` con:
   - `SKILL.md` siguiendo la plantilla de [`docs/crear-nueva-skill.md`](docs/crear-nueva-skill.md).
   - `README.md` siguiendo el patrón de las SKILLs existentes.
5. Actualizar:
   - `catalog.json` añadiendo la entrada.
   - `README.md` raíz (tabla resumen).
   - `CHANGELOG.md` bajo `[No publicado]`.
6. Abrir un Pull Request usando la plantilla del repo.

## Estilo del SKILL.md

- Frontmatter YAML con `name` y `description` obligatorios.
- `description` debe incluir disparadores léxicos (palabras clave que activan la SKILL).
- Cuerpo en español neutro, secciones numeradas o con encabezados claros.
- Citar normas con su nombre y número (ej. `NIA 530`, `ISO 27001:2022`).
- Indicar versiones cuando aplique (ej. `COBIT 2019`, `NIST CSF 2.0`).

## Revisión

Cada PR es revisado por al menos un mantenedor con experiencia en el dominio relevante. Buscamos:

- Corrección normativa.
- Aplicabilidad práctica (¿un auditor real puede usar esto?).
- Coherencia con el resto del catálogo.
- Ausencia de información sensible.

## Código de conducta

Al participar aceptás el [Código de Conducta](CODE_OF_CONDUCT.md). Sé respetuoso, profesional y constructivo.

## Licencia de tus contribuciones

Al enviar un PR aceptás que tu contribución se publique bajo la misma licencia del repositorio: **CC BY-SA 4.0**.
