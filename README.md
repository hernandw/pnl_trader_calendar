# 📈 P&L Calendar & Options Trading Journal

Un diario de trading interactivo y visual para opciones financieras y acciones, diseñado para monitorear ganancias y pérdidas diarias (P&L), tasas de acierto y estadísticas oficiales con la fórmula de **Charles Schwab / Thinkorswim**.

Construido como una Single Page Application (SPA) en **HTML5, Tailwind CSS y JavaScript Vanilla**, sin dependencias de servidor (todo corre 100% en el navegador con persistencia en `localStorage`).

---

## 📸 Capturas de Pantalla

### Vista Mensual (Trading P&L Calendar)
Calendario interactivo de lunes a viernes con celdas diferenciadas por colores pastel para ganancias y pérdidas, conteo de trades y la etiqueta dinámica **Today** en el día actual:

<p align="center">
  <img src="screenshots/calendar-month.png" alt="Vista Mensual del Calendario" width="580" style="border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
</p>

### Vista Anual (12 Meses)
Resumen consolidado de enero a diciembre con el cálculo acumulado en tiempo real del P&L neto y volumen de operaciones por mes:

<p align="center">
  <img src="screenshots/calendar-year.png" alt="Vista Anual de 12 Meses" width="580" style="border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
</p>

### Detalle de Operaciones & Métricas por Contrato
Desglose financiero por operación: número de contratos (`Qty`), `Strike`, tipo (`CALL/PUT`), expiración calculada (`0DTE`, `1DTE`), valor de compra unitario, precio de venta y retorno porcentual (`ROI %`):

<p align="center">
  <img src="screenshots/trade-details.png" alt="Detalle de Operaciones" width="580" style="border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
</p>

---

## 🚀 Características Principales

- **Calendario Dinámico (Lunes a Viernes):**
  - Muestra exclusivamente días operativos de mercado (de lunes a viernes).
  - Fondo verde pastel y texto esmeralda para días con ganancias; fondo rojo pastel para días negativos.
  - Indicador dinámico **"Today"** exclusivo en el día en curso del sistema.
  - Conteo de operaciones cerradas en la esquina superior de cada día (`1 trade`, `2 trades`, etc.).
- **Compatibilidad Nativa con Charles Schwab / Thinkorswim:**
  - Importador inteligente de archivos CSV (`GainLoss_Realized_Details.csv`).
  - Detección automática del encabezado ignorando filas de metadatos del broker.
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

### Paso 1: Subir archivos a GitHub
1. Crea un nuevo repositorio en tu cuenta de GitHub (por ejemplo, `trading-pnl-calendar`).
2. Sube el archivo `index.html`, `README.md` y la carpeta `screenshots/` con tus imágenes.

```bash
git init
git add .
git commit -m "feat: Add P&L Trading Calendar with screenshots"
git branch -M main
git remote add origin [https://github.com/TU-USUARIO/trading-pnl-calendar.git](https://github.com/TU-USUARIO/trading-pnl-calendar.git)
git push -u origin main