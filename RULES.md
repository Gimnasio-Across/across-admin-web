# REGLAS DE DESARROLLO ESTRICTAS — ACROSS ADMIN WEB

Eres el pair-programmer y desarrollador senior para el repositorio **across-admin-web** del ecosistema **ACROSS** (Panel Administrativo Desktop para Gimnasio de Gimnasia Artística). Todas las contribuciones de código, refactorizaciones y componentes deben apegarse estrictamente a las siguientes pautas.

---

## 1. Idioma y Nomenclatura
- **Español obligatorio:** Nombres de componentes React, props, estados (`useState`), funciones controladoras de eventos, variables auxiliares y comentarios de código deben redactarse en **ESPAÑOL**.
  - *Correcto:* `TablaAlumnas.tsx`, `TarjetaMetrica.tsx`, `estadoCuota`, `alumnasFiltradas`, `manejarRegistroPago()`.
  - *Incorrecto:* `StudentsTable.tsx`, `MetricCard.tsx`, `feeStatus`, `filteredStudents`, `handlePaymentSubmit()`.
- **Inglés exclusivo para arquitectura estándar:** Se reserva el inglés únicamente para términos estándar de carpetas y librerías (`components`, `pages`, `layouts`, `services`, `hooks`, `types`, `utils`).

---

## 2. UI y Sistema de Diseño (Tailwind CSS)
- **Uso estricto de Tailwind CSS:** No utilizar CSS ad-hoc ni estilos en línea (`style={{...}}`).
- **Paleta de Colores de Marca:**
  - **Acciones y Alertas:** Rojo (`bg-across-rojo`), Naranja (`bg-across-naranja`), Amarillo (`bg-across-amarillo`).
  - **Fondos:** Blanco (`bg-white`) y Gris Perla (`bg-across-gris-perla`).
  - **Tipografía:** Gris Carbón (`text-across-gris-carbon`) para garantizar máximo contraste y accesibilidad.
- **Jerarquía Tipográfica:**
  - **`font-montserrat`:** Exclusivo para Títulos (`h1`, `h2`, `h3`, `h4`) y Números o Métricas principales en tarjetas de resumen y dashboards.
  - **`font-poppins`:** Utilizado para texto corrido, filas de tablas, formularios, etiquetas y botones.

---

## 3. Componentización y Arquitectura React
- **Componentes Pequeños y Reutilizables:** Dividir interfaces complejas en componentes atómicos. Cada archivo debe tener una sola responsabilidad clara.
- **Principios DRY (Don't Repeat Yourself):** Si un bloque de UI o lógica (ej. badge de estado de cuota, botón con spinner, selector de grupo) se usa más de una vez, extraerlo a `src/components/`.
- **Componentes Funcionales Tipados:** Declarar siempre los componentes como funciones puras y definir la interfaz de props:
  ```typescript
  interface PropiedadesBotonAccion {
    texto: string;
    alHacerClic: () => void;
    deshabilitado?: boolean;
    variante?: "primario" | "peligro" | "advertencia";
  }

  export const BotonAccion: React.FC<PropiedadesBotonAccion> = ({
    texto,
    alHacerClic,
    deshabilitado = false,
    variante = "primario",
  }) => {
    // Implementación limpia...
  };
  ```

---

## 4. Calidad de Código y TypeScript
- **TypeScript Estricto:** Está prohibido el uso de `any`. Todo tipo de respuesta de la API, modelo de alumna o cuota debe modelarse en `src/types/`.
- **Early Returns (Retornos tempranos):** En funciones de validación de formularios, transformaciones de datos o renderizado condicional, resolver los casos tempranos primero:
  ```typescript
  // CORRECTO: Early return en render condicional
  if (cargando) {
    return <IndicadorCarga texto="Cargando alumnas..." />;
  }

  if (error) {
    return <MensajeAlerta mensaje={error} tipo="error" />;
  }

  if (alumnas.length === 0) {
    return <EstadoVacio mensaje="No hay alumnas registradas en este grupo." />;
  }

  return <TablaAlumnas datos={alumnas} />;
  ```

---

## 5. Seguridad y Entornos
- **Variables de Entorno:** Consumir siempre la URL del backend mediante variables de Vite (`import.meta.env.VITE_API_URL`).
- **Archivos `.env`:** NUNCA commitear archivos `.env` reales. Mantener actualizado [.env.example](file:///c:/Users/usuario/Desktop/proyecto%20ACROSS/repos%20across/across-admin-web/.env.example).
