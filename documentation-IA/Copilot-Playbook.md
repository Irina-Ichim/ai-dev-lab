# Copilot Playbook: Maximizar ROI, Minimizar Consumo

> **Objetivo**: Usar Copilot estratégicamente para pagar menos sin perder velocidad.

---

## 1. Features de Copilot en VS Code

| Feature | Coste Relativo | Cuándo Activarla | Cuándo Desactivarla | Lenguajes Clave | Alternativa Barata |
|---------|----------------|------------------|---------------------|-----------------|-------------------|
| **Inline Suggestions** | Bajo | Siempre (escritura de código) | En archivos de configuración o JSON/YAML estáticos | JS/TS/React/Python | Snippets de VS Code, Emmet |
| **Copilot Chat** | Alto | Solo para problemas complejos o diseño de arquitectura | Cuando puedes resolver con docs o Stack Overflow | Todos (neutral) | Google, Stack Overflow, docs oficiales |
| **Workspace Indexing** | Medio-Alto | Proyectos grandes (>50 archivos) donde necesitas contexto cross-file | Proyectos pequeños (<20 archivos) | TS/Java/Spring Boot | Búsqueda nativa VS Code (`Ctrl+Shift+F`) |
| **Agent Mode** (`@workspace`)| Alto | Refactors multi-archivo o migraciones | Cambios localizados en 1-2 archivos | TS/React/Java | Refactoring manual con Find & Replace |
| **Edit Mode** (multi-line) | Medio | Generación de boilerplate (componentes, clases) | Cuando ya tienes el código claro en tu cabeza | React/Java/Python | Templates de archivo, snippets personalizados |
| **Explain/Fix** | Medio | Errores crípticos o stack traces complejos | Errores de sintaxis obvios | Java/Python | ESLint, TypeScript compiler, linter errors |
| **Generate Tests** | Medio | Tests unitarios repetitivos (happy path) | Tests de integración o E2E complejos | JS/TS/Python | Frameworks de test con helpers (Vitest, Jest) |
| **Generate Docs** | Bajo-Medio | Funciones públicas de librerías | Código interno de equipo | Todos | JSDoc templates, copiar/pegar estructura |
| **Slash Commands** (`/fix`, `/explain`) | Medio | Debugging de bugs no obvios | Cuando el error es un typo o falta de import | Todos | Console.log, debugger, linters |

---

## 2. Reglas Fijas

### ✅ Siempre ON
- **Inline Suggestions** → Es tu herramienta principal.  Coste bajo, ROI alto.
- **Ghost Text** (preview) → No consume hasta que aceptas. 
- **Auto-trigger** → Solo activa cuando escribes código, no cuando lees.

### ❌ Siempre OFF
- **Copilot Chat en sidebar** → No lo dejes abierto; abre solo cuando lo necesites (`Ctrl+Shift+I`).
- **Auto-regenerate en Chat** → No pidas variantes automáticas; edita tu prompt.
- **`@workspace` por defecto** → Usa solo cuando sea necesario (consume contexto masivo).

### 🔄 Toggleable (Atajo: `Ctrl+Shift+P` → "Toggle Copilot")
- **Copilot completo** → Desactiva cuando: 
  - Estás leyendo código (no escribiendo).
  - Estás en reuniones con código abierto.
  - Editas archivos de configuración (`.env`, `package.json`, etc.).

---

## 3. Checklists por Tarea

### 🚀 Estoy empezando una feature
- ✅ **Activar**:  Inline Suggestions, Edit Mode (si necesitas boilerplate).
- ❌ **Desactivar**:  Chat, `@workspace`.
- **Flujo**:
  1. Define tipos/interfaces manualmente (TypeScript).
  2. Deja que Copilot complete implementaciones.
  3. Si necesitas arquitectura → Dibuja primero en papel, luego usa Chat para validar.

### 🐛 Estoy debuggeando
- ✅ **Activar**: Inline Suggestions (para fixes rápidos).
- 🔄 **Chat solo si**:  Stack trace >20 líneas o error en librería externa.
- ❌ **Desactivar**: Edit Mode, `@workspace`.
- **Flujo**:
  1. `console.log` / debugger primero.
  2. Si no es obvio → `/explain` en Chat con el error específico. 
  3. **Límite**: Max 2 preguntas.  Si no resuelve, ve a docs/GitHub issues.

### 🔧 Voy a refactorizar
- ✅ **Activar**: Inline Suggestions. 
- 🔄 **Agent Mode** solo si:  Cambios en >5 archivos relacionados.
- ❌ **Desactivar**: Chat para consultas genéricas.
- **Flujo**:
  1. Usa refactors nativos de VS Code (`F2` para rename, Extract Function).
  2. Si es complejo → `@workspace` con prompt específico:  "Renombrar `UserService` a `AccountService` en todos los archivos".
  3. **Límite**: Max 1 sesión de Agent Mode por refactor.

### ✅ Voy a escribir tests
- ✅ **Activar**: Inline Suggestions, `/tests` command.
- ❌ **Desactivar**: Chat para explicaciones de testing.
- **Flujo**:
  1. Escribe el primer test a mano (estructura).
  2. Deja que Copilot complete casos similares.
  3. Para mocks complejos → Usa librerías (`msw`, `jest.mock`) antes que Chat. 

### 📝 Voy a documentar
- ✅ **Activar**: Inline Suggestions (JSDoc/docstrings).
- 🔄 **Generate Docs** solo para:  APIs públicas o funciones exportadas.
- ❌ **Desactivar**: Chat. 
- **Flujo**: 
  1. Escribe `/**` y deja que Copilot complete.
  2. Si necesitas README → Usa template markdown + Copilot para llenar secciones. 

---

## 4. Modo Ahorro (Semanas de Alto Consumo)

### Configuración Recomendada
```json
// settings.json
{
  "github.copilot.enable": {
    "*": true,
    "yaml": false,
    "json": false,
    "markdown": false
  },
  "github.copilot.editor.enableAutoCompletions": true,
  "github.copilot.chat.enabled": false // Activa manualmente cuando necesites
}
```

### Hábitos de Ahorro
- ❌ **No pidas explicaciones largas** → En lugar de "explícame esta función", pregunta "qué hace línea 45".
- ❌ **No regeneres prompts** → Si la respuesta no sirve, edita tu pregunta en lugar de pedir variantes.
- ✅ **Fragmenta peticiones** → En lugar de "crea un CRUD completo", pide "crea solo el endpoint POST". 
- ✅ **Usa ejemplos concretos** → "Completa esta función para sumar dos números" > "ayúdame con esta función". 
- ✅ **Cierra Chat después de usar** → No lo dejes abierto consumiendo contexto. 
- ✅ **Desactiva Copilot al leer código** → Solo activa al escribir. 

### Telemetría (Monitorea tu Consumo)
- Revisa tu usage en GitHub dashboard mensualmente.
- Si ves picos, identifica qué días usaste Chat intensivamente. 

---

## 5. FAQ: Decisiones Rápidas

### ❓ Solo necesito completar una función
→ **Usa**: Inline Suggestions.   
→ **No uses**: Chat.  
→ **Tip**: Escribe firma + tipos, deja que Copilot llene el cuerpo.

### ❓ Necesito entender un error
→ **1º**: Lee el mensaje de error completo.  
→ **2º**: Google/Stack Overflow (gratis).  
→ **3º**: Si sigue sin estar claro → Chat con `/explain` + pega solo el error (no todo el archivo).

### ❓ Necesito cambios en varios archivos
→ **Si son <3 archivos**: Hazlo manual con Inline Suggestions.  
→ **Si son 3-10 archivos**: `@workspace` con prompt específico.  
→ **Si son >10 archivos**: Considera script automatizado (Node.js, bash) + Copilot para generar el script.

### ❓ Estoy atascado en un problema de arquitectura
→ **Antes de Chat**: 
  1. Dibuja diagrama en papel/Excalidraw.
  2. Consulta docs del framework.
  3. Busca ejemplos en GitHub.
→ **Usa Chat solo si**: Necesitas validar tradeoffs entre opciones (ej: "Context API vs Zustand para estado global en React").

### ❓ Necesito aprender una nueva librería
→ **No uses Chat** → Lee docs oficiales (gratis y más actualizado).  
→ **Usa Inline Suggestions** para completar código basado en ejemplos de docs. 

### ❓ Tengo que migrar código (ej: JavaScript → TypeScript)
→ **<5 archivos**: Manual + Inline Suggestions.  
→ **>5 archivos**:  `@workspace` con prompt:  "Convierte estos archivos JS a TS con tipos explícitos".  
→ **Límite**: Max 1 sesión, luego revisa manual.

---

## Bonus:  Métricas de Éxito

Mide tu eficiencia cada mes:

| Métrica | Target |
|---------|--------|
| **% de código generado por Inline vs Chat** | >80% inline |
| **Promedio preguntas Chat/día** | <5 |
| **Uso de `@workspace`/semana** | <3 veces |
| **Tiempo ahorrado** | >2 horas/semana |

---

## Atajos de Teclado Clave

- `Tab` → Aceptar sugerencia inline. 
- `Alt+]` / `Alt+[` → Navegar entre sugerencias.
- `Ctrl+Shift+I` → Abrir Chat (úsalo manualmente).
- `Ctrl+Enter` → Activar Copilot en bloque de código.
- `Esc` → Rechazar sugerencia (cuando no aporta).

---

**Regla de Oro**: Si puedes resolverlo en <2 minutos sin Copilot, no uses Copilot.
