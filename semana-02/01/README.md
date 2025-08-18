# Clase 01 - Semana 02 - Ciclo de vida del Producto, calidad, fundamentos de DevOps y CI/CD

- Unidad 01: **Calidad y Testing de Software**
- Fecha: Lunes 18 de Agosto, 2025:
- Horario: 15:50 - 18:10
- Docente: Diego Obando

## 📏 1. Métricas de Calidad: Del concepto a la prácticando

## 🎯 Objetivos de la Clase

Al finalizar la clase seras capaz de:

- Integrar estrategias de testing en cada fase del ciclo de vida del desarrollo de software (SDLC).
- Implementar el concepto de "Shift-Left Testing" para mejorar la calidad del producto.
- Comprender las métricas de calidad y quality gates en contextos DevOps.
- Aplicar los fundamentos de DevOps y CI/CD en procesos de testing automatizado.

---

## 📖 Contenidos

### BLOQUE 1: Ciclo de vida del producto y Testing (35 min)

### BLOQUE 2: Calidad en contexto DevOps (35 min)

### BLOQUE 3: DevOps y CI/CD - Fundamentos (40 min)

### BLOQUE 4: Testing en pipelines CI/CD (30 min)

---

# 📦 BLOQUE 1: Ciclo de vida del producto y Testing (35 min)

_"El testing no es una fase, es una mentalidad que debe estar presente en todo el ciclo de vida del producto"_

## 🔄 1. SDLC y Testing: Más allá de los conceptos básicos

Ya conocemos los niveles básicos de testing (unidad, integración, sistema) que vimos la semana pasada. Ahora vamos a **profundizar** en cómo el testing se integra estratégicamente en cada fase del desarrollo.

_SDLC acrónimo de Software Development Life Cycle_ es el proceso que abarca desde la concepción de un producto hasta su despliegue y mantenimiento. En este bloque, veremos cómo el testing no es una fase aislada, sino una actividad que debe estar presente en cada etapa del SDLC.

### 1.1 El Modelo V Extendido 🔀

```
DESARROLLO                    TESTING
┌─────────────────┐          ┌─────────────────┐
│   Requisitos    │ ◄──────► │ Pruebas de      │
│                 │          │ Aceptación      │
├─────────────────┤          ├─────────────────┤
│   Diseño de     │ ◄──────► │ Pruebas de      │
│   Sistema       │          │ Sistema         │
├─────────────────┤          ├─────────────────┤
│   Diseño        │ ◄──────► │ Pruebas de      │
│   Detallado     │          │ Integración     │
├─────────────────┤          ├─────────────────┤
│   Codificación  │ ◄──────► │ Pruebas         │
│                 │          │ Unitarias       │
└─────────────────┘          └─────────────────┘
```

**🔍 Punto clave:** El modelo V muestra cómo cada fase de desarrollo tiene su contraparte en testing, y ambas se planifican **simultáneamente**, no secuencialmente.

**🔍 Punto clave:** Cada fase de desarrollo tiene su contraparte en testing, y ambas se planifican **simultáneamente**, no secuencialmente.

### 1.2 Testing en cada fase del SDLC 📋

| Fase SDLC                  | Actividades de Testing                                                                             | Entregables de Testing                                                                      | Valor Agregado                                               |
| -------------------------- | -------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| **Análisis de Requisitos** | • Revisión de requisitos<br>• Definición de criterios de aceptación<br>• Identificación de riesgos | • Matriz de trazabilidad<br>• Casos de prueba de alto nivel                                 | Detección temprana de ambigüedades y requisitos no testeable |
| **Diseño**                 | • Revisión de arquitectura<br>• Definición de estrategia de testing<br>• Diseño de casos de prueba | • Plan de pruebas<br>• Casos de prueba detallados<br>• Datos de prueba                      | Validación de que el diseño soporta los requisitos           |
| **Implementación**         | • Testing unitario<br>• Revisión de código<br>• Análisis estático                                  | • Suites de pruebas unitarias<br>• Reportes de cobertura<br>• Reportes de análisis estático | Detección de defectos a nivel de código                      |
| **Integración**            | • Pruebas de integración<br>• Pruebas de API<br>• Testing de contratos                             | • Resultados de pruebas de integración<br>• Documentación de interfaces                     | Validación de interacciones entre componentes                |
| **Sistema**                | • Pruebas funcionales<br>• Pruebas no funcionales<br>• Testing de regresión                        | • Resultados de pruebas de sistema<br>• Métricas de rendimiento<br>• Reportes de defectos   | Validación del sistema completo                              |
| **Despliegue**             | • Pruebas de smoke<br>• Pruebas de aceptación<br>• Monitoreo post-despliegue                       | • Reportes de smoke testing<br>• Sign-off de aceptación<br>• Métricas de producción         | Validación en ambiente productivo                            |

## 🏃‍♂️ 2. Shift-Left Testing: La revolución del testing temprano

### 2.1 ¿Qué es Shift-Left Testing?

**Definición:** Estrategia que mueve las actividades de testing hacia las **fases más tempranas** del ciclo de desarrollo.

```
TRADICIONAL:
Requisitos → Diseño → Código → Testing → Despliegue
                              ↑
                         Testing aquí

SHIFT-LEFT:
Requisitos → Diseño → Código → Testing → Despliegue
    ↑         ↑        ↑
Testing desde aquí en todas las fases
```

### 2.2 Los 4 tipos de Shift-Left Testing 🎯

#### Tipo 1: Shift-Left Traditional 📚

- **Qué es:** Comenzar el diseño de pruebas durante las fases de requisitos y diseño
- **Cuándo:** Proyectos con metodologías tradicionales (Waterfall, V-Model)
- **Ejemplo práctico:**
  ```
  Requisito: "El usuario debe poder cambiar su contraseña"
  Testing temprano:
  ✅ ¿Qué validaciones debe tener la nueva contraseña?
  ✅ ¿Cómo se notifica al usuario del cambio exitoso?
  ✅ ¿Qué pasa si falla el cambio?
  ```

#### Tipo 2: Shift-Left Incremental 🔄

- **Qué es:** Testing continuo en cada iteración/sprint
- **Cuándo:** Metodologías ágiles (Scrum, Kanban)
- **Ejemplo práctico:**
  ```
  Sprint Planning:
  - Historia de usuario definida
  - Criterios de aceptación claros
  - Casos de prueba diseñados
  - Definition of Done incluye testing
  ```

#### Tipo 3: Shift-Left Agile/DevOps 🚀

- **Qué es:** Developers escriben y ejecutan sus propias pruebas
- **Cuándo:** Equipos DevOps maduros
- **Ejemplo práctico:**
  ```javascript
  // Developer escribe test ANTES del código
  test("changePassword should validate minimum length", () => {
    expect(() => changePassword("123")).toThrow("Password too short");
  });
  ```

#### Tipo 4: Shift-Left Model-Based 🧠

- **Qué es:** Uso de modelos para generar automáticamente casos de prueba
- **Cuándo:** Sistemas complejos con modelos formales
- **Ejemplo:** Diagramas de estado que generan automáticamente tests

### 2.3 Beneficios del Shift-Left Testing 📈

| Beneficio                | Sin Shift-Left            | Con Shift-Left              |
| ------------------------ | ------------------------- | --------------------------- |
| **Costo de defectos**    | Alto (encontrados tarde)  | Bajo (encontrados temprano) |
| **Tiempo de feedback**   | Días/semanas              | Minutos/horas               |
| **Calidad del código**   | Reactiva                  | Proactiva                   |
| **Cobertura de testing** | Limitada por tiempo       | Integral desde el inicio    |
| **Colaboración equipo**  | Testing como "gatekeeper" | Testing como enabler        |

### 2.4 Implementación práctica de Shift-Left 🛠️

#### Checklist para implementar Shift-Left:

**En la fase de Requisitos:**

- [ ] Cada requisito tiene criterios de aceptación claros y testeables
- [ ] Se han identificado casos edge y escenarios negativos
- [ ] Existe trazabilidad entre requisitos y casos de prueba

**En la fase de Diseño:**

- [ ] La arquitectura considera la testabilidad (dependency injection, etc.)
- [ ] Se han definido interfaces claras para facilitar mocking
- [ ] Existe una estrategia de datos de prueba

**En la fase de Desarrollo:**

- [ ] Developers escriben unit tests antes o durante el desarrollo
- [ ] Code reviews incluyen revisión de tests
- [ ] CI/CD ejecuta automáticamente las pruebas en cada commit

## 🔄 3. Testing Continuo vs Testing Tradicional

### 3.1 Comparativa detallada

| Aspecto             | Testing Tradicional            | Testing Continuo                    |
| ------------------- | ------------------------------ | ----------------------------------- |
| **Momento**         | Fase dedicada post-desarrollo  | Integrado en todo el ciclo          |
| **Frecuencia**      | Lotes grandes, menos frecuente | Pequeños incrementos, muy frecuente |
| **Feedback**        | Al final del ciclo             | Inmediato                           |
| **Automatización**  | Limitada                       | Extensiva                           |
| **Responsabilidad** | Equipo de QA separado          | Todo el equipo                      |
| **Métricas**        | Defectos encontrados           | Defectos prevenidos                 |

### 3.2 El flujo del Testing Continuo 🌊

```
Código → Build → Unit Tests → Integration Tests → Deploy to Test →
System Tests → Performance Tests → Security Tests → Deploy to Prod →
Monitor → Feedback → Código (nuevo ciclo)
```

**🎯 Punto clave:** En testing continuo, cada cambio de código activa automáticamente una serie de validaciones que proporcionan feedback inmediato.

## 💡 Ejercicio Práctico (10 min)

**Escenario:** Tu equipo está desarrollando una aplicación de e-commerce.

**Requisito nuevo:** "Implementar sistema de descuentos por código promocional"

**Tarea en grupos (3-4 personas):**

1. Identifica en qué fases del SDLC aplicarías testing
2. Define 3 actividades de Shift-Left Testing para este requisito
3. Diseña 2 casos de prueba que escribirías ANTES de programar

**Tiempo:** 7 minutos de discusión + 3 minutos de puesta en común

---

## 🔚 Resumen BLOQUE 1

**Conceptos clave cubiertos:**
✅ SDLC extendido con testing integrado
✅ 4 tipos de Shift-Left Testing
✅ Testing continuo vs tradicional
✅ Implementación práctica

**Para el siguiente bloque:**
🎯 Métricas de calidad y quality gates en DevOps

---

# 📊 BLOQUE 2: Calidad en contexto DevOps (35 min)

_"No puedes mejorar lo que no puedes medir, pero las métricas sin acción son solo números bonitos"_

## 📚 Glosario de Términos Clave

Antes de profundizar, definamos los conceptos y acrónimos que usaremos:

| Término/Acrónimo          | Definición                                                                                                                        | Ejemplo                                                            |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| **DevOps**                | Development + Operations. Cultura y prácticas que combinan desarrollo y operaciones para entregar software más rápido y confiable | Equipos que despliegan código varias veces al día                  |
| **CI/CD**                 | Continuous Integration / Continuous Deployment. Automatización del proceso de integración y despliegue de código                  | GitHub Actions que ejecuta tests automáticamente en cada push      |
| **DORA**                  | DevOps Research and Assessment. Organización que define las 4 métricas clave de rendimiento DevOps                                | Las métricas que miden qué tan bien funciona tu equipo             |
| **MTTR**                  | Mean Time To Recovery. Tiempo promedio para recuperarse de un fallo en producción                                                 | Si el sistema falla, ¿cuánto tardamos en arreglarlo?               |
| **SLA/SLO**               | Service Level Agreement/Objective. Acuerdos sobre nivel de servicio esperado                                                      | "El sistema debe estar disponible 99.9% del tiempo"                |
| **Lead Time**             | Tiempo desde que se hace un commit hasta que llega a producción                                                                   | Desde que escribes código hasta que los usuarios lo usan           |
| **Technical Debt**        | Costo de refactorización necesaria por tomar atajos en el desarrollo                                                              | Código mal escrito que funciona pero es difícil de mantener        |
| **Quality Gate**          | Punto de control automatizado que bloquea código que no cumple criterios de calidad                                               | "No pasa a producción si tiene menos de 80% de cobertura de tests" |
| **Mutation Testing**      | Técnica que introduce errores artificiales en el código para probar la calidad de los tests                                       | Si cambio un ">" por "<", ¿mis tests detectan el error?            |
| **Code Coverage**         | Porcentaje del código que es ejecutado por las pruebas automatizadas                                                              | "Mis tests ejecutan el 85% de las líneas de código"                |
| **Cyclomatic Complexity** | Métrica que mide la complejidad del código basado en el número de caminos independientes                                          | Una función con muchos `if` y `loops` tiene alta complejidad       |
| **Feedback Loop**         | Tiempo que tarda en llegar información sobre si algo funciona bien o mal                                                          | Desde que haces un cambio hasta que sabes si funcionó              |

## 📏 1. Métricas de Calidad: Del concepto a la práctica

Ya sabemos que la calidad es importante. Ahora necesitamos **medirla**, **monitorearla** y **actuar** basados en datos concretos.

### 1.1 Pirámide de Métricas de Calidad 🏗️

```mermaid
graph TD
    A[📊 Métricas de Negocio] --> B[📈 Métricas de Producto]
    B --> C[⚙️ Métricas de Proceso]
    C --> D[🔧 Métricas Técnicas]

    A1[User Satisfaction<br/>Revenue Impact<br/>Churn Rate]
    B1[Feature Adoption<br/>Performance<br/>Availability]
    C1[Lead Time<br/>Deploy Frequency<br/>MTTR]
    D1[Code Coverage<br/>Cyclomatic Complexity<br/>Technical Debt]

    A --> A1
    B --> B1
    C --> C1
    D --> D1
```

### 1.2 Métricas Técnicas de Calidad 🔧

#### Métricas de Cobertura

> 💡 **¿Qué es Code Coverage?** Es el porcentaje de código que es ejecutado cuando corren nuestras pruebas. Si tengo 100 líneas de código y mis tests ejecutan 80 líneas, tengo 80% de cobertura.

| Métrica               | Descripción                       | Valor Target | ⚠️ Cuidado                       |
| --------------------- | --------------------------------- | ------------ | -------------------------------- |
| **Line Coverage**     | % líneas ejecutadas por tests     | 70-80%       | Alta cobertura ≠ buenos tests    |
| **Branch Coverage**   | % ramas de condiciones probadas   | 80-90%       | Más importante que line coverage |
| **Function Coverage** | % funciones invocadas             | 90-95%       | Identifica código no utilizado   |
| **Mutation Coverage** | % mutaciones detectadas por tests | 60-70%       | Mide calidad real de los tests   |

**📝 Explicaciones:**

- **Line Coverage:** Si mi función tiene 10 líneas y los tests ejecutan 8, tengo 80% line coverage
- **Branch Coverage:** Si tengo un `if/else` y solo pruebo el `if`, tengo 50% branch coverage
- **Function Coverage:** Si tengo 5 funciones y solo llamo a 4 en mis tests, tengo 80% function coverage
- **Mutation Coverage:** Cambia automáticamente `>` por `<` en el código. Si mis tests siguen pasando, están mal hechos

#### Métricas de Complejidad

> 💡 **¿Qué es Complejidad de Código?** Es qué tan difícil es entender, modificar y mantener el código. Código complejo = más bugs y más tiempo de desarrollo.

| Métrica                   | Descripción                            | Valor Target              | Acción si excede          |
| ------------------------- | -------------------------------------- | ------------------------- | ------------------------- |
| **Cyclomatic Complexity** | Número de caminos independientes       | < 10 por función          | Refactorizar función      |
| **Cognitive Complexity**  | Dificultad mental para entender código | < 15 por función          | Simplificar lógica        |
| **Depth of Inheritance**  | Niveles de herencia                    | < 5 niveles               | Revisar diseño OO         |
| **Lines of Code (LOC)**   | Líneas por función/clase               | < 50 función, < 500 clase | Dividir responsabilidades |

**📝 Explicaciones:**

- **Cyclomatic Complexity:** Cuenta `if`, `while`, `for`, `case`. Una función con 3 `if` tiene complexity ≈ 4
- **Cognitive Complexity:** Mide esfuerzo mental. Nested loops y condiciones suman más puntos
- **Depth of Inheritance:** Clase A → Clase B → Clase C = profundidad 3
- **LOC:** Simplemente cuenta líneas. Funciones largas son difíciles de entender

### 1.3 DORA Metrics: Las 4 métricas clave de DevOps 🎯

```mermaid
graph LR
    subgraph "📊 DORA Metrics"
        A[⚡ Deployment<br/>Frequency]
        B[📈 Lead Time<br/>for Changes]
        C[🛠️ Mean Time<br/>to Recovery]
        D[❌ Change Failure<br/>Rate]
    end

    subgraph "🏆 Elite Performance"
        A1[Multiple deploys<br/>per day]
        B1[< 1 hour]
        C1[< 1 hour]
        D1[0-15%]
    end

    A --> A1
    B --> B1
    C --> C1
    D --> D1
```

#### Detalle de DORA Metrics:

**1. Deployment Frequency (Frecuencia de Despliegue)**

- **Qué mide:** ¿Con qué frecuencia desplegamos código a producción?
- **Por qué importa:** Indica la capacidad del equipo para entregar valor
- **Niveles de performance:**
  - 🏆 Elite: Multiple deploys per day
  - 🥇 High: Between once per day and once per week
  - 🥈 Medium: Between once per week and once per month
  - 🥉 Low: Between once per month and once every 6 months

**2. Lead Time for Changes (Tiempo desde commit hasta producción)**

- **Qué mide:** ¿Cuánto tiempo tarda un cambio en llegar a producción?
- **Por qué importa:** Mide la eficiencia del pipeline de desarrollo
- **Cómo mejorar:** Automatización, CI/CD, reducir batch size

**3. Mean Time to Recovery (MTTR)**

- **Qué mide:** ¿Cuánto tiempo tomamos en recuperarnos de un fallo?
- **Por qué importa:** Indica la resilencia y capacidad de respuesta
- **Cómo mejorar:** Monitoring, alertas, rollback automático

**4. Change Failure Rate**

- **Qué mide:** ¿Qué % de deploys resultan en fallo en producción?
- **Por qué importa:** Indica la calidad de nuestros procesos de testing
- **Ejemplo práctico:** De 10 veces que subimos código, ¿cuántas veces algo se rompe?
- **Cómo mejorar:** Mejor testing, feature flags, canary deployments

> 💡 **¿Qué son Feature Flags?** Son interruptores en el código que permiten activar/desactivar funcionalidades sin redesplegar. Como un switch de luz para funciones del software.

> 💡 **¿Qué es Canary Deployment?** Es desplegar la nueva versión solo para un pequeño porcentaje de usuarios primero. Si funciona bien, se despliega para todos.

## 🚪 2. Quality Gates: Los guardianes de la calidad

### 2.1 ¿Qué son los Quality Gates?

**Definición:** Puntos de control automatizados que **bloquean** el avance del código si no cumple criterios de calidad predefinidos.

> 💡 **Analogía:** Es como un control de seguridad en el aeropuerto. Si no cumples los requisitos, no pasas. En software, si el código no cumple estándares de calidad, no avanza al siguiente ambiente.

```mermaid
graph LR
    A[Developer<br/>Commit] --> B{Quality Gate 1<br/>Unit Tests}
    B -->|✅ Pass| C{Quality Gate 2<br/>Code Quality}
    B -->|❌ Fail| A
    C -->|✅ Pass| D{Quality Gate 3<br/>Integration Tests}
    C -->|❌ Fail| A
    D -->|✅ Pass| E{Quality Gate 4<br/>Security Scan}
    D -->|❌ Fail| A
    E -->|✅ Pass| F[Deploy to<br/>Staging]
    E -->|❌ Fail| A
```

### 2.2 Configuración de Quality Gates por ambiente 🎚️

#### Quality Gate - Development

```yaml
# Ejemplo configuración SonarQube
sonar.qualitygate.wait=true
conditions:
  - Coverage > 80%
  - Duplicated Lines < 3%
  - Maintainability Rating = A
  - Reliability Rating = A
  - Security Rating = A
  - New Code Coverage > 85%
```

#### Quality Gate - Production

```yaml
# Más estricto para producción
conditions:
  - Coverage > 90%
  - Duplicated Lines < 1%
  - Critical Vulnerabilities = 0
  - High Vulnerabilities < 5
  - Performance Tests Pass = 100%
  - Load Tests Pass = 100%
```

### 2.3 Implementación práctica de Quality Gates 🛠️

> 💡 **Herramientas explicadas:**
>
> - **SonarQube:** Analiza código para encontrar bugs, vulnerabilidades y "code smells" (código que funciona pero está mal escrito)
> - **JaCoCo/Jest:** Herramientas que miden qué porcentaje del código está cubierto por tests
> - **OWASP ZAP:** Herramienta que busca vulnerabilidades de seguridad en aplicaciones web
> - **JMeter/k6:** Herramientas que simulan muchos usuarios usando la aplicación para medir rendimiento

| Etapa Pipeline   | Quality Gate              | Herramienta  | Acción si falla         |
| ---------------- | ------------------------- | ------------ | ----------------------- |
| **Build**        | Compilación exitosa       | Maven/Gradle | Notificar desarrollador |
| **Unit Tests**   | Coverage > 80%            | JaCoCo/Jest  | Bloquear merge          |
| **Code Quality** | No code smells críticos   | SonarQube    | Crear issue automático  |
| **Security**     | No vulnerabilidades altas | OWASP ZAP    | Bloquear despliegue     |
| **Performance**  | Response time < 200ms     | JMeter/k6    | Rollback automático     |

## 🔄 3. Feedback Loops: El corazón de la mejora continua

> 💡 **¿Qué es un Feedback Loop?** Es el tiempo que tarda en llegar información sobre si algo funciona bien o mal. Entre más rápido el feedback, más rápido puedes corregir errores.

### 3.1 Tipos de Feedback Loops

**📝 Explicaciones de tipos de feedback:**

- **IDE Linting:** Tu editor de código te dice inmediatamente si hay errores de sintaxis (líneas rojas)
- **Static Analysis:** Analiza el código sin ejecutarlo para encontrar posibles problemas
- **E2E Tests:** End-to-End, pruebas que simulan un usuario real usando toda la aplicación
- **A/B Testing:** Mostrar dos versiones diferentes a usuarios para ver cuál funciona mejor

### 3.1 Tipos de Feedback Loops

```mermaid
graph TD
    subgraph "⚡ Fast Feedback (< 10 min)"
        A[IDE Linting]
        B[Unit Tests]
        C[Static Analysis]
    end

    subgraph "🚀 Medium Feedback (10-60 min)"
        D[Integration Tests]
        E[Code Quality Gates]
        F[Security Scanning]
    end

    subgraph "🎯 Slow Feedback (1-24 hours)"
        G[E2E Tests]
        H[Performance Tests]
        I[User Acceptance]
    end

    subgraph "📊 Business Feedback (days-weeks)"
        J[User Metrics]
        K[Business KPIs]
        L[A/B Test Results]
    end
```

### 3.2 Principios de Feedback efectivo 📡

#### The 3 R's of Feedback:

1. **Rapid (Rápido):** Feedback inmediato cuando es posible
2. **Relevant (Relevante):** Información específica y accionable
3. **Reliable (Confiable):** Consistente y preciso

#### Implementación práctica:

```javascript
// Ejemplo: Feedback inmediato en IDE
// ESLint + Prettier + TypeScript
{
  "scripts": {
    "lint:fix": "eslint --fix src/",
    "test:watch": "jest --watch --coverage",
    "type:check": "tsc --noEmit"
  },
  "husky": {
    "hooks": {
      "pre-commit": "lint-staged && npm test"
    }
  }
}
```

## 📊 4. Dashboards y Visualización de Métricas

### 4.1 Dashboard de Calidad - Ejemplo estructura

```mermaid
graph TB
    subgraph "🎯 Executive Dashboard"
        A1[DORA Metrics]
        A2[Business KPIs]
        A3[Quality Trends]
    end

    subgraph "👨‍💻 Team Dashboard"
        B1[Test Coverage]
        B2[Build Success Rate]
        B3[Code Quality]
        B4[Deployment Status]
    end

    subgraph "🔧 Technical Dashboard"
        C1[Performance Metrics]
        C2[Error Rates]
        C3[Infrastructure Health]
        C4[Security Vulnerabilities]
    end
```

#### 📋 Explicación detallada de cada Dashboard:

### 🎯 Executive Dashboard (Para directivos y gerentes)

**Propósito:** Vista de alto nivel para tomar decisiones estratégicas

| Métrica            | ¿Qué muestra?                                | Ejemplo práctico                                       | ¿Por qué importa?                                 |
| ------------------ | -------------------------------------------- | ------------------------------------------------------ | ------------------------------------------------- |
| **DORA Metrics**   | Las 4 métricas clave que ya vimos            | "Desplegamos 3 veces por semana, Lead Time de 2 horas" | Mide la eficiencia del equipo de desarrollo       |
| **Business KPIs**  | Métricas de negocio relacionadas con calidad | "Customer satisfaction: 4.2/5, Churn rate: 5%"         | Conecta calidad técnica con resultados de negocio |
| **Quality Trends** | Evolución de la calidad en el tiempo         | "Los bugs en producción bajaron 40% este trimestre"    | Muestra si las inversiones en calidad funcionan   |

### 👨‍💻 Team Dashboard (Para desarrolladores y QA)

**Propósito:** Métricas operativas diarias para el equipo de desarrollo

| Métrica                | ¿Qué muestra?                             | Ejemplo práctico                                  | ¿Cómo actuar?                                  |
| ---------------------- | ----------------------------------------- | ------------------------------------------------- | ---------------------------------------------- |
| **Test Coverage**      | % del código cubierto por pruebas         | "Coverage actual: 78%, objetivo: 80%"             | Si baja del objetivo, agregar más tests        |
| **Build Success Rate** | % de builds que pasan sin errores         | "95% de builds exitosos esta semana"              | Si baja mucho, revisar procesos de development |
| **Code Quality**       | Métricas de SonarQube (bugs, code smells) | "3 bugs críticos, 12 code smells menores"         | Priorizar corrección de issues críticos        |
| **Deployment Status**  | Estado actual de deployments              | "Prod: ✅ Stable, Staging: ⚠️ Deploy in progress" | Visibilidad del estado de ambientes            |

### 🔧 Technical Dashboard (Para DevOps y SRE)

**Propósito:** Monitoreo técnico de sistemas en tiempo real

> 💡 **¿Qué es SRE?** Site Reliability Engineering - Equipos que se encargan de que los sistemas funcionen de manera confiable en producción.

| Métrica                      | ¿Qué muestra?                              | Ejemplo práctico                             | ¿Cuándo alertar?                         |
| ---------------------------- | ------------------------------------------ | -------------------------------------------- | ---------------------------------------- |
| **Performance Metrics**      | Tiempo de respuesta, throughput            | "API response time: 150ms avg, 1200 req/min" | Si response time > 500ms                 |
| **Error Rates**              | % de requests que fallan                   | "Error rate: 0.1% (5 errors/5000 requests)"  | Si error rate > 1%                       |
| **Infrastructure Health**    | CPU, memoria, disco de servidores          | "CPU: 45%, Memory: 67%, Disk: 23%"           | Si CPU > 80% por 5+ minutos              |
| **Security Vulnerabilities** | Vulnerabilidades detectadas en tiempo real | "2 medium vulnerabilities detected"          | Vulnerabilidades críticas inmediatamente |

#### 🎨 Principios de diseño para Dashboards efectivos:

1. **Jerarquía visual:** Lo más importante debe ser más visible
2. **Códigos de color consistentes:** Verde = bien, Amarillo = atención, Rojo = problema
3. **Información accionable:** Cada métrica debe sugerir qué hacer
4. **Actualización en tiempo real:** Los datos deben ser frescos y confiables

#### 💻 Ejemplo de implementación práctica:

```yaml
# Configuración ejemplo para Grafana Dashboard
dashboard:
  - title: "Team Dashboard"
    panels:
      - title: "Test Coverage"
        type: "stat"
        targets:
          - expr: "sonarqube_coverage_percentage"
        thresholds:
          - color: "red"
            value: 0
          - color: "yellow"
            value: 70
          - color: "green"
            value: 80

      - title: "Build Success Rate"
        type: "stat"
        targets:
          - expr: "rate(jenkins_builds_success_total[7d])"
        unit: "percent"
```

### 4.2 Herramientas recomendadas 🛠️

| Categoría        | Herramientas                       | Propósito                        |
| ---------------- | ---------------------------------- | -------------------------------- |
| **Code Quality** | SonarQube, CodeClimate             | Análisis estático, deuda técnica |
| **Testing**      | Jest, JUnit, Cypress               | Ejecución y reporte de pruebas   |
| **Performance**  | Grafana, New Relic                 | Monitoreo de performance         |
| **CI/CD**        | Jenkins, GitLab CI, GitHub Actions | Pipeline automation              |
| **Dashboards**   | Grafana, DataDog, Elastic          | Visualización de métricas        |

## 💡 Ejercicio Práctico (10 min)

**Escenario:** Tu equipo tiene estos números actuales:

- Deployment Frequency: 1 vez por semana
- Lead Time: 3 días
- MTTR: 4 horas
- Change Failure Rate: 25%
- Test Coverage: 65%

**Tarea individual (5 min):**

1. Identifica cuál es tu métrica más crítica
2. Define 2 acciones concretas para mejorarla
3. Propón 1 Quality Gate que ayudaría

**Puesta en común (5 min):** Discusión grupal de soluciones

---

## 🔚 Resumen BLOQUE 2

**Conceptos clave cubiertos:**
✅ Pirámide de métricas de calidad
✅ DORA Metrics y su importancia  
✅ Quality Gates automatizados
✅ Feedback loops efectivos
✅ Dashboards y visualización

**Para el siguiente bloque:**
🎯 Fundamentos de DevOps y cultura CAMS

---

# 🚀 BLOQUE 3: DevOps y CI/CD - Fundamentos (40 min)

_"DevOps no es una herramienta, no es un rol, es una cultura que transforma cómo desarrollamos y entregamos software"_

## 📚 Glosario adicional para DevOps

| Término/Acrónimo           | Definición                                                            | Ejemplo práctico                                          |
| -------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------- |
| **DevOps**                 | Cultura que unifica Development (Dev) y Operations (Ops)              | Los desarrolladores pueden desplegar su propio código     |
| **CI/CD**                  | Continuous Integration / Continuous Deployment                        | Cada push al repositorio activa build y deploy automático |
| **CAMS**                   | Culture, Automation, Measurement, Sharing - pilares de DevOps         | Las 4 áreas clave para implementar DevOps exitosamente    |
| **Infrastructure as Code** | Gestionar infraestructura usando código versionado                    | Crear servidores usando archivos de configuración         |
| **Microservicios**         | Arquitectura de aplicaciones como servicios pequeños e independientes | En lugar de 1 app monolítica, tener 10 servicios pequeños |
| **Containers**             | Tecnología para empaquetar aplicaciones con sus dependencias          | Docker containers que corren igual en dev y producción    |
| **Pipeline**               | Secuencia automatizada de pasos para procesar código                  | Code → Build → Test → Deploy                              |

## 🎯 1. ¿Qué es DevOps realmente?

### 1.1 Evolución histórica: Del caos a la colaboración

```mermaid
graph LR
    subgraph "🏚️ Antes (Silos)"
        A1[Developers<br/>🧑‍💻]
        A2[QA<br/>🧪]
        A3[Operations<br/>⚙️]
    end

    subgraph "🤝 DevOps (Colaborativo)"
        B1[Dev+Ops Team<br/>🚀<br/>Cross-functional]
    end

    A1 -.->|"Throw code<br/>over the wall"| A2
    A2 -.->|"Throw bugs<br/>back"| A1
    A2 -.->|"Deploy when<br/>ready"| A3
    A3 -.->|"Production<br/>issues"| A1

    A1 --> B1
    A2 --> B1
    A3 --> B1
```

**📊 Problemas del modelo tradicional:**

- **Silos organizacionales:** Cada equipo trabaja aislado
- **Handoffs lentos:** "Tiramos el código por encima del muro"
- **Blame culture:** "No es mi problema, es del otro equipo"
- **Deploy traumático:** Releases cada 6 meses, llenos de bugs
- **Feedback tardío:** Problemas se descubren en producción

**✅ Beneficios del modelo DevOps:**

- **Colaboración continua:** Todos trabajan hacia el mismo objetivo
- **Ownership compartido:** "You build it, you run it"
- **Feedback rápido:** Problemas detectados en minutos, no meses
- **Deploys frecuentes:** Múltiples releases por día
- **Mayor calidad:** Menos bugs, más estabilidad

### 1.2 DevOps no es solo herramientas

> ⚠️ **Error común:** "Implementamos Jenkins y Docker, ya tenemos DevOps"

**❌ DevOps NO ES:**

- Una herramienta específica
- Un título de trabajo ("DevOps Engineer")
- Solo automatización
- Reemplazar QA con developers
- Solo para empresas tech grandes

**✅ DevOps SÍ ES:**

- Una **cultura** de colaboración
- Un conjunto de **prácticas** para entregar valor rápido
- Una **mentalidad** de mejora continua
- **Responsabilidad compartida** de la calidad
- **Automatización** como medio, no como fin

## 🏗️ 2. Los 4 pilares de DevOps: Modelo CAMS

### 2.1 📚 Culture (Cultura) - El pilar más importante

**¿Qué significa?**
Cambiar la mentalidad de "nosotros vs ellos" a "todos somos un equipo"

**Características de una cultura DevOps:**
| Antes | Después |
|-------|---------|
| "No es mi código, no es mi problema" | "Todos somos responsables del producto final" |
| "Funciona en mi máquina" | "Funciona en producción o no funciona" |
| "QA encontrará los bugs" | "Calidad es responsabilidad de todos" |
| "Deploys los viernes están bien" | "Deploys pequeños y frecuentes" |

**🛠️ Cómo implementar cultura DevOps:**

- **Blameless postmortems:** Cuando algo falla, enfocarse en el proceso, no en culpar personas
- **Cross-functional teams:** Equipos con devs, QA, ops, product managers
- **Shared metrics:** Todas las teams medidas con las mismas métricas (DORA)
- **Learning culture:** Experimentar, fallar rápido, aprender, iterar

### 2.2 🤖 Automation (Automatización) - Eliminar el trabajo manual

**¿Por qué automatizar?**

- Los humanos cometen errores en tareas repetitivas
- La automatización es consistente y repetible
- Libera tiempo para trabajo de mayor valor

**🔧 Áreas clave de automatización:**

```mermaid
graph TD
    A[🤖 Automatización DevOps] --> B[Code Integration]
    A --> C[Testing]
    A --> D[Deployment]
    A --> E[Infrastructure]
    A --> F[Monitoring]

    B --> B1[Git hooks<br/>Code reviews<br/>Branch policies]
    C --> C1[Unit tests<br/>Integration tests<br/>Security scans]
    D --> D1[Blue-green deploys<br/>Rollbacks<br/>Feature flags]
    E --> E1[Infrastructure as Code<br/>Auto-scaling<br/>Provisioning]
    F --> F1[Alerts<br/>Log aggregation<br/>Health checks]
```

**💻 Ejemplo de automatización práctica:**

```yaml
# Pipeline CI/CD automatizado
trigger:
  - main

stages:
  - stage: Build
    jobs:
      - job: CompileAndTest
        steps:
          - script: npm install
          - script: npm run build
          - script: npm test
          - script: npm run coverage

  - stage: QualityGates
    dependsOn: Build
    jobs:
      - job: SecurityScan
        steps:
          - script: npm audit
          - script: sonarqube-scanner

  - stage: Deploy
    dependsOn: QualityGates
    condition: succeeded()
    jobs:
      - job: DeployToProduction
        steps:
          - script: docker build -t myapp .
          - script: kubectl apply -f k8s/
```

### 2.3 📊 Measurement (Medición) - Lo que no se mide, no se mejora

**¿Qué medimos en DevOps?**

**📈 Métricas de flujo (ya vimos DORA):**

- Deployment Frequency
- Lead Time for Changes
- Mean Time to Recovery
- Change Failure Rate

**📊 Métricas de calidad:**

- Automated test coverage
- Defect density
- Customer satisfaction
- System availability

**🎯 Métricas de equipo:**

- Team velocity
- Cycle time
- Work in progress (WIP)
- Employee engagement

**📋 Implementación práctica de medición:**

```javascript
// Ejemplo: Métricas automáticas en código
const metrics = {
  deployments: {
    frequency: trackDeployments(),
    leadTime: calculateLeadTime(),
    failureRate: calculateFailureRate(),
  },
  quality: {
    coverage: getCoverageFromJest(),
    bugs: getFromJira("type = Bug"),
    performance: getResponseTimes(),
  },
};

// Enviar métricas a dashboard
sendMetrics(metrics);
```

### 2.4 🤝 Sharing (Compartir) - El conocimiento que no se comparte, se pierde

**¿Qué compartimos?**

**📚 Conocimiento:**

- Documentation as Code (docs en el mismo repo)
- Runbooks automatizados
- Incident response procedures
- Lessons learned sessions

**🛠️ Herramientas y prácticas:**

- Internal open source (código compartido entre equipos)
- Standardized tooling
- Common CI/CD templates
- Shared libraries

**📊 Datos y métricas:**

- Dashboards visibles para todos
- Performance metrics transparentes
- Error rates and trends
- Business impact metrics

**💡 Ejemplo de sharing en la práctica:**

```markdown
# Ejemplo: Runbook compartido

## Incident Response: API Down

### Detection

- Alert triggers when API response time > 5s
- Monitoring: Grafana dashboard shows red

### Investigation Steps

1. Check application logs: `kubectl logs -f deployment/api`
2. Check database connectivity: `pg_isready -h db-host`
3. Check resource usage: `kubectl top pods`

### Common Solutions

- If memory issue: Scale horizontally `kubectl scale deployment api --replicas=5`
- If database issue: Restart connection pool
- If code issue: Rollback to previous version

### Escalation

- If not resolved in 15min, escalate to @oncall-senior
- Update status page: status.company.com
```

## ⚙️ 3. CI/CD: La automatización en acción

### 3.1 Continuous Integration (CI) 🔄

**Definición:** Práctica de integrar cambios de código frecuentemente (varias veces al día) con validación automática.

**🎯 Principios clave del CI:**

1. **Single source of truth:** Todo el código en un repositorio central
2. **Automate the build:** Un comando para compilar todo
3. **Test everything:** Cada commit ejecuta la suite de tests
4. **Fast feedback:** Builds rápidos (< 10 minutos idealmente)
5. **Fix broken builds immediately:** Build roto = prioridad máxima

**🔧 Componentes de un pipeline CI típico:**

```mermaid
graph LR
    A[👨‍💻 Developer<br/>Push] --> B[⚡ Trigger<br/>Build]
    B --> C[📦 Compile<br/>Code]
    C --> D[🧪 Run<br/>Tests]
    D --> E[📊 Quality<br/>Checks]
    E --> F[🔒 Security<br/>Scan]
    F --> G[📋 Generate<br/>Reports]
    G --> H{✅ All Pass?}
    H -->|Yes| I[✅ Build<br/>Success]
    H -->|No| J[❌ Build<br/>Failure]
```

### 3.2 Continuous Deployment (CD) 🚀

**Definición:** Extensión de CI donde cada cambio que pasa las pruebas se despliega automáticamente a producción.

**🎯 Niveles de CD:**

1. **Continuous Delivery:** Código siempre listo para deploy, pero deploy es manual
2. **Continuous Deployment:** Deploy completamente automático a producción

**🛡️ Estrategias de deployment seguro:**

| Estrategia        | Descripción                                 | Cuándo usar                     |
| ----------------- | ------------------------------------------- | ------------------------------- |
| **Blue-Green**    | Dos ambientes idénticos, switch instantáneo | Apps críticas, rollback rápido  |
| **Canary**        | Deploy gradual (5% → 25% → 100% usuarios)   | Apps con mucho tráfico          |
| **Rolling**       | Reemplazar instancias una por una           | Apps stateless, downtime mínimo |
| **Feature Flags** | Código desplegado pero función desactivada  | Testing en producción           |

### 3.3 Pipeline completo: De código a producción

```mermaid
graph TD
    subgraph "🔧 Continuous Integration"
        A1[Code Commit] --> A2[Build]
        A2 --> A3[Unit Tests]
        A3 --> A4[Integration Tests]
        A4 --> A5[Code Quality]
        A5 --> A6[Security Scan]
    end

    subgraph "🚀 Continuous Deployment"
        A6 --> B1[Deploy to Staging]
        B1 --> B2[E2E Tests]
        B2 --> B3[Performance Tests]
        B3 --> B4[Deploy to Production]
    end

    subgraph "📊 Continuous Monitoring"
        B4 --> C1[Health Checks]
        C1 --> C2[Performance Metrics]
        C2 --> C3[User Analytics]
        C3 --> C4[Feedback Loop]
    end
```

## 💡 Ejercicio Práctico (10 min)

**Escenario:** Tu empresa actualmente:

- Deploy manual cada viernes
- 3 equipos separados: Dev, QA, Ops
- Testing manual antes de cada release
- Bugs descubiertos por usuarios

**Tarea en grupos (3-4 personas):**

1. **Identifica 3 problemas** principales con este modelo
2. **Propón 2 cambios culturales** (pilar Culture de CAMS)
3. **Diseña 1 automatización** que impactaría más (pilar Automation)
4. **Define 1 métrica** para medir el éxito del cambio (pilar Measurement)

**Tiempo:** 7 minutos de discusión + 3 minutos de presentación grupal

---

## 🔚 Resumen BLOQUE 3

**Conceptos clave cubiertos:**
✅ DevOps como cultura, no herramienta
✅ Modelo CAMS: Culture, Automation, Measurement, Sharing
✅ CI/CD: Integración y deployment continuo
✅ Estrategias de deployment seguro
✅ Pipeline completo DevOps

**Para el siguiente bloque:**
🎯 Testing automatizado en pipelines CI/CD

---

# 🧪 BLOQUE 4: Testing en pipelines CI/CD (30 min)

_"En DevOps, el testing no es un gate que bloquea, es un safety net que permite ir más rápido con confianza"_

## 📚 Glosario de Testing en CI/CD

| Término                 | Definición                                                                 | Ejemplo práctico                                                   |
| ----------------------- | -------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| **Test Pyramid**        | Estrategia de testing con más tests unitarios, menos E2E                   | 70% unit, 20% integration, 10% E2E                                 |
| **Smoke Tests**         | Pruebas básicas que verifican funcionalidad crítica después del deploy     | "¿La app arranca?", "¿La DB está conectada?"                       |
| **Regression Tests**    | Pruebas que verifican que nuevos cambios no rompan funcionalidad existente | Suite de tests que corre en cada deploy                            |
| **Contract Testing**    | Pruebas que verifican que APIs mantengan su contrato                       | "Este endpoint siempre devuelve un JSON con campo 'id'"            |
| **Chaos Engineering**   | Introducir fallos controlados para probar la resilencia                    | Apagar un servidor aleatoriamente para ver si el sistema sobrevive |
| **Shift-Right Testing** | Testing en producción con usuarios reales                                  | A/B testing, feature flags, monitoring                             |

## 🏗️ 1. Arquitectura de Testing en CI/CD

### 1.1 La Test Pyramid en el contexto del pipeline

```mermaid
graph TD
    subgraph "🚀 CI/CD Pipeline"
        A[Code Commit]
        B[Build]
        C[Unit Tests<br/>⚡ Fast, Many]
        D[Integration Tests<br/>🔗 Medium, Some]
        E[Contract Tests<br/>📋 API Contracts]
        F[System Tests<br/>🧪 Slow, Few]
        G[Deploy to Staging]
        H[E2E Tests<br/>🎭 Critical User Journeys]
        I[Performance Tests<br/>⏱️ Load & Stress]
        J[Security Tests<br/>🔒 Vulnerability Scans]
        K[Deploy to Production]
        L[Smoke Tests<br/>💨 Basic Health Checks]
        M[Monitoring<br/>📊 Real User Data]
    end

    A --> B
    B --> C
    C --> D
    D --> E
    E --> F
    F --> G
    G --> H
    H --> I
    I --> J
    J --> K
    K --> L
    L --> M
```

### 1.2 Testing en diferentes etapas del pipeline

| Etapa Pipeline  | Tipos de Tests        | Objetivo                 | Tiempo típico | Si falla               |
| --------------- | --------------------- | ------------------------ | ------------- | ---------------------- |
| **Pre-commit**  | Linting, Format       | Calidad básica de código | < 30 segundos | Bloquea commit         |
| **Build**       | Unit Tests            | Lógica individual        | 1-5 minutos   | Falla el build         |
| **Integration** | API Tests, DB Tests   | Componentes juntos       | 5-15 minutos  | No avanza a staging    |
| **Staging**     | E2E, Performance      | Sistema completo         | 15-60 minutos | No avanza a producción |
| **Production**  | Smoke, Health Checks  | Verificación básica      | 1-2 minutos   | Rollback automático    |
| **Post-deploy** | Monitoring, A/B Tests | Experiencia real         | Continuo      | Alertas y métricas     |

## ⚡ 2. Fast Feedback: Tests que ejecutan rápido

### 2.1 Optimización de Unit Tests

**🎯 Principios para tests rápidos:**

```javascript
// ✅ BIEN: Test unitario rápido, aislado
describe("CalculadoraDescuentos", () => {
  test("debería aplicar descuento del 10% correctamente", () => {
    const calculadora = new CalculadoraDescuentos();
    const precio = 100;
    const descuento = 10;

    const resultado = calculadora.aplicarDescuento(precio, descuento);

    expect(resultado).toBe(90);
  });
});

// ❌ MAL: Test que depende de base de datos (lento)
describe("CalculadoraDescuentos", () => {
  test("debería aplicar descuento desde DB", async () => {
    const db = await conectarBaseDatos();
    const calculadora = new CalculadoraDescuentos(db);

    const resultado = await calculadora.aplicarDescuentoDesdeDB(100, 1);

    expect(resultado).toBe(90);
  });
});
```

**🚀 Estrategias para acelerar tests:**

1. **Mocking de dependencias externas** (DB, APIs, file system)
2. **Paralelización** de test suites
3. **Test data builders** para setup rápido
4. **In-memory databases** para tests de integración
5. **Smart test selection** (solo tests afectados por cambios)

### 2.2 Pre-commit hooks: El primer filtro

```javascript
// .husky/pre-commit
#!/usr/bin/env sh
. "$(dirname -- "$0")/_/husky.sh"

echo "🔍 Running pre-commit checks..."

# Formato de código
npm run format:check
if [ $? -ne 0 ]; then
  echo "❌ Code formatting failed"
  exit 1
fi

# Linting
npm run lint
if [ $? -ne 0 ]; then
  echo "❌ Linting failed"
  exit 1
fi

# Tests unitarios rápidos
npm run test:unit
if [ $? -ne 0 ]; then
  echo "❌ Unit tests failed"
  exit 1
fi

echo "✅ Pre-commit checks passed!"
```

## 🔗 3. Integration Testing en el pipeline

### 3.1 Contract Testing: Asegurando compatibilidad

**¿Qué es Contract Testing?**
Verifica que los servicios mantengan sus "contratos" (APIs) sin necesidad de levantar todos los servicios.

```javascript
// Ejemplo con Pact.js
const { Pact } = require("@pact-foundation/pact");

describe("User Service Contract", () => {
  const provider = new Pact({
    consumer: "Frontend App",
    provider: "User Service",
  });

  test("should get user by ID", async () => {
    await provider
      .given("user exists")
      .uponReceiving("a request for user")
      .withRequest({
        method: "GET",
        path: "/users/123",
        headers: { Accept: "application/json" },
      })
      .willRespondWith({
        status: 200,
        headers: { "Content-Type": "application/json" },
        body: {
          id: 123,
          name: "John Doe",
          email: "john@example.com",
        },
      });

    const response = await userService.getUser(123);
    expect(response.id).toBe(123);
  });
});
```

### 3.2 Database Testing: Datos consistentes

```yaml
# docker-compose.test.yml
services:
  test-db:
    image: postgres:13
    environment:
      POSTGRES_DB: test_db
      POSTGRES_USER: test
      POSTGRES_PASSWORD: test
    ports:
      - "5433:5432"

  app-tests:
    build: .
    depends_on:
      - test-db
    environment:
      DATABASE_URL: postgresql://test:test@test-db:5432/test_db
    command: npm run test:integration
```

## 🎭 4. End-to-End Testing: La experiencia completa del usuario

### 4.1 E2E Tests estratégicos, no exhaustivos

**🎯 Principio clave:** E2E debe cubrir **happy paths críticos**, no todos los casos edge.

```javascript
// Ejemplo con Playwright
const { test, expect } = require("@playwright/test");

test("Usuario puede completar compra exitosamente", async ({ page }) => {
  // 1. Login
  await page.goto("/login");
  await page.fill("[data-testid=email]", "usuario@test.com");
  await page.fill("[data-testid=password]", "password123");
  await page.click("[data-testid=login-button]");

  // 2. Agregar producto al carrito
  await page.goto("/productos");
  await page.click("[data-testid=producto-123]");
  await page.click("[data-testid=agregar-carrito]");

  // 3. Checkout
  await page.goto("/carrito");
  await page.click("[data-testid=checkout]");

  // 4. Verificar compra exitosa
  await expect(page.locator("[data-testid=compra-exitosa]")).toBeVisible();
  await expect(page.locator("[data-testid=numero-orden]")).toContainText(
    /ORD-\d+/
  );
});
```

### 4.2 Visual Testing: UI consistente

```javascript
// Ejemplo con Percy o Chromatic
test("Página de checkout se ve correctamente", async ({ page }) => {
  await page.goto("/checkout");

  // Llenar formulario con datos de prueba
  await llenarFormularioCheckout(page);

  // Captura visual regression testing
  await percySnapshot(page, "Checkout Page - Filled Form");
});
```

## ⚡ 5. Performance Testing en el pipeline

### 5.1 Load Testing automatizado

```javascript
// k6 script para load testing
import http from "k6/http";
import { check, sleep } from "k6";

export let options = {
  stages: [
    { duration: "30s", target: 20 }, // Subir a 20 usuarios
    { duration: "1m", target: 20 }, // Mantener 20 usuarios
    { duration: "20s", target: 0 }, // Bajar a 0 usuarios
  ],
  thresholds: {
    http_req_duration: ["p(95)<200"], // 95% de requests < 200ms
    http_req_failed: ["rate<0.1"], // Menos del 10% de errores
  },
};

export default function () {
  let response = http.get("https://api.ejemplo.com/users");

  check(response, {
    "Status es 200": (r) => r.status === 200,
    "Respuesta en menos de 200ms": (r) => r.timings.duration < 200,
  });

  sleep(1);
}
```

### 5.2 Pipeline con performance gates

```yaml
# GitHub Actions ejemplo
name: CI/CD with Performance Testing

on: [push]

jobs:
  performance-test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2

      - name: Deploy to staging
        run: ./deploy-staging.sh

      - name: Run load tests
        run: k6 run performance-test.js

      - name: Check performance thresholds
        run: |
          if [ $? -ne 0 ]; then
            echo "❌ Performance tests failed - blocking deployment"
            exit 1
          fi
          echo "✅ Performance tests passed"

      - name: Deploy to production
        if: success()
        run: ./deploy-production.sh
```

## 🔒 6. Security Testing integrado

### 6.1 SAST y DAST en el pipeline

```yaml
security-scan:
  runs-on: ubuntu-latest
  steps:
    - uses: actions/checkout@v2

    # Static Application Security Testing (SAST)
    - name: Run SAST scan
      uses: github/super-linter@v4
      env:
        DEFAULT_BRANCH: main
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

    # Dependency vulnerability scan
    - name: Run vulnerability scan
      run: npm audit --audit-level high

    # Dynamic Application Security Testing (DAST)
    - name: Deploy to test environment
      run: ./deploy-test.sh

    - name: Run DAST scan
      run: |
        docker run --rm \
          -v $(pwd):/zap/wrk/:rw \
          owasp/zap2docker-stable:latest \
          zap-baseline.py -t https://test.myapp.com
```

## 💨 7. Smoke Tests: Validación post-deployment

### 7.1 Health checks esenciales

```javascript
// smoke-tests.js
const axios = require("axios");

const PRODUCTION_URL = "https://api.miapp.com";

describe("Smoke Tests - Production Health", () => {
  test("API está respondiendo", async () => {
    const response = await axios.get(`${PRODUCTION_URL}/health`);
    expect(response.status).toBe(200);
    expect(response.data.status).toBe("healthy");
  });

  test("Base de datos está conectada", async () => {
    const response = await axios.get(`${PRODUCTION_URL}/health/database`);
    expect(response.status).toBe(200);
    expect(response.data.database).toBe("connected");
  });

  test("Servicios externos están disponibles", async () => {
    const response = await axios.get(`${PRODUCTION_URL}/health/external`);
    expect(response.status).toBe(200);
    expect(response.data.payment_gateway).toBe("available");
    expect(response.data.email_service).toBe("available");
  });

  test("Funcionalidad crítica funciona", async () => {
    // Test del happy path más importante
    const loginResponse = await axios.post(`${PRODUCTION_URL}/auth/login`, {
      email: "smoke-test@example.com",
      password: "test-password",
    });

    expect(loginResponse.status).toBe(200);
    expect(loginResponse.data.token).toBeDefined();
  });
});
```

### 7.2 Automated rollback basado en smoke tests

```yaml
deploy-with-rollback:
  runs-on: ubuntu-latest
  steps:
    - name: Deploy new version
      id: deploy
      run: |
        ./deploy.sh
        echo "DEPLOYMENT_ID=$(cat deployment.id)" >> $GITHUB_OUTPUT

    - name: Wait for deployment to be ready
      run: sleep 60

    - name: Run smoke tests
      id: smoke-tests
      run: npm run test:smoke
      continue-on-error: true

    - name: Rollback if smoke tests fail
      if: steps.smoke-tests.outcome == 'failure'
      run: |
        echo "❌ Smoke tests failed - initiating rollback"
        ./rollback.sh ${{ steps.deploy.outputs.DEPLOYMENT_ID }}
        exit 1

    - name: Success notification
      if: steps.smoke-tests.outcome == 'success'
      run: echo "✅ Deployment successful - all smoke tests passed"
```

## 💡 Ejercicio Práctico Final (15 min)

**Escenario:** Diseña un pipeline de CI/CD para una aplicación web de e-commerce

**Requerimientos:**

- Frontend React + Backend Node.js + Base de datos PostgreSQL
- Deploy frecuente (varias veces por día)
- Zero downtime deployments
- SLA 99.9% uptime

**Tarea en grupos (3-4 personas):**

1. **Diseña el pipeline** (7 min):

   - ¿Qué tests incluirías en cada etapa?
   - ¿En qué puntos agregarías quality gates?
   - ¿Qué estrategia de deployment usarías?

2. **Define métricas de éxito** (3 min):

   - ¿Cómo medirías que el pipeline funciona bien?
   - ¿Qué alertas configurarías?

3. **Presenta tu solución** (5 min):
   - Un grupo presenta su pipeline
   - Discusión grupal de ventajas/desventajas

---

## 🔚 Resumen BLOQUE 4

**Conceptos clave cubiertos:**
✅ Test pyramid en contexto CI/CD
✅ Fast feedback con pre-commit hooks
✅ Contract testing para microservicios
✅ E2E testing estratégico
✅ Performance y security testing automatizado
✅ Smoke tests y rollback automático

---

## 🎓 RESUMEN GENERAL DE LA CLASE

### 🔄 Recorrido completo:

**BLOQUE 1:** Integramos testing en todo el SDLC con Shift-Left Testing
**BLOQUE 2:** Medimos calidad con métricas DORA y Quality Gates  
**BLOQUE 3:** Adoptamos cultura DevOps con modelo CAMS
**BLOQUE 4:** Automatizamos testing en pipelines CI/CD

### 🎯 Objetivos logrados:

✅ **Integrar estrategias de testing** en cada fase del SDLC
✅ **Implementar Shift-Left Testing** para calidad proactiva
✅ **Comprender métricas de calidad** y quality gates en DevOps
✅ **Aplicar fundamentos DevOps y CI/CD** en testing automatizado

### 🚀 Para la próxima clase:

- **Implementación práctica** de pipelines CI/CD
- **Hands-on** con herramientas reales (GitHub Actions, Jest, Playwright)
- **Workshop** de configuración de Quality Gates

### 📚 Recursos para profundizar:

- **Libros:** "Accelerate" (DORA research), "The DevOps Handbook"
- **Herramientas:** GitHub Actions, GitLab CI, Jenkins, SonarQube
- **Práctica:** Crear tu propio pipeline CI/CD con un proyecto personal

---

**¡Gracias por participar! 🙌**

_"El testing en la era DevOps no es sobre encontrar bugs, es sobre entregar valor con confianza y velocidad"_
