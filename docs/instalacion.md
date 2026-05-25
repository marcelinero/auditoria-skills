# Guía de instalación

Las SKILLs de este repositorio son archivos Markdown con frontmatter YAML. Esto les permite ser utilizadas en prácticamente cualquier agente de IA moderno, ya sea como *skills* nativas, *system prompts*, *project knowledge* o instrucciones contextuales.

A continuación, el método de instalación recomendado para cada plataforma.

---

## 0. Servidor MCP — recomendado para Claude Desktop y Claude Code

El método más simple: un servidor MCP que expone las 20 SKILLs como herramientas nativas, sin copiar archivos ni gestionar contexto manualmente.

**Requisito:** tener [uv](https://docs.astral.sh/uv/getting-started/installation/) instalado.

```bash
# macOS / Linux
curl -LsSf https://astral.sh/uv/install.sh | sh

# Windows (PowerShell)
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Luego cloná el repo y agregá esta configuración a tu cliente:

```json
{
  "mcpServers": {
    "auditoria-skills": {
      "command": "uv",
      "args": ["run", "--script", "/ruta/al/repo/auditoria-skills/mcp/server.py"]
    }
  }
}
```

- **Claude Desktop:** el archivo de configuración está en `~/Library/Application Support/Claude/claude_desktop_config.json` (macOS) o `%APPDATA%\Claude\claude_desktop_config.json` (Windows).
- **Claude Code CLI:** ejecutá `claude mcp add auditoria-skills -- uv run --script /ruta/al/repo/auditoria-skills/mcp/server.py`

Instrucciones completas → [`../mcp/README.md`](../mcp/README.md)

---

## 1. Claude Code (CLI de Anthropic) — instalación de archivos

Claude Code soporta de forma nativa el formato SKILL.md.

### Opción A — Skills personales (todas tus sesiones)

```bash
# Clonar el repositorio en tu carpeta personal de skills
git clone https://github.com/marcelinero/auditoria-skills.git ~/.claude/skills/auditoria
```

Reinicia Claude Code y ejecuta `/skills` para verificar que se han cargado.

### Opción B — Skills por proyecto (sólo este repo)

```bash
# En la raíz de tu proyecto de auditoría
mkdir -p .claude/skills
git clone https://github.com/marcelinero/auditoria-skills.git .claude/skills/auditoria
```

### Opción C — Submódulo git

```bash
git submodule add https://github.com/marcelinero/auditoria-skills.git .claude/skills/auditoria
git submodule update --init
```

---

## 2. Claude.ai — Projects (interfaz web)

1. Crea un nuevo *Project* en [claude.ai](https://claude.ai).
2. En **Project knowledge**, sube los archivos `SKILL.md` que necesites (puedes empezar por las SKILLs de proceso y agregar especialidades según el tipo de auditoría).
3. En **Project instructions**, copia el contenido de [`docs/como-usar.md`](como-usar.md) sección "Orquestación de SKILLs".
4. Inicia una conversación; el agente cargará automáticamente las SKILLs como contexto.

> 💡 **Tip:** Para evitar saturar el contexto, sube sólo las SKILLs relevantes al tipo de auditoría que vas a ejecutar (típicamente: 3–4 procesos + 1–2 especialidades).

---

## 3. Claude Agent SDK (programático)

Si construyes tu propio agente con el [SDK de Anthropic](https://docs.anthropic.com/en/api/agent-sdk):

```python
from anthropic import Anthropic
from pathlib import Path

client = Anthropic()

# Cargar SKILLs como system prompt
skills_dir = Path("auditoria-skills/skills")
skill_files = [
    skills_dir / "procesos/planeacion-basada-riesgos/SKILL.md",
    skills_dir / "procesos/evaluacion-controles/SKILL.md",
    skills_dir / "especialidades/financiera/SKILL.md",
]
system_prompt = "\n\n---\n\n".join(f.read_text(encoding="utf-8") for f in skill_files)

response = client.messages.create(
    model="claude-opus-4-7",
    max_tokens=4096,
    system=system_prompt,
    messages=[{"role": "user", "content": "Planea una auditoría SOX 404 sobre el ciclo de ingresos."}],
)
print(response.content[0].text)
```

> 💡 Para optimizar costo, usa **prompt caching** marcando el bloque del system prompt como `cache_control: ephemeral`.

---

## 4. ChatGPT — Custom GPTs

1. En [chat.openai.com](https://chat.openai.com), crea un nuevo Custom GPT.
2. En **Instructions**, pega el contenido de la SKILL principal (especialidad) que quieras usar.
3. En **Knowledge**, sube los archivos `SKILL.md` adicionales (procesos transversales).
4. Configura el modelo (GPT-4o o superior).
5. Si quieres una experiencia conversacional, agrega en *Conversation starters*:
   - "Planea una auditoría de ciberseguridad bajo NIST CSF"
   - "Diseña la matriz de riesgos del ciclo de compras"
   - "Genera el cronograma del plan anual de auditoría"

---

## 5. Google Gemini — Gems

1. Abre [gemini.google.com](https://gemini.google.com) y entra a **Gems**.
2. En *Custom instructions*, pega la SKILL principal.
3. Activa la subida de archivos y carga las SKILLs adicionales por sesión cuando las necesites.

---

## 6. Otros agentes (Cursor, Windsurf, Aider, etc.)

La mayoría de IDEs con agentes IA permiten cargar archivos de contexto:

- **Cursor:** copia las SKILLs en `.cursor/rules/`.
- **Windsurf:** colócalas en `.windsurfrules` o `.windsurf/rules/`.
- **Aider:** úsalas con `--read auditoria-skills/skills/.../SKILL.md`.
- **GitHub Copilot Chat:** referencia el archivo con `#file:SKILL.md`.

---

## 7. Uso minimalista — copia y pega

Si tu plataforma no soporta archivos de contexto, simplemente:

1. Abre el `SKILL.md` que necesitás.
2. Copia el contenido completo.
3. Pégalo al inicio de tu conversación con el modelo.
4. Continúa con tu instrucción específica.

---

## Verificación

Independientemente del método, podés verificar que la SKILL está activa preguntando al agente:

> *"¿Qué SKILLs tienes activas y cuáles son sus marcos de referencia?"*

Una respuesta correcta debe enumerar los nombres exactos de las SKILLs y los estándares ancla.

---

## Próximos pasos

- Lee [`como-usar.md`](como-usar.md) para entender cómo orquestar varias SKILLs en un mismo trabajo de auditoría.
- Revisá [`casos-de-uso.md`](casos-de-uso.md) para ver combinaciones típicas por tipo de auditoría.
