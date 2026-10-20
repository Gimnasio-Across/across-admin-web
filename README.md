# ACROSS Admin Web — Panel Administrativo Desktop 💻

Frontend web de escritorio para la administración general del gimnasio de Gimnasia Artística **ACROSS**.

Permite a los administradores gestionar altas/bajas de alumnas, conformación de grupos y niveles, cobro y seguimiento de cuotas mensuales, registro de seguros federativos/deportivos y visualización de métricas del gimnasio.

---

## 🛠️ Stack Tecnológico

- **Framework:** [React 19](https://react.dev/)
- **Bundler & Dev Server:** [Vite](https://vitejs.dev/)
- **Lenguaje:** [TypeScript](https://www.typescriptlang.org/) (Modo estricto)
- **Estilos:** [Tailwind CSS v3](https://tailwindcss.com/) + PostCSS + Autoprefixer
- **Tipografías:** Google Fonts (`Montserrat` & `Poppins`)

---

## 🎨 Sistema de Diseño ACROSS

### 1. Tipografías
- **`font-montserrat` (`Montserrat`):** Reservada para Títulos (`h1`, `h2`, `h3`) y Números/Métricas de impacto en tarjetas y dashboards.
- **`font-poppins` (`Poppins`):** Utilizada para texto corrido, tablas de datos, formularios y botones.

### 2. Paleta de Colores Corporativa
Configurada en `tailwind.config.js` bajo el prefijo `across-`:

| Token Tailwind | Tono | Uso recomendado |
| :--- | :--- | :--- |
| `bg-across-rojo` / `text-across-rojo` | Rojo (`#E53935`) | Acciones destructivas, alertas críticas, cuotas vencidas. |
| `bg-across-naranja` / `text-across-naranja` | Naranja (`#FB8C00`) | Acciones primarias, llamadas de atención, estados pendientes. |
| `bg-across-amarillo` / `text-across-amarillo` | Amarillo (`#FDD835`) | Advertencias, avisos preventivos, destacados. |
| `bg-across-gris-perla` | Gris Perla (`#F4F5F7`) | Fondo principal de pantallas y contenedores suaves. |
| `text-across-gris-carbon` | Gris Carbón (`#212121`) | Texto principal de alto contraste y legibilidad. |

---

## 📁 Estructura del Proyecto

```text
across-admin-web/
├── public/                   # Recursos estáticos públicos (logos, favicons)
├── src/
│   ├── assets/               # Imágenes, ilustraciones y gráficos SVG
│   ├── components/           # Componentes UI atómicos y reutilizables (Botón, Input, Modal, Tabla)
│   ├── layouts/              # Plantillas maestras (Sidebar, Header, Layout administrativo)
│   ├── pages/                # Vistas principales (Dashboard, Alumnas, Cuotas, Grupos)
│   ├── services/             # Clientes de consumo de la API (`across-backend`)
│   ├── types/                # Interfaces y contratos de tipos TypeScript
│   ├── utils/                # Funciones auxiliares de formateo (fechas, moneda, etc.)
│   ├── App.tsx               # Enrutador y árbol principal de componentes
│   ├── index.css             # Directivas Tailwind y estilos globales
│   └── main.tsx              # Renderizado inicial en el DOM
├── RULES.md                  # Reglas de desarrollo estrictas para pair-programming
├── index.html                # Plantilla HTML con precarga de Google Fonts
├── package.json              # Dependencias y scripts
├── tailwind.config.js         # Tokens de tipografía y colores de marca
└── vite.config.ts            # Configuración de Vite
```

---

## 🚀 Instalación y Puesta en Marcha Local

### 1. Prerrequisitos
- [Node.js](https://nodejs.org/) (v18 o superior).

### 2. Clonar e Instalar Dependencias
```bash
git clone https://github.com/Gimnasio-Across/across-admin-web.git
cd across-admin-web
npm install
```

### 3. Levantar en Modo Desarrollo
```bash
npm run dev
```
La aplicación abrirá por defecto en `http://localhost:5173`.

### 4. Compilar para Producción
```bash
npm run build
```
Genera la carpeta optimizada `dist/` lista para despliegue.

---

## 🛡️ Reglas de Desarrollo
Consulta [RULES.md](file:///c:/Users/usuario/Desktop/proyecto%20ACROSS/repos%20across/across-admin-web/RULES.md) para cumplir las directrices de nomenclatura en español, componentización funcional estricta, TypeScript sin `any` y arquitectura DRY.
