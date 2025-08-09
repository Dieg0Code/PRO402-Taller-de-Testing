# 📚 Clase 02: Pruebas de sistema, verificación vs validación y Conceptos de Pruebas Automatizadas

- Unidad 1: **Taller de Calidad y Testing de Software**
- Fecha: Martes 12 de Agosto, 2025
- Horario: 15:50 - 18:10
- Docente: Diego Obando

## 🎯 Objetivos de la Clase

Al finalizar la clase, serás capaz de:

- Comprender la diferencia entre verificación y validación.
- Identificar los tipos de pruebas de sistema y su importancia.
- Conocer los conceptos básicos de pruebas automatizadas y su implementación.

## 📖 Contenidos

- Verificación vs Validación
- Pruebas de Sistema
- Introducción a las Pruebas Automatizadas

## 📚 Verificación vs Validación

### 1. Definiciones Clave 🧭

- **Verificación (¿Construimos el producto correctamente?)**  
  Actividades para comprobar que cada artefacto (requisitos, diseño, código) cumple con las especificaciones establecidas. Se centra en la CONSISTENCIA interna.
- **Validación (¿Construimos el producto correcto?)**  
  Actividades para confirmar que el software satisface necesidades reales del usuario/negocio en su contexto. Se centra en la ADECUACIÓN al uso.

> Mnemonic: Verificación = “Checklists”. Validación = “Usuarios”.

### 2. Comparativa Rápida ⚖️

| Aspecto         | Verificación 🛠️                                                                  | Validación 👥                                                           |
| --------------- | -------------------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| Pregunta        | ¿Correcto según especificación?                                                  | ¿Útil y correcto para el usuario?                                       |
| Momento         | Durante el desarrollo (iterativa)                                                | Al final de un ciclo / antes de liberar                                 |
| Quién participa | Devs, QA técnico                                                                 | Usuarios, negocio, QA funcional                                         |
| Ejemplos        | Revisión de código, inspección de requisitos, análisis estático, tests unitarios | Pruebas de aceptación, pruebas beta, pruebas exploratorias con usuarios |
| Enfoque         | Prevención                                                                       | Aceptación / Ajuste                                                     |
| Artefactos base | Documentos y código                                                              | Casos de uso reales, escenarios de negocio                              |

### 3. Ejemplo Integrado (Funcionalidad: Registro de Usuario) 🧪

| Paso                                                                         | Acción                 | Tipo         |
| ---------------------------------------------------------------------------- | ---------------------- | ------------ |
| Revisar que el requisito “contraseña mínima 8 caracteres” esté escrito claro | Revisión de requisitos | Verificación |
| Code review del módulo hashPassword()                                        | Peer review            | Verificación |
| Test unitario: hash no igual a texto plano                                   | Test unitario          | Verificación |
| Test de integración: flujo POST /register crea usuario y envía email         | Integración            | Verificación |
| Usuario final prueba registro en entorno preproducción con datos reales      | UAT                    | Validación   |
| Se detecta que el mensaje de éxito es confuso para usuarios                  | Feedback negocio       | Validación   |

### 4. Errores Comunes 🚨

- Creer que “pasar todos los tests” = producto validado.
- Saltarse validación y recibir rechazo tardío del cliente.
- Hacer “validación” con el mismo equipo que diseñó (sesgo).
- No versionar criterios de aceptación (cambian y se pierde trazabilidad).

### 5. Relación con la Pirámide de Pruebas 🧱

- Base (unitarios/integración): predominio de verificación.
- Capas superiores (sistema / aceptación): foco creciente en validación.
- Necesitamos ambas: solo verificación → software “correcto” que nadie quiere; solo validación → descubrimos tarde defectos técnicos.

### 6. Mini Actividad (3 min) ✍️

Para cada ítem di V (verificación) o VA (validación):

1. Cliente revisa si el flujo de pago refleja impuestos locales.
2. Linter report detecta variables no usadas.
3. QA funcional ejecuta caso “recuperar contraseña” con correo real.
4. Equipo hace revisión de arquitectura para asegurar estándares internos.

(Resolver en voz / pizarra y justificar una respuesta que genere duda.)

### 7. Checklist Práctico ✅

Antes de decir “listo para validar”:

- [ ] Requisitos revisados (sin ambigüedades críticas)
- [ ] Cobertura de tests básicos aceptable
- [ ] Errores de lint y build resueltos
- [ ] Entorno estable y datos semilla listos
- [ ] Criterios de aceptación documentados

### 8. Frase Resumen 🧠

Verificar es al “cómo” técnico lo que validar es al “para qué” del usuario.

## Pruebas de Sistema

### 1. ¿Qué son? 🧩

Ejecución de pruebas sobre el **sistema completo integrado** (todas las piezas juntas) para verificar que cumple requisitos funcionales y algunos no funcionales básicos (flujos, datos, mensajes, estados). Responden: “¿Las funcionalidades trabajan bien de extremo a extremo bajo condiciones realistas?”

### 2. Alcance 🔍

Incluye: API + lógica + persistencia + configuraciones + integración con servicios internos simulados (externos reales solo si es ambiente controlado).  
Excluye: detalles internos de funciones (eso es unidad) y feedback final del usuario (eso es aceptación).

### 3. Entradas / Salidas ⚙️

| Elemento                | Ejemplos                                                                       |
| ----------------------- | ------------------------------------------------------------------------------ |
| Entradas                | Requisitos funcionales, criterios de aceptación, casos de uso, modelo de datos |
| Artefactos generados    | Casos de prueba E2E, evidencias (capturas/logs), reporte de defectos           |
| Oráculos (qué comparar) | Respuesta HTTP, cambios en BD, correos enviados (simulados), logs              |

### 4. Tipos comunes dentro de “Sistema” 🗂️

- Funcionales end‑to‑end (flujo completo: registro → login → acción).
- De regresión (conjunto estable tras cada release).
- Smoke / sanity (subset rápido: “el sistema respira”).
- Configuración / despliegue (variables de entorno correctas, rutas accesibles).
- Básicas no funcionales iniciales (tiempo respuesta simple, tamaño payload).

### 5. Ejemplo (Aplicación de Cursos) 🎓

Flujo: “Estudiante se registra a un curso pago”.

1. Precondición: Curso “JS-101” existe con cupos.
2. Pasos: (a) Registrar usuario, (b) Login, (c) Seleccionar curso, (d) Confirmar inscripción.
3. Verificaciones:
   - HTTP 201 al crear usuario, hash password ≠ texto.
   - En BD: registro en tabla inscripciones con estado “pendiente”.
   - Email simulado (mock SMTP) generado.
   - Cupos decrementan en 1.
4. Resultado esperado: Estado final “inscrito”.

### 6. Estrategia mínima para el curso 🧭

Semana 2–3:

- Definir “smoke list” (5–7 flujos principales).
- Automatizar progresivamente algunos como pruebas de integración de alto nivel (no UI gráfica aún).
- Mantener datos de prueba semilla (reset reproducible).

### 7. Diferencias: Unidad vs Integración vs Sistema 🔄

| Aspecto     | Unidad           | Integración          | Sistema                      |
| ----------- | ---------------- | -------------------- | ---------------------------- |
| Aislamiento | Máximo (mocks)   | Parcial              | Mínimo (real)                |
| Velocidad   | Muy alta         | Media                | Más lenta                    |
| Objetivo    | Correcto interno | Colaboración módulos | Flujo completo y requisitos  |
| Fragilidad  | Baja             | Media                | Alta si no se diseña estable |

### 8. Datos de Prueba 🗃️

Principios:

- Reutilizables: script para poblar / limpiar (seed + reset).
- Representativos: incluir casos límite (cupo=1, usuario duplicado).
- Desacoplados de datos personales reales (ficticios siempre).
  Formato sugerido: carpeta /data con JSON semilla.

### 9. Ambientes 🌐

| Ambiente           | Uso                   | Riesgo si falta             |
| ------------------ | --------------------- | --------------------------- |
| DEV                | Desarrollo diario     | Mezcla parcial de código    |
| TEST / QA          | Pruebas de sistema    | Datos inconsistentes        |
| STAGING (opcional) | Ensayo pre‑producción | Saltar validaciones finales |
| PROD               | Real                  | No es para experimentar     |

Para la asignatura: trabajaremos con un ambiente local (simulando TEST) + más adelante integración remota simple.

### 10. Errores frecuentes ⚠️

- Duplicar casos (mismo flujo con texto distinto).
- Tests de sistema demasiado dependientes del momento del día.
- No controlar estado inicial → falsos positivos/negativos.
- Probar “todo” en un solo caso gigante (difícil de diagnosticar).
- Usar credenciales reales (riesgo privacidad).

### 11. Buenas prácticas ✅

- Nombrar casos por objetivo: ST_REGISTRO_USUARIO_OK.
- 1 flujo principal + variaciones separadas (ej: contraseña corta).
- Evidencia automática: logs guardados / capturas si UI (más adelante).
- Definir criterio “pasa/falla” claro antes de ejecutar.
- Mantener suite smoke < 5 min.

### 12. Mini Actividad (5 min) ✍️

Diseña esquema (sin código) de un test de sistema para “Recuperar contraseña”:
Incluye: precondición, pasos, verificaciones y datos clave. Compartir 1 ejemplo en voz.

### 13. Checklist antes de ejecutar suite de sistema 📋

- [ ] Base de datos reseteada / datos conocidos.
- [ ] Variables de entorno cargadas (.env ejemplo).
- [ ] Servicios dependientes simulados o disponibles.
- [ ] Logs limpios (fácil detectar nuevo error).
- [ ] Lista de casos priorizada (crit → opt).

### 14. Métrica inicial sugerida 📊

Tiempo total suite smoke / Nº de defectos reales detectados / Nº falsos positivos → Usar para ajustar cobertura.

### 15. Frase memoria 🧠

“Prueba de sistema = realidad controlada: todo junto, pero bajo un guión verificable.”

> Siguiente sección: Introducción a las Pruebas Automatizadas (por qué, qué NO automatizar primero, y vistazo a Jest).

## Introducción a las Pruebas Automatizadas

### 0. Panorama Rápido 🗺️

Automatizar = convertir verificaciones repetibles (entradas, ejecución, comparación con esperado) en scripts que corren solos y entregan un veredicto (pasa / falla) consistente y rápido.

### Conceptos Clave (Glosario Inicial) 🔑

| Término                   | Explicación breve                                                                                    |
| ------------------------- | ---------------------------------------------------------------------------------------------------- |
| Test Runner               | Herramienta que localiza, ejecuta y reporta tests (Jest).                                            |
| Suite                     | Grupo de tests relacionados (bloque describe).                                                       |
| Caso de prueba            | Escenario individual (bloque test / it).                                                             |
| Aserción (assert)         | Verificación: expect(valor).matcher(esperado).                                                       |
| Matcher                   | Método que compara (toBe, toEqual, toThrow, etc.).                                                   |
| Fixture                   | Datos / estado inicial controlado para un test.                                                      |
| Mock                      | Objeto/función simulada que reemplaza dependencia real (controla comportamiento + captura llamadas). |
| Stub                      | Versión mínima que devuelve respuestas predefinidas (no siempre inspeccionada).                      |
| Spy                       | Observa/espía una función real (registra llamadas) sin reemplazar lógica (o con envoltorio).         |
| Cobertura (coverage)      | % de código ejecutado por tests (líneas, ramas, funciones).                                          |
| Flaky Test                | Test que a veces pasa y a veces falla sin cambios de código (inestable).                             |
| Determinismo              | Misma entrada → mismo resultado siempre (ideal para tests).                                          |
| Watch Mode                | Re-ejecuta tests al guardar archivos.                                                                |
| CI (Integración Continua) | Servidor que ejecuta tests automáticamente en cada cambio (pipeline).                                |

### Manual vs Automatizado ⚖️

| Aspecto            | Manual                          | Automatizado               |
| ------------------ | ------------------------------- | -------------------------- |
| Velocidad          | Lenta, depende de la persona    | Rápida y paralelizable     |
| Consistencia       | Variable (cansancio, omisiones) | Repetible idéntico         |
| Escalabilidad      | Se vuelve costoso               | Escala con infraestructura |
| Costo inicial      | Bajo                            | Mayor (config + escribir)  |
| Detección temprana | Limitada                        | Alta (cada commit)         |

### Flujo Típico (Ciclo Simplificado) 🔄

1. Especificar comportamiento esperado (qué debe pasar).
2. Escribir test (rojo: falla).
3. Implementar / ajustar código (verde: pasa).
4. Refactor (mantener verde).
5. Integrar a CI (verificar en cada push).
6. Monitorear: eliminar flaky, revisar cobertura relevante (no perseguir 100% ciego).

```
Especificación → Test rojo → Implementación → Test verde → Refactor → CI
```

### Buen Alcance Inicial ✅

- Funciones puras (sin red, sin fechas no controladas).
- Reglas de negocio con condiciones.
- Utilidades críticas (cálculos, validaciones).
  (No iniciar por UI compleja o integraciones externas inestables.)

### Antipatrones Tempranos ❌

- Test duplicado (misma verificación con distinto texto).
- Test que solo hace console.log (sin expect).
- Aserciones múltiples sin relación (dificulta causa raíz).
- Uso de tiempos (setTimeout largo) para “esperar” algo en vez de simularlo.

### 1. ¿Qué es una prueba automatizada? ⚙️

Script que ejecuta código de la aplicación con entradas controladas y verifica salidas (asserts) de forma repetible sin intervención humana.

### 2. ¿Por qué automatizar? 🎯

- Repetibilidad (mismo resultado hoy y mañana).
- Velocidad (segundos vs minutos manuales).
- Detección temprana de regresiones.
- Documentación viva del comportamiento.
- Base para Integración Continua (CI).

### 3. ¿Qué NO automatizar primero? 🚫

- Flujos UI inestables / en constante cambio.
- Casos extremadamente raros (baja frecuencia + alto costo).
- Pruebas que dependen de servicios externos sin mocks.
- Rendimiento profundo (requiere tooling específico).

Empieza por: funciones puras críticas + flujos “felices” (happy path) de negocio.

### 4. Criterios de selección inicial ✅

| Pregunta                                       | Si “Sí” → Mejor candidato |
| ---------------------------------------------- | ------------------------- |
| ¿Corre rápido?                                 | ✔                         |
| ¿Se usa mucho?                                 | ✔                         |
| ¿Romperlo causa daño visible?                  | ✔                         |
| ¿Tiene lógica (condiciones) que puede cambiar? | ✔                         |

### 5. ROI simplificado 💰

Costo inicial alto (escribir + configurar), pero coste marginal ≈ 0 por cada re-ejecución. Manual: coste lineal cada vez. Punto de equilibrio cuando las repeticiones superan el tiempo de creación.

### 6. Dónde encaja en la pirámide 🧱

- Base automatizada: unitarios + integración ligera.
- Media: pruebas de sistema automatizadas (selectivas).
- Pico mínimo: UI end‑to‑end críticos (checkout, login).

### 7. Estructura típica (Jest) 🧪

(No instalamos aún, solo concepto.)

```javascript
// archivo: suma.test.js
describe("suma()", () => {
  test("suma dos números positivos", () => {
    expect(suma(2, 3)).toBe(5);
  });

  test("suma con cero", () => {
    expect(suma(7, 0)).toBe(7);
  });
});
```

Palabras clave:

- describe: agrupa casos.
- test / it: define un caso.
- expect(...).matcher: aserción (toBe, toEqual, etc.).

### 8. Buenas prácticas iniciales 🧭

- 1 idea por test (un assert principal claro).
- Nombres expresivos: “debería …”.
- Evitar dependencias entre tests.
- Preparar datos dentro del test (o helpers simples).
- Mantener tests rápidos (< 200 ms cada uno en esta etapa).

### 9. Errores frecuentes al empezar ⚠️

- Tests que dependen del orden de ejecución.
- Olvidar el assert (el test siempre “pasa”).
- Verificar demasiadas cosas a la vez.
- Confundir lógica de producción dentro del test (duplicas bugs).

### 10. Mini Showcase (conceptual) 🔍

Función objetivo:

```javascript
// src/esPar.js
function esPar(n) {
  if (typeof n !== "number") throw new Error("Tipo inválido");
  return n % 2 === 0;
}
module.exports = esPar;
```

Test pensado:

```javascript
// tests/esPar.test.js
const esPar = require("../src/esPar");

describe("esPar", () => {
  test("true para número par", () => {
    expect(esPar(4)).toBe(true);
  });
  test("false para número impar", () => {
    expect(esPar(7)).toBe(false);
  });
  test("lanza error para string", () => {
    expect(() => esPar("4")).toThrow("Tipo inválido");
  });
});
```

Conceptos: caso normal, borde, error.

### 11. Actividad Rápida (5 min) ✍️

Diseña en papel los casos (solo títulos) para testear una función `calcularDescuento(precio, porcentaje)`:

- Lista mínima de 4 casos (incluye error/validación).
- Elegir 1 como “prioridad alta” y justificar.

### 12. Checklist previa a automatizar 🧾

- [ ] Función estable (no cambia cada hora).
- [ ] Requisitos claros (resultado esperado definido).
- [ ] Entradas y salidas deterministas.
- [ ] No depende de red / tiempo real sin control.

Frase cierre: “Automatizar temprano lo estable, manual donde aún exploramos.”
