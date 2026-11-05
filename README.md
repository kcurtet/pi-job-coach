# jobsearch

Base de operaciones de búsqueda de empleo: coaching, ofertas, candidaturas y embudo.

## Uso

```bash
cd ~/dev/jobsearch && pi
```

La skill `job-coach` se descubre automáticamente en este directorio. Arranca con cualquiera de: "coach", "busco trabajo", "qué ofertas hay", "revisa mi CV", "simulacro de entrevista", "seguimiento".

- **Primera sesión**: la skill hace el diagnóstico (preguntas por rondas) y genera `data/perfil.md` y `docs/diagnostico.md`.
- **Login de portales (una vez)**: `agent-browser --session jobs --headed open https://www.linkedin.com` e inicia sesión en la ventana; la sesión `jobs` conserva el login para búsquedas futuras. Igual con InfoJobs.

## Estructura

| Ruta | Qué es |
|---|---|
| `.agents/skills/job-coach/SKILL.md` | El coach: persona, diagnóstico, búsqueda, embudo, entrevistas |
| `data/perfil.md` | Perfil de candidato (lo escribe la primera sesión) |
| `data/applications.json` | Tracker de candidaturas — fuente de verdad del embudo |
| `data/acuerdos.md` | Tareas con plazo de cada sesión + historial |
| `docs/` | Diagnóstico e informes de embudo |
| `cv/` | CV fuente, versiones por rol y cartas |

## Fuentes de ofertas

- **Remoto vía API** (sin login): Remotive, Himalayas, Jobicy, Working Nomads, WeWorkRemotely (RSS).
- **España vía navegador** (agent-browser, sesión `jobs`): LinkedIn Jobs, InfoJobs — ambos con filtro remoto.
- Descubrimiento puntual con `web_search` (`site:linkedin.com/jobs`, etc.).
