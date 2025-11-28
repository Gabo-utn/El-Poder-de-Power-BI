# 📊 El Poder de Power BI – Mercado Laboral IT en Argentina 2023

[![Status](https://img.shields.io/badge/Status-Completado-success)]()
[![Tool](https://img.shields.io/badge/Tool-Power%20BI-F2C811?logo=powerbi&logoColor=black)]()
[![Language](https://img.shields.io/badge/Idioma-Español-blue)]()

> **Alumno:** Héctor Gabriel Campi  
> **Asignatura:** Análisis de Datos  
> **Tema:** Recuperatorio Laboratorio Práctico – *El Poder de Power BI*  
> **Docente:** Miguel Puente  

---

## 🚀 Descripción general

Este proyecto muestra cómo utilizar **Power BI** para convertir datos crudos en un **dashboard interactivo** que describe el **Mercado Laboral IT en Argentina** a partir de la encuesta salarial de Sysarmy 2023.

El informe permite analizar:

- 💼 **Roles mejor remunerados**
- 📈 Evolución del **salario promedio en el tiempo**
- 🧗‍♂️ Diferencias salariales por **seniority**
- 🌍 Distribución de encuestados por **provincia**
- ⚖️ Comparación entre **salario promedio** y **salario mediano**, para entender mejor la distribución de sueldos

---

## 🎯 Objetivos del proyecto

- Aplicar un proceso **ETL completo** dentro de Power BI.
- Diseñar un **modelo de datos en estrella** a partir de varias fuentes.
- Crear un **dashboard profesional** con indicadores claros para la toma de decisiones.
- Practicar buenas prácticas de visualización y storytelling con datos.

---

## 🧾 Fuentes de datos

Se utilizaron **tres datasets principales**:

1. `2023.1_Sysarmy_Encuesta de remuneración salarial Argentina.csv`  
   - Encuesta salarial de la comunidad Sysarmy (mercado IT argentino).
2. `base_araucano.csv`  
   - Base de egresados universitarios argentinos.
3. `poblacion_ar_dpto.csv`  
   - Población por departamento en Argentina.

> Todas las fuentes se trabajaron en Power Query para limpieza y transformación.  
> El modelo principal del dashboard se centra en la encuesta Sysarmy (tabla `Fact_Salarios`).

---

## 🔄 Proceso ETL (resumen)

En el Editor de Power Query se realizaron los siguientes pasos:

- 📥 **Extracción**
  - Importación de los archivos CSV.
  - Promoción de encabezados y detección de tipos de datos.

- 🧹 **Transformación**
  - Estandarización de nombres de columnas (ej.: `Rol`, `Seniority`, `Provincia`, `Modalidad`, `SalarioBruto`).
  - Corrección de tipos (texto, número, fecha).
  - Eliminación de filas con valores nulos o inconsistentes en campos clave.
  - Creación de columnas derivadas (por ejemplo, `MesAño` en la tabla de fechas).
  - Generación de tablas de dimensiones a partir de la tabla de hechos con **Quitar duplicados**.

- 📦 **Carga**
  - Carga de las tablas finales al modelo de Power BI.
  - Validación de filas, tipos de datos y relaciones antes de construir el dashboard.

---

## 🧩 Modelo de datos

Se diseñó un **esquema en estrella**, con:

- **Tabla de hechos**
  - `Fact_Salarios`: contiene una fila por encuestado con salario, rol, seniority, provincia, modalidad de trabajo y género.

- **Tablas de dimensiones**
  - `Dim_Rol` – listado único de roles del mercado IT.
  - `Dim_Seniority` – niveles de seniority (Junior, Semi-Senior, Senior).
  - `Dim_Modalidad` – modalidades de trabajo (presencial, remoto, híbrido).
  - `Dim_Region` – provincias de Argentina.
  - `DimFecha` – tabla calendario marcada como tabla de fechas.

- **Relaciones**
  - Todas las dimensiones se relacionan con `Fact_Salarios` en esquemas **1 : * (uno a muchos)**.
  - `DimFecha` se conecta a la fecha de referencia (mes del último ajuste salarial) para habilitar inteligencia de tiempo.

---

## 📊 El dashboard

> 📌 Archivo principal: `El-Poder-de-Power-BI.pbix`.

Vista principal del informe:

```text
Análisis del Mercado Laboral IT – Argentina 2023


