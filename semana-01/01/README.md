# 📚 Clase 01: Presentación del Módulo y Diagnostico

- Unidad 1: **Taller de Calidad y Testing de Software**
- Fecha: Lunes 11 de Agosto, 2025
- Horario: 15:50 - 18:10
- Docente: Diego Obando

## 🎯 Objetivos de la Clase

Al finalizar la clase, serás capaz de:

- Comprender el contexto y objetivos del módulo.
- Identificar tu nivel actual de conocimiento en testing mediante el diagnóstico inicial.
- Configurar tu entorno de trabajo para el curso con: Git, VS Code, GitHub y Node.js.

## 📖 Contenidos

- Introducción al Testing de Software
- Diagnóstico de Conocimientos Previos
- Configuración del Entorno de Trabajo
  - Instalación de Git
  - Instalación de Visual Studio Code
  - Creación de una cuenta en GitHub
  - Instalación de Node.js

## 📚 Introducción al Testing de Software

### 1. ¿Qué es “Testing”? 🔍

Actividad sistemática para evaluar si el software hace lo que debe (cumple requisitos) e identificar defectos antes de que lleguen al usuario.  
No es “demostrar que funciona”, es “buscar evidencia de que podría fallar”.

### 2. QA, QC, Testing – Diferencias clave 🧭

- **QA (Quality Assurance / Aseguramiento de Calidad):** Procesos y políticas preventivas (normas, estándares, revisiones).
- **QC (Quality Control / Control de Calidad):** Actividades para verificar el producto (inspecciones, pruebas).
- **Testing:** Subconjunto de QC. Ejecutar el software (o partes) y observar resultados.

> Metáfora: QA diseña la receta, QC revisa el plato, Testing lo prueba para ver si realmente sabe bien.

### 3. Conceptos esenciales (Glosario rápido) 🧠

| Término         | Definición corta                                 |
| --------------- | ------------------------------------------------ |
| Requisito       | Necesidad o expectativa del usuario/negocio      |
| Caso de prueba  | Pasos + datos + resultado esperado               |
| Bug / Defecto   | Error introducido en el código / artefactos      |
| Fallo (Failure) | Comportamiento incorrecto observado en ejecución |
| Error humano    | Acción que introduce el defecto                  |
| Assert          | Verificación (comparar esperado vs real)         |
| Ambiente        | Conjunto controlado: SO + versión + dependencias |

### 4. ¿Por qué testear? (Motivadores) 🚦

- Detectar defectos temprano (más barato corregir).
- Reducir regresiones (errores que vuelven).
- Aumentar confianza al refactorizar.
- Documentar comportamiento esperado (tests = especificación viva).
- Base para integración continua (CI) y despliegues frecuentes.

### 5. Principios básicos del testing (Resumen) 📐

1. No demuestra ausencia total de defectos.
2. Comenzar lo antes posible (shift-left).
3. Agrupar pruebas por nivel y objetivo (pirámide).
4. Exhaustivo es imposible → priorizar riesgo.
5. Agrupar defectos: suelen concentrarse en módulos “calientes”.
6. Pesticide paradox: si repites siempre lo mismo, dejas de encontrar nuevos fallos.
7. El contexto importa: no se testea igual un videojuego que un sistema bancario.

### 6. Niveles de prueba (visión macro) 🏗️

| Nivel            | Pregunta                         | Ejemplo simple hoy        |
| ---------------- | -------------------------------- | ------------------------- |
| Unidad           | ¿Funciona este pedacito aislado? | función suma(a,b)         |
| Integración      | ¿Cooperan bien módulos juntos?   | suma() + logger           |
| Sistema          | ¿Funciona todo como un todo?     | CLI completa              |
| Aceptación (UAT) | ¿Satisface al usuario/negocio?   | Flujo “registrar usuario” |

(Profundizaremos más adelante; hoy solo contexto.)

### 7. Pirámide de Pruebas 🧱

Base amplia de **tests unitarios** (rápidos), menor cantidad de **integración**, pocos y críticos de **UI / end-to-end** (más lentos y frágiles).  
Objetivo: equilibrio costo / velocidad / cobertura de riesgo.

### 8. Tipos según objetivo 🎯

- Funcionales (qué hace)
- No funcionales (rendimiento, seguridad, usabilidad) – se introducen más adelante
- Regresión (verificar que algo que funcionaba sigue funcionando)
- Exploratorio (aprendo + diseño + ejecuto simultáneamente)

### 9. Ciclo “Rojo → Verde → Refactor” (TDD en miniatura) 🔄

1. Escribir un test que falla (rojo)
2. Implementar lo mínimo para que pase (verde)
3. Mejorar el código manteniendo tests verdes (refactor)

(No aplicaremos TDD completo hoy, solo ver el concepto.)

### 10. Roles y responsabilidades 👥

- Desarrollador: escribe y mantiene pruebas (unidad / integração ligera).
- QA/Tester: diseña escenarios, analiza riesgos, apoya automatización, realiza exploración.
- Equipo: calidad compartida – “No es trabajo de QA arreglar lo que desarrollo rompe”.

### 11. Qué haremos HOY ✅

- Entender vocabulario base.
- Ver flujo básico de validación (conceptual).
- Preparar entorno: Node.js + Git + VS Code.
- Crear repositorio y carpeta para tests.
  (NO: pruebas automatizadas avanzadas, cobertura, mocks complejos.)

### 12. Qué haremos en las próximas clases 🗓️

- Instalar y usar Jest (estructura de test, expect, matchers).
- Diseñar casos de prueba efectivos.
- Introducir mocks, stubs y coverage.
- Integrar tests en pipeline.

### 13. Errores comunes de principiantes ⚠️

- Test que solo “imprime cosas” (falta assert).
- Mezclar muchos escenarios en un solo test.
- Nombres vagos: “test1”, “function works”.
- Dependencias ocultas (orden de ejecución importa).
- Test frágiles (dependen de hora real, datos externos sin aislar).

### 14. Indicadores que iremos midiendo 📊

- % estudiantes que crean y ejecutan al menos 1 test.
- Número medio de asserts por test.
- Tiempo entre cambio y ejecución de tests (feedback loop).

### 15. Recursos recomendados (inicio) 🔗

- Glosario ISTQB (ES): https://glossary.istqb.org/es/
- Pirámide de pruebas (artículo de referencia corto)
- “Testing JavaScript Fundamentals” (resumen interno entregable posterior)

> Pregunta guía para el resto del módulo: “¿Qué pasa si esto deja de funcionar mañana y nadie se da cuenta?” – Esa es la motivación para automatizar.

## Diagnóstico de Conocimientos Previos

Formato: EN PAPEL. Tiempo: 10–12 min. Responde con tus palabras. Si no sabes, escribe “NS”.

### A. Experiencia (breve)

1. Tiempo programando (meses / años) y qué has hecho.
2. Lenguajes usados y para qué (1 frase cada uno).
3. ¿Cómo usas hoy Git? (menciona comandos o flujo típico).

### B. Testing

4. ¿Has probado código antes? ¿Cómo lo hiciste? (manual / algún framework / nunca).
5. ¿Qué crees que valida un test unitario?
6. Diferencia (según tú) entre “bug” y “fallo”.

### C. Conceptos (definición corta, 1 línea)

7. Pirámide de pruebas:
8. TDD:
9. Assert / aserción:

### D. JavaScript / Node

10. Pasos mínimos para iniciar un proyecto Node y poder ejecutar un archivo JS.
11. ¿Cuándo usarías async/await? (describe una situación real).

### E. Mini Ejercicio

12. Escribe la función esPar(n) (solo lógica) y casos esperados para n=4 y n=7.

### F. Objetivo Personal

13. Una frase: “Al terminar el módulo quiero poder …”

// ...existing code...

## 🛠️ Configuración del Entorno de Trabajo

Objetivo: salir hoy con un proyecto Node listo para comenzar a testear en la próxima clase.

### 1. Instalación de Git ✅

1. Visita https://git-scm.com/download/win (elige instalador 64-bit).
2. Acepta valores por defecto (importante: “Adjusting your PATH” → “Git from the command line”).
3. Finaliza. Abre una terminal (PowerShell o CMD) y verifica:
   ```bash
   git --version
   ```
4. Configura identidad (solo la primera vez):
   ```bash
   git config --global user.name "Tu Nombre"
   git config --global user.email "tu.email@ejemplo.com"
   git config --global core.autocrlf true   # Normaliza saltos de línea en Windows
   git config --global init.defaultBranch main
   ```
5. Verifica config:
   ```bash
   git config --list
   ```

### 2. Instalación de Visual Studio Code 💻

1. Descarga desde https://code.visualstudio.com/
2. Instala (marca “Add to PATH” si aparece).
3. Extensiones recomendadas iniciales:
   - GitLens (historial y blame)
   - ESLint
   - Error Lens
   - EditorConfig (opcional)
4. Atajos clave (teclado latinoamericano):
   - Abrir terminal integrada: Ctrl + Ñ
   - Paleta de comandos: Ctrl + Shift + P
   - Guardar: Ctrl + S

### 3. Creación de Cuenta en GitHub 🌐

1. Ir a https://github.com/ y registrarse (usa correo académico si tienes).
2. Ajustar Settings → Email (elige “Keep my email addresses private” si deseas).
3. Crear repositorio nuevo:
   - Nombre: taller-testing-2025
   - Público (ok para el curso)
   - SIN README (lo crearemos local y luego subimos)
   - Copia la URL remota (HTTPS)

### 4. Instalación de Node.js (LTS) ⚙️

1. Descarga LTS desde https://nodejs.org/
2. Instala con valores por defecto.
3. Verifica:
   ```bash
   node -v
   npm -v
   ```
   (Avanzado opcional: usar nvm-windows más adelante para múltiples versiones.)

---

### 5. Crear el Proyecto Base 📂

En una carpeta de trabajo (ej: C:\dev):

```bash
mkdir taller-testing-2025
cd taller-testing-2025
git init
npm init -y
code .
```

Estructura mínima inicial:

```
taller-testing-2025/
  package.json
  src/
    index.js
  README.md
```

Crear index.js:

```javascript
// src/index.js
function suma(a, b) {
  return a + b;
}
console.log("Demo:", suma(2, 3));
```

Actualizar README.md (breve descripción).

---

### 6. Flujo Git Básico (Local) 🔄

Comandos esenciales:

```bash
git status          # Ver qué cambió
git add .           # Preparar cambios
git commit -m "feat: proyecto base"
git log --oneline   # Historial compacto
git diff            # Ver diferencias antes de add
```

Buenas prácticas de mensajes (convención simple):

- feat: nueva funcionalidad
- fix: corrección
- chore: tareas de soporte (config, limpieza)
- docs: documentación

---

### 7. Conectar con GitHub (Remoto) ☁️

Agregar remoto y subir:

```bash
git remote add origin https://github.com/TU_USUARIO/taller-testing-2025.git
git branch -M main
git push -u origin main
```

Confirmar en GitHub que aparecen los archivos.

Clonar (si empiezas en otro equipo):

```bash
git clone https://github.com/TU_USUARIO/taller-testing-2025.git
```

Actualizar (traer cambios):

```bash
git pull
```

---

### 8. Ramas (Uso Inicial) 🌿

Crear y cambiar a una rama:

```bash
git checkout -b ejercicio/diagnostico
# ... modificas archivos ...
git add .
git commit -m "feat: agrega respuestas diagnóstico"
git push -u origin ejercicio/diagnostico
```

Luego abrirás un Pull Request (PR) en GitHub (lo veremos formalmente más adelante).

---

### 9. Archivo .gitignore 🙈

Crear .gitignore:

```
node_modules
.env
.DS_Store
coverage
```

Agregarlo y hacer commit:

```bash
git add .gitignore
git commit -m "chore: agrega gitignore"
```

---

### 10. Resumen de Flujo Diario 🧭

1. git pull (antes de empezar)
2. git checkout -b tarea/lo-que-haces (si aplica)
3. Codificar (commits pequeños y claros)
4. git push
5. (Más adelante) Crear PR y pedir revisión

---

### 11. Comandos de Referencia Rápida ⚡

| Acción             | Comando                    |
| ------------------ | -------------------------- |
| Ver estado         | git status                 |
| Agregar todo       | git add .                  |
| Commit             | git commit -m "mensaje"    |
| Cambiar rama       | git checkout nombre        |
| Nueva rama         | git checkout -b nueva-rama |
| Ver ramas          | git branch                 |
| Agregar remoto     | git remote add origin URL  |
| Subir cambios      | git push origin rama       |
| Traer cambios      | git pull                   |
| Historial compacto | git log --oneline          |

---

### 12. Problemas Frecuentes 🛑

| Situación                   | Solución                                                                           |
| --------------------------- | ---------------------------------------------------------------------------------- |
| “git: command not found”    | Reabrir terminal; reinstalar Git; verificar PATH                                   |
| Rechazado por commits atrás | git pull --rebase origin main; resolver conflictos; push                           |
| Nombre/email incorrectos    | git config --global user.name "Nuevo"                                              |
| node_modules subido         | Añadir a .gitignore, eliminar carpeta del control: git rm -r --cached node_modules |

---

### 13. Checklist Final (Antes de cerrar la clase) ✅

- [ ] Git instalado y configurado
- [ ] Node y npm verificados
- [ ] Repo local inicializado (o clonado)
- [ ] README.md creado
- [ ] .gitignore agregado
- [ ] Primer commit subido a GitHub
- [ ] Estructura src/index.js funcional
