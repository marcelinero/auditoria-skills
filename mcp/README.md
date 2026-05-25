# auditoria-skills — Servidor MCP

Servidor [Model Context Protocol (MCP)](https://modelcontextprotocol.io) que expone las **20 SKILLs de auditoría** de este repositorio como herramientas listas para usar desde cualquier cliente compatible: Claude Desktop, Claude Code, o cualquier agente construido con el SDK de Claude.

---

## Herramientas disponibles

| Herramienta | Descripción |
| --- | --- |
| `listar_skills` | Lista las 20 SKILLs con tipo, categoría/dominio y marcos normativos |
| `obtener_skill` | Devuelve el contenido completo de una SKILL por su nombre exacto |
| `buscar_skills` | Filtra el catálogo por tipo (`proceso`/`especialidad`) y/o marco normativo |

---

## Requisitos

- [**uv**](https://docs.astral.sh/uv/getting-started/installation/) — gestor de paquetes Python (recomendado, sin pasos previos de instalación)
- **Python 3.11+** — alternativa sin `uv`

### Instalar `uv` (si no lo tenés)

```bash
# macOS / Linux
curl -LsSf https://astral.sh/uv/install.sh | sh

# Windows (PowerShell)
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

---

## Configuración

### Claude Desktop

Editá el archivo de configuración de Claude Desktop:

- **macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows:** `%APPDATA%\Claude\claude_desktop_config.json`
- **Linux:** `~/.config/Claude/claude_desktop_config.json`

```json
{
  "mcpServers": {
    "auditoria-skills": {
      "command": "uv",
      "args": [
        "run",
        "--script",
        "/ruta/completa/al/repo/auditoria-skills/mcp/server.py"
      ]
    }
  }
}
```

> **Windows:** usá barras invertidas dobles o barras simples normales, por ejemplo:
> `"C:/Users/TuUsuario/auditoria-skills/mcp/server.py"`

Reiniciá Claude Desktop después de guardar.

---

### Claude Code (CLI)

Agregá el servidor al proyecto con:

```bash
claude mcp add auditoria-skills -- uv run --script /ruta/al/repo/auditoria-skills/mcp/server.py
```

O editá `.claude/settings.json` en la raíz del proyecto donde usás las SKILLs:

```json
{
  "mcpServers": {
    "auditoria-skills": {
      "command": "uv",
      "args": [
        "run",
        "--script",
        "/ruta/al/repo/auditoria-skills/mcp/server.py"
      ]
    }
  }
}
```

---

### Sin `uv` (Python directo)

Si tenés Python 3.11+ y preferís instalación manual:

```bash
pip install mcp
python /ruta/al/repo/auditoria-skills/mcp/server.py
```

Configuración en `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "auditoria-skills": {
      "command": "python",
      "args": ["/ruta/al/repo/auditoria-skills/mcp/server.py"]
    }
  }
}
```

---

## Verificar que funciona

En Claude Desktop o Claude Code, enviá:

```text
Listá las SKILLs de auditoría disponibles.
```

El agente debería llamar a `listar_skills` y devolver el catálogo completo.

---

## Ejemplos de uso

### Cargar una SKILL específica

```text
Cargá la SKILL auditoria-ciberseguridad y ayudame a planear
una auditoría basada en NIST CSF 2.0.
```

El agente invocará `obtener_skill` con `nombre: "auditoria-ciberseguridad"` y luego trabajará con el contenido de esa SKILL.

### Buscar SKILLs por marco normativo

```text
¿Qué SKILLs del catálogo están ancladas a normas ISO?
```

El agente invocará `buscar_skills` con `marco: "ISO"`.

### Flujo completo de una auditoría

```text
Voy a hacer una auditoría de cumplimiento de ISO 37301 en una empresa
del sector financiero. Cargá las SKILLs relevantes y ayudame a
construir el plan de engagement.
```

El agente buscará y cargará `auditoria-cumplimiento` + `planeacion-basada-riesgos`.

---

## Estructura del servidor

```text
mcp/
├── server.py   ← servidor MCP (archivo único con dependencias inline)
└── README.md   ← esta guía
```

El servidor lee los archivos `SKILL.md` directamente desde el repositorio, por lo que siempre refleja la versión más reciente del catálogo sin ningún paso de sincronización.

---

## Compatibilidad

| Cliente | Soporte |
| --- | --- |
| Claude Desktop (macOS / Windows) | ✅ |
| Claude Code (CLI) | ✅ |
| Agentes via Claude API + MCP SDK | ✅ |
| Cualquier cliente MCP compatible | ✅ |

---

## Licencia

Mismo que el repositorio: [CC BY-SA 4.0](../LICENSE).
