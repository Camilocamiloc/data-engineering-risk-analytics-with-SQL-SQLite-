# Robust Data Ingestion & QA Pipeline

ETL en Python para la ingesta segura y automatizada de datos en SQLite.

## 🛡️ Sistema de Seguridad y QA Integrado

El pipeline actúa como un guardián de la integridad de los datos mediante tres capas:

1.  **QA de Funcionamiento (Unit Testing):** Antes de la ingesta, ejecuta pruebas unitarias para asegurar que la lógica de transformación, anonimización y hashing esté intacta.
2.  **QA de Datos (Data Quality Gates):** Audita la estructura física de los CSV (conteo de columnas y validación de archivos vacíos) antes de permitir su entrada al sistema.
3.  **Trazabilidad Total (Logging System):** Genera un archivo `.log` detallado con la traza completa de ejecución, errores críticos y métricas de tiempo para un control operativo total.

## Características Técnicas

* **Privacidad:** Anonimización vectorizada de datos sensibles (PII).
* **Idempotencia:** Deduplicación basada en hashes **SHA-256**.
* **Ingesta Eficiente:** Uso de tablas de *Staging* para cargas masivas (**Bulk Upsert**).
* **Gestión de Archivos:** Archivado automático con *timestamps* tras una ingesta exitosa.

## Estructura del Proyecto

```text
.
├── data/
│   ├── landing/          # Archivos CSV crudos (Entrada)
│   └── archive/          # Histórico de archivos procesados
├── notebooks/
│   ├── etl_pipeline_e_ingesta/   # Core del Pipeline y Orquestación
│   └── ejemplos_consultas_sql/   # Ejemplos de consultas SQL en una base de datos local SQLite 
├── db/
│   ├── prueba_sql.db/    # Base de Datos SQLite
└── etl_pipeline_pro.log  # Traza de ejecución y auditoría
```

**Nota**: esta data se destina para el control de riesgo de una entidad financiera.

La data se dispone para el proceso de visualización a través de un tablero creado en Power BI para el área operativa y de riesgos.

Se realizan consultas y se exporta en archivos .csv para ser consumidos de forma incremental y presentados en el tablero, con el fin de evitar agotamiento del sistema por exceso de consultas desde el tablero y debido a las restricciones de datos del ecosistema del negocio.



