# 📈 P&L Calendar & Options Trading Journal

Un diario de trading interactivo y visual para opciones financieras y acciones, diseñado para monitorear ganancias y pérdidas diarias (P&L), tasas de acierto y estadísticas oficiales con la fórmula de **Charles Schwab / Thinkorswim**.

Construido como una Single Page Application (SPA) en **HTML5, Tailwind CSS y JavaScript Vanilla**, sin dependencias de servidor (todo corre 100% en el navegador con persistencia en `localStorage`).

---

## 🚀 Características Principales

- **Calendario Dinámico (Lunes a Viernes):**
  - Muestra exclusivamente días operativos de mercado (de lunes a viernes).
  - Fondo verde pastel y texto esmeralda para días con ganancias; fondo rojo pastel para días negativos.
  - Indicador dinámico **"Today"** exclusivo en el día en curso del sistema.
  - Conteo de operaciones cerradas en la esquina superior de cada día (`1 trade`, `2 trades`, etc.).
- **Compatibilidad Nativa con Charles Schwab / Thinkorswim:**
  - Importador inteligente de archivos CSV (`GainLoss_Realized_Details.csv`).
  - Detección automática del encabezado ignorando filas de metadatos.
  - Modo **Fusión inteligente:** suma nuevos reportes sin sobreescribir los datos previos ni duplicar registros.
- **Desglose de Opciones Financieras:**
  - Extracción de **Ticker**, **Strike limpio** (sin `$`), tipo (**CALL / PUT**) y número de contratos (**Qty**).
  - Cálculo matemático exacto de **DTE** (`0DTE`, `1DTE`, `2DTE`, etc.) comparando fecha de apertura (`Opened Date`) y fecha de expiración.
  - Precios unitarios: Costo por contrato de compra (`Cto Compra`) y precio de venta (`Cto Venta`).
  - Cálculo del retorno porcentual de la posición (**ROI %**).
- **Métricas Alineadas a Charles Schwab:**
  - **Relación Ganancia/Pérdida:** Calculada mediante la fórmula oficial de volumen:
    $$\text{Relación G/P} = \frac{\text{Ganancias Brutas}}{\text{Ganancias Brutas} + \vert{}\text{Pérdidas Brutas}\vert{}} \times 100$$
  - Desglose de Ganancias Brutas (`+$$$`) y Pérdidas Brutas (`-$$$`).
  - Tasa de acierto de trades (`Win Rate %`).
- **Resumen Anual (12 Meses):**
  - Tarjetas de enero a diciembre con el P&L acumulado y el número total de trades por mes.
- **Pestaña de Tickers (Compañías):**
  - Resumen por activo (`SPY`, `TSLA`, `AMD`, `NVDA`, `QQQ`).
  - Total invertido, Win Rate por empresa y modal para inspeccionar el historial individual de cada símbolo.
- **Privacidad y Persistencia:**
  - Todos los datos se almacenan localmente en el navegador (`localStorage`). No se envían datos a ningún servidor externo.

---

## 🛠️ Tecnologías Utilizadas

- **HTML5 semántico**
- **[Tailwind CSS (CDN)](https://tailwindcss.com/):** Estilos modernos, diseño responsive y paleta pastel personalizada.
- **[Lucide Icons](https://lucide.dev/):** Iconografía moderna y ligera.
- **[PapaParse](https://www.papaparse.com/):** Procesamiento y parseo rápido de archivos CSV en el cliente.
- **JavaScript (ES6+):** Lógica reactiva sin frameworks pesados.

---

## 📂 Formato de CSV Soportado

El analizador está preparado para reportes de ganancias realizadas de brokers (formato Charles Schwab):

| Columna | Descripción |
| :--- | :--- |
| `Symbol` | Símbolo estándar de opciones (ej. `TSLA 04/08/2026 340.00 P`) |
| `Opened Date` | Fecha de apertura (`MM/DD/YYYY`) |
| `Closed Date` | Fecha de cierre (`MM/DD/YYYY`) |
| `Quantity` | Cantidad de contratos operados |
| `Cost Basis (CB)` | Capital total invertido en la posición |
| `Proceeds` | Monto total recibido al cerrar la posición |
| `Gain/Loss ($)` | Ganancia o pérdida neta |

---

## 💻 Instalación y Despliegue en GitHub Pages

### Paso 1: Clonar o crear el repositorio
1. Crea un nuevo repositorio en tu cuenta de GitHub (por ejemplo, `trading-pnl-calendar`).
2. Sube los archivos `index.html` y `README.md`.

```bash
git init
git add .
git commit -m "Initial commit: P&L Trading Calendar"
git branch -M main
git remote add origin [https://github.com/TU-USUARIO/trading-pnl-calendar.git](https://github.com/TU-USUARIO/trading-pnl-calendar.git)
git push -u origin main