# ETL Pipeline: Datos de Bicicletas Públicas de Londres

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Pandas](https://img.shields.io/badge/Pandas-1.5+-green.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

## Descripción

Pipeline ETL (Extract, Transform, Load) que obtiene datos en tiempo real de las estaciones de bicicletas públicas de Londres a través de la API de [Transport for London (TfL)](https://api.tfl.gov.uk/).

## Arquitectura del Pipeline

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   EXTRACT   │────▶│  TRANSFORM  │────▶│    LOAD     │
│  (API TfL)  │     │  (Pandas)   │     │  (Parquet)  │
└─────────────┘     └─────────────┘     └─────────────┘
```

### Fases del ETL

| Fase | Descripción |
|------|-------------|
| **Extract** | Conexión a la API de TfL y descarga de datos JSON de ~800 estaciones |
| **Transform** | Limpieza, estructuración y validación de datos con Pandas |
| **Load** | Almacenamiento en formato Parquet optimizado para análisis |

## Tecnologías Utilizadas

- **Python 3.8+**
- **Pandas** - Manipulación y análisis de datos
- **Requests** - Consumo de API REST
- **PyArrow** - Almacenamiento en formato Parquet
- **python-dotenv** - Gestión de variables de entorno

## Estructura del Proyecto

```
flujo_etl/
├── etl_api_transporte_londres.ipynb  
├── datos_transporte_londres.parquet  
├── requirements.txt                   
├── .env.example                       
├── .gitignore                         
└── README.md                          
```

## Datos Obtenidos

El pipeline extrae los siguientes campos de cada estación:

| Campo | Descripción |
|-------|-------------|
| `nombre_estacion` | Nombre de la estación de bicicletas |
| `disponible` | Si la estación está operativa (Sí/No) |
| `n_bicis` | Número total de bicicletas disponibles |
| `n_espacios_disponibles` | Espacios vacíos para devolver bicicletas |
| `n_espacios_total` | Capacidad total de la estación |
| `n_bicis_estandar` | Bicicletas estándar disponibles |
| `n_bicis_electricas` | Bicicletas eléctricas disponibles |
| `latitud` | Coordenada geográfica |
| `longitud` | Coordenada geográfica |
| `fecha_extraccion` | Timestamp de la extracción |

## 📄 Licencia

Este proyecto está bajo la Licencia MIT - ver el archivo [LICENSE](LICENSE) para más detalles.

## Contribuciones

Las contribuciones son bienvenidas. Por favor, abre un issue primero para discutir los cambios propuestos.

---

