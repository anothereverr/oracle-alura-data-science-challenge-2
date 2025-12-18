# 📊 TelecomX - Análisis de Evasión de Clientes (Churn)

## 📋 Descripción del Proyecto

Este proyecto analiza los factores que influyen en la evasión de clientes (Churn) en TelecomX, una empresa de telecomunicaciones. A través del proceso ETL y el Análisis Exploratorio de Datos (EDA), se identifican patrones y tendencias que ayudan a comprender por qué los clientes abandonan el servicio.

## 🎯 Objetivo

Identificar los factores clave que contribuyen a la pérdida de clientes y proporcionar recomendaciones estratégicas basadas en datos para reducir la tasa de churn.

## 📁 Estructura del Proyecto

```
TelecomX_Churn_Analysis/
│
├── TelecomX_LATAM.ipynb             # Notebook principal con todo el análisis
├── TelecomX_diccionario.md          # Diccionario de datos
├── README.md                        # Este archivo
│
└── Visualizaciones/
    ├── distribucion_churn.png
    ├── distribucion_variables_numericas.png
    ├── churn_por_demograficos.png
    ├── churn_por_contrato_servicios.png
    ├── churn_por_servicios_adicionales.png
    ├── churn_por_cantidad_servicios.png
    ├── churn_por_tenure.png
    ├── boxplots_churn.png
    ├── matriz_correlacion.png
    ├── scatter_tenure_cargo.png
    └── resumen_hallazgos.png
```

## 🔧 Requisitos e Instalación

### Dependencias
```bash
pip install pandas numpy matplotlib seaborn
```

### Versiones utilizadas
- Python 3.8+
- pandas >= 1.3.0
- numpy >= 1.20.0
- matplotlib >= 3.4.0
- seaborn >= 0.11.0


## 📊 Dataset

El dataset contiene **7,267 registros** de clientes con **21 variables** que incluyen:

| Categoría | Variables |
|-----------|-----------|
| **Identificación** | customerID |
| **Demográficos** | gender, SeniorCitizen, Partner, Dependents |
| **Servicios de Telefonía** | PhoneService, MultipleLines |
| **Servicios de Internet** | InternetService, OnlineSecurity, OnlineBackup, DeviceProtection, TechSupport, StreamingTV, StreamingMovies |
| **Cuenta** | Contract, PaperlessBilling, PaymentMethod, Charges.Monthly, Charges.Total |
| **Variable Objetivo** | Churn |

## 🔄 Proceso ETL

### Extracción
- Carga de datos desde archivo JSON con estructura anidada
- Normalización a formato tabular plano

### Transformación
- **224 registros eliminados** por valores vacíos en Churn
- **11 valores imputados** en Cargo_Total
- Creación de variable `Cargo_Diario`
- Creación de variable `Cantidad_Servicios`
- Renombrado de columnas al español

### Carga
- Dataset limpio con **7,043 registros** listos para análisis

## 📈 Principales Hallazgos

### Tasa de Churn General: **26.5%**
- 1,869 clientes se dieron de baja
- 5,174 clientes permanecen

### ⚠️ Factores de Alto Riesgo

| Factor | Tasa de Churn |
|--------|---------------|
| Clientes nuevos (≤6 meses) | 52.9% |
| Pago con cheque electrónico | 45.3% |
| Contrato mes a mes | 42.7% |
| Servicio fibra óptica | 41.9% |
| Adultos mayores (65+) | 41.7% |

### ✅ Factores Protectores

| Factor | Tasa de Churn |
|--------|---------------|
| Contrato de 2 años | 2.8% |
| Clientes antiguos (≥48 meses) | 9.6% |
| Con soporte técnico | 15.2% |
| Con dependientes | 15.5% |

## 💡 Recomendaciones Estratégicas

### Acciones Inmediatas (0-3 meses)
1. **Programa de retención para clientes nuevos** - Seguimiento personalizado en los primeros 90 días
2. **Migración a pagos automáticos** - Incentivos del 5-10% por débito automático
3. **Identificación proactiva de clientes en riesgo** - Score de riesgo basado en tipo de contrato, antigüedad y método de pago

### Acciones a Mediano Plazo (3-6 meses)
4. **Promoción de contratos a largo plazo** - Ofertas atractivas para migrar de mes a mes
5. **Bundles de servicios** - Paquetes que incluyan servicios "ancla"
6. **Revisión del servicio de fibra óptica** - Investigar causas de insatisfacción

### Acciones a Largo Plazo (6-12 meses)
7. **Programa de lealtad** - Beneficios escalonados por antigüedad
8. **Atención especializada para adultos mayores**

## 📊 KPIs Sugeridos

| Métrica | Actual | Meta 6 meses | Meta 12 meses |
|---------|--------|--------------|---------------|
| Tasa de Churn General | 26.5% | 22% | 18% |
| Churn Clientes Nuevos | ~53% | 40% | 30% |
| % Contratos Mes a Mes | ~55% | 45% | 35% |
| % Pagos Automáticos | ~35% | 50% | 65% |

## 📌 Correlaciones Clave con Churn

| Variable | Correlación | Interpretación |
|----------|-------------|----------------|
| Meses_Contrato | -0.35 | Mayor antigüedad → Menor churn |
| Cargo_Total | -0.20 | Mayor gasto acumulado → Menor churn |
| Cargo_Mensual | +0.19 | Mayor cargo mensual → Mayor churn |
| Factura_Digital | +0.19 | Factura digital → Mayor churn |
| Seguridad_Online | -0.17 | Con seguridad → Menor churn |
