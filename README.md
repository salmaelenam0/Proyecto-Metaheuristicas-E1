# Proyecto-Metaheuristicas-E1
Este proyecto implementa dos enfoques complementarios para resolver el problema de planificación de carga en estaciones de vehículos eléctricos (EVs): un modelo matemático exacto y una heurística constructiva con búsqueda local. Ambos métodos buscan asignar cargadores a vehículos maximizando la energía entregada y minimizando el costo, cumpliendo con restricciones técnicas como disponibilidad, capacidad del transformador y potencia de cargadores.

---

##  Estructura del Proyecto

El proyecto se encuentra en un único archivo Jupyter Notebook que contiene:

- Fase 1: Modelo exacto para maximizar la energía entregada.
- Fase 2: Re optimización de la asignación para minimizar el costo de energía.
- Heurística Constructiva: Asigna vehículos según una prioridad basada en urgencia y disponibilidad.
- Búsqueda Local: Reubica energía hacia intervalos más baratos para reducir el costo.
- Visualizaciones: Diagramas de Gantt y gráficos de uso del transformador.

---

##  Metodología

###  Modelo Matemático (Fase 1 + Fase 2)
- Fase 1: Maximiza la energía suministrada a los vehículos, asegurando que no se sobrecargue el transformador ni los cargadores.
- Fase 2: Redistribuye esa energía para minimizar el costo total aprovechando los precios horarios.

> Implementado en Python con Gurobi como solver de optimización.

### Heurística Constructiva
- Calcula una prioridad dinámica para cada vehículo
- Asigna de forma greedy respetando las restricciones de disponibilidad, transformador y potencia.
- Inspirada en Vandael et al. (2015).

### Búsqueda Local
- Mejora el plan inicial moviendo carga desde intervalos con alto precio hacia otros más baratos, manteniendo factibilidad.
- Aumenta significativamente la eficiencia sin comprometer la satisfacción energética.

---

## Resultados y Visualización

- Modelos exactos: Alta satisfacción energética (hasta 100 %) con tiempos de cómputo más elevados.
- Heurística + BL: Soluciones de buena calidad en menor tiempo (milisegundos a pocos segundos).
- Comparativas: Se incluyen gráficas del uso del transformador y diagramas de Gantt para evaluar distribución temporal y eficiencia.

---
##Cómo ejecutar
1.Clona el repositorio o descarga el archivo .ipynb donde está todo el código (modelos + heurística).

2.Prepara tu entorno Python :

python -m venv ev-env
source ev-env/bin/activate  # o ev-env\Scripts\activate en Windows
3.Instala las dependencias necesarias:

pip install gurobipy matplotlib
*Asegúrate de tener Gurobi instalado y con licencia activada. 

4. Ubica los archivos de prueba JSON, por ejemplo:
test_system_1.json, test_system_2.json, etc., en el mismo directorio del notebook, o modifica la variable archivo en el código para apuntar a la ruta correcta.

5. Abre y ejecuta el Notebook en Jupyter:

Ejecuta cada celda secuencialmente para correr:

- Fase 1 (Maximización de energía),

- Fase 2 (Minimización de costos),

- Heurística constructiva,

- Búsqueda local,

- Visualizaciones (Gantt y uso del transformador).
