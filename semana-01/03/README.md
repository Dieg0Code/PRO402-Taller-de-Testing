# 📚 Clase 03: Software Testeado vs No Testeado, Casos Reales: Fallos famosos por falta de Testing

- Unidad 1: **Taller de Calidad y Testing de Software**
- Fecha: Miércoles 13 de Agosto, 2025
- Horario: 15:50 - 18:10
- Docente: Diego Obando

## 🎯 Objetivos de la Clase

Al finalizar la clase, serás capaz de:

- Comprender la importancia de las pruebas en el desarrollo de software.
- Identificar casos reales de fallos en software debido a la falta de testing.
- Analizar y discutir lecciones aprendidas de fallos famosos.

## 📖 Contenidos

- Importancia de las pruebas en el desarrollo de software.
- Casos reales de fallos en software por falta de testing.
- Lecciones aprendidas de fallos famosos.

## Software Testeado vs No Testeado

### 1. Idea Central 🧠

Un sistema “funciona” no significa que sea confiable. La diferencia real se nota cuando:

- Cambias código → ¿Sigue comportándose igual? (regresión)
- Escala el uso → ¿Responde de forma estable?
- Ocurre un error → ¿Lo detectas pronto o el usuario te avisa?

### 2. Contraste Rápido ⚖️

| Aspecto                                | Software Testeado              | Software No Testeado       |
| -------------------------------------- | ------------------------------ | -------------------------- |
| Cambios pequeños                       | Confianza (suite verde)        | Miedo a romper algo        |
| Bugs reportados por usuarios           | Menos y más específicos        | Muchos y repetidos         |
| Refactor                               | Hábito saludable               | Postergado indefinidamente |
| Documentación de comportamiento        | Tests vivos                    | Memoria tribal             |
| Tiempo de incorporación de nuevos devs | Corto (lean en tests)          | Largo (depende de “gurú”)  |
| Coste de defectos                      | Descubiertos temprano (barato) | Tarde en prod (caro)       |

### 3. Coste del Defecto 💸 (Regla empírica)

Corrigiendo en:

- Diseño: barato (1x)
- Desarrollo: 5x
- Pruebas internas: 10x
- Producción: 30x–100x (marca, soporte, parches urgentes)

Visualízalo: cada día sin detectar un defecto crítico lo “capitaliza” (crece su costo).

### 4. Síntomas de Proyecto “No Testeado” 🚨

- Commits grandes y nocturnos (“arreglé varias cosas”).
- “Funciona en mi máquina”.
- Bugs que vuelven (regresiones circulares).
- Deuda técnica invisible (nadie se atreve a tocar módulos viejos).
- Issue tracker lleno de reproducir-pedir-clarificar.

### 5. Síntomas de Proyecto “Saludable” 🩺

- Commits pequeños + mensajes claros.
- Integración frecuente (pull/push diario).
- Refactors acompañados de tests que validan.
- Defectos nuevos: se aíslan rápido y generan tests adicionales.
- Métricas mínimas visibles (build status verde).

### 6. Matriz de Riesgo Simplificada 🎯

| Módulo           | Impacto si falla | Cambia seguido | ¿Debe priorizar tests?  |
| ---------------- | ---------------- | -------------- | ----------------------- |
| Autenticación    | Alto             | Medio          | Sí (unit + integración) |
| Reportes PDF     | Medio            | Bajo           | Cobertura básica        |
| Envío Email      | Medio            | Alto           | Tests + mocks           |
| Página Marketing | Bajo             | Alto           | Manual + smoke ligero   |

Enfoque: primero Alta combinación (Impacto Alto + Cambios Frecuentes).

### 7. Mini Auto‑Diagnóstico (3 preguntas) 🔍

Responde S / N:

1. ¿Puedo modificar una función y saber en <30s si rompí algo?
2. ¿Cada bug corregido genera al menos 1 test nuevo?
3. ¿La mayoría de defectos se detectan antes de producción?

Resultados:

- 3 “Sí”: Buen camino.
- 1–2 “Sí”: Riesgo medio → priorizar suite base.
- 0 “Sí”: Urgente establecer pruebas unitarias mínimas.

### 8. Ejemplo Ilustrativo (Función de cálculo impuestos) 🧪

Escenario:

- Versión sin tests: cambio tasa IVA; se rompe cálculo descuentos acumulados (nadie lo nota 3 semanas).
- Versión con tests: suite falla al cambiar tasa; ajustas lógica en minutos.

Mensaje: Los tests no evitan pensar, evitan olvidar.

### 9. Mitos Comunes 🧵

| Mito                                  | Realidad                                  |
| ------------------------------------- | ----------------------------------------- |
| “Quita tiempo”                        | Ahorra tiempo neto al reducir re-trabajo  |
| “Solo para proyectos grandes”         | Es lo que permite que crezcan             |
| “El QA se encarga”                    | Calidad es responsabilidad colectiva      |
| “100% cobertura = perfecto”           | Métrica complementaria, no objetivo único |
| “Primero terminamos, luego testeamos” | “Luego” casi nunca llega                  |

### 10. Estrategia de Entrada (lo que haremos en el módulo) 🛠️

1. Semana 1–2: Base de tests unitarios (Jest) en funciones puras.
2. Semana 3: Integración ligera (módulos que colaboran).
3. Semana 4: Introducción a pruebas de sistema controladas.
4. Continuo: Añadir test por cada bug detectado (anti-regresión).

### 11. Actividad Rápida (5 min) ✍️

En parejas: Elegir un módulo hipotético (ej: carrito, login, pagos). Listar:

- 2 riesgos (qué podría fallar y dolería).
- 2 tests mínimos que mitigarían cada riesgo.
  Compartir 1 ejemplo al grupo.

### 12. Frase Ancla 🧠

“Software sin tests no es ‘más rápido’; solo difiere el momento en que pagas el costo.”

## Casos Reales: Fallos (y un éxito) Famosos 🛰️💥

> Objetivo: ver impacto real de defectos y qué práctica de calidad/testing faltó (o funcionó).

### 1. Ariane 5 – Vuelo 501 (1996) 🚀

- Contexto: Cohete europeo (primera misión).
- Fallo: Conversión de un número de 64 bits a 16 bits → overflow → apagado de la unidad inercial → autodestrucción.
- Causa raíz: Reuso de código de Ariane 4 sin validar nuevas condiciones de velocidad horizontal.
- Qué faltó: Testing / simulaciones con perfiles reales de vuelo de Ariane 5 + manejo de errores seguro.
- Lección: Reuso ≠ copiar y pegar; validar supuestos en nuevo contexto.

### 2. Mars Climate Orbiter (1999) 🪐

- Fallo: Pérdida de la sonda (se desintegró en la atmósfera marciana).
- Causa: Mezcla de unidades (libras‑fuerza vs newtons) entre equipos (imperial vs métrico).
- Qué faltó: Validaciones automáticas de unidades + pruebas de integración entre subsistemas de navegación.
- Lección: “Pequeñas” inconsistencias de datos destruyen proyectos multimillonarios.

### 3. Therac‑25 (1985–87) ☢️

- Fallo: Múltiples sobredosis de radiación a pacientes.
- Causas: Concurrencia/race conditions, falta de interlocks hardware, confianza excesiva en software “optimizado”.
- Qué faltó: Testing de estrés concurrente, análisis formal, validación independiente de seguridad.
- Lección: En sistemas críticos, pruebas negativas y de condiciones de carrera son obligatorias.

### 4. Knight Capital (2012) 💸

- Fallo: Algoritmo bursátil fuera de control → pérdidas ≈ 440 M USD en 45 minutos.
- Causa: Código antiguo reactivado en algunos servidores + despliegue inconsistente.
- Qué faltó: Pruebas de despliegue, feature flags controlados, entorno staging representativo.
- Lección: Testing también incluye proceso de release; consistencia ambiental es crítica.

### 5. Heartbleed (2014) 🔓

- Fallo: Vulnerabilidad en OpenSSL permitía leer memoria sensible.
- Causa: Falta de pruebas que cubrieran límites y validación de longitud declarada vs real.
- Qué faltó: Tests de seguridad (fuzzing), revisión de código exhaustiva en paths críticos.
- Lección: Casos borde y validación de parámetros no son opcionales en librerías base.

### 6. Apollo 11 “1201 / 1202” (1969) ✅ (Éxito por buen diseño)

- Evento: Alarmas de sobrecarga de la computadora de abordo durante alunizaje.
- Causa: Entrada extra de radar saturó ciclos de CPU.
- Qué funcionó: Sistema priorizaba tareas críticas y descartaba las no esenciales (testing + diseño de prioridades).
- Lección: Calidad no solo evita fallos; prepara al sistema para fallar con gracia (resiliencia).

### Patrones Repetidos 🔁

| Patrón                              | Ejemplos       | Práctica que faltó                  |
| ----------------------------------- | -------------- | ----------------------------------- |
| Supuestos no reevaluados            | Ariane 5       | Pruebas con nuevos perfiles         |
| Integración deficiente              | Mars Orbiter   | Validación de interfaces / unidades |
| Concurrencia ignorada               | Therac‑25      | Tests de carrera / análisis formal  |
| Release caótico                     | Knight Capital | Pipeline controlado / rollback      |
| Validación insuficiente de entradas | Heartbleed     | Tests de límites / fuzzing          |

### Lecciones Transversales 📌

1. Reuso exige revalidar supuestos.
2. Datos / unidades deben ser verificados automáticamente.
3. Testing de “casos felices” no basta: hay que buscar fallos.
4. Automatización del proceso de despliegue reduce riesgos humanos.
5. Diseño + pruebas orientadas a resiliencia salvan misiones (Apollo 11).

### Actividad Rápida (5 min) ✍️

Elige 1 caso: escribe (a) riesgo principal, (b) test o control que lo habría detectado antes. Compartir.

Frase ancla: “Los fallos famosos no son magia: son supuestos sin test que llegaron a producción.”
