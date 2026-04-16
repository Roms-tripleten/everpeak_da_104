# Análisis de Segmentación de Clientes EverPeak para SilverBasket Retail Group

## 📝 Descripción del Proyecto

Este repositorio contiene el análisis de datos transaccionales de **EverPeak Holdings**, realizado como parte del proceso de diligencia previa a su adquisición por **SilverBasket Retail Group**. El objetivo principal es evaluar la calidad y estructura de los datos, identificar patrones clave en el comportamiento del cliente y definir segmentos estratégicos que permitan una integración exitosa y la optimización de futuras estrategias de negocio.

## 🎯 Objetivos del Análisis

1.  **Evaluar la Calidad y Consistencia de Datos**: Diagnosticar la integridad y fiabilidad de los datos transaccionales de EverPeak.
2.  **Identificar Patrones de Comportamiento**: Descubrir tendencias en el valor de las transacciones (`order_value`) y la demografía (`customer_age`).
3.  **Definir Segmentos de Clientes**: Crear una segmentación de clientes basada en el valor de gasto y la edad para identificar grupos de alto potencial.

## 📊 Metodología

El análisis se llevó a cabo utilizando `Python` y las librerías `pandas`, `matplotlib` y `seaborn` en un entorno de Google Colab. La metodología incluyó los siguientes pasos:

### 1. Visión General y Carga de Datos

*   Carga inicial del dataset `everpeak_retail.csv`.
*   Revisión de la estructura del dataset, tipos de datos y presencia de valores faltantes.

### 2. Limpieza y Preparación de Datos

*   **Estandarización de Columnas de Texto**: Eliminación de espacios, normalización a minúsculas y reemplazo de valores `?` o nulos por `'Unknown'` en categorías como `product_category`, `payment_method`, `city`, `state`.
*   **Tratamiento de Variables Numéricas**: Conversión a formato numérico, reemplazo de valores centinela (`-999`) y nulos con la media de la columna en `price` y `customer_age`.
*   **Conversión de Fechas**: Transformación de `order_date` a formato `datetime`.
*   **Eliminación de Duplicados**: Asegurar la unicidad de las transacciones.

### 3. Análisis Estadístico y Tratamiento de Atípicos

*   **`order_value`**: Análisis de distribución (histograma y boxplot) y detección de 165 outliers mediante el método IQR. Se decidió eliminar estos registros para evitar distorsiones en la segmentación.
*   **`customer_age`**: Análisis de distribución y resumen estadístico. La variable mostró una distribución balanceada y sin atípicos significativos, lo que la hace robusta para la segmentación.

### 4. Segmentación de Clientes

Se implementó una segmentación propuesta por la gerencia, combinando `order_value` y `customer_age` para categorizar a los clientes en los siguientes grupos:

*   **Senior VIP**: Alto gasto (`>= 10000`) y edad avanzada (`>= 55`).
*   **Junior VIP**: Alto gasto (`>= 10000`) y edad joven (`< 55`).
*   **Sr. Medium Value**: Gasto medio (`>= 5000` y `< 10000`) y edad avanzada (`>= 55`).
*   **Jr. Medium Value**: Gasto medio (`>= 5000` y `< 10000`) y edad joven (`< 55`).
*   **Low Value**: Gasto bajo (`< 5000`).

## 💡 Resultados Clave de la Segmentación

La segmentación reveló una estructura clara de la base de clientes de EverPeak:

| Segmento          | Clientes |
| :---------------- | :------- |
| Senior VIP        | 2005     |
| Low Value         | 1699     |
| Jr. Medium Value  | 654      |
| Junior VIP        | 485      |

*   **Senior VIP**: El grupo más numeroso, representa clientes de alto valor y lealtad, cruciales para la retención.
*   **Low Value**: Segundo grupo más grande, ofrece oportunidades para estrategias de activación y *upselling*.
*   **Junior VIP** y **Jr. Medium Value**: Grupos más pequeños pero con alto potencial de crecimiento a largo plazo, ideales para fidelización temprana.

Esta segmentación proporciona a SilverBasket una visión estratégica equilibrada entre los clientes que sostienen el valor actual de EverPeak y aquellos que representan su potencial de crecimiento futuro.

## 🚀 Cómo Reutilizar el Análisis

El notebook de Google Colab (`Análisis_estadístico_para_detectar_patrones_y_outliers_III.ipynb`) contiene todo el código y la documentación detallada para reproducir este análisis. Puedes abrirlo directamente en Google Colab y ejecutar las celdas para replicar los resultados y explorar los datos.

---
