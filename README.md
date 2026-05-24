# 🎬 Association Rules · Movie Recommendation System
### Apriori · FP-Growth · ECLAT sobre MovieLens 100K

[![R](https://img.shields.io/badge/Lenguaje-R-276DC3?logo=r)](https://www.r-project.org/)
[![Quarto](https://img.shields.io/badge/Notebook-Quarto-5A9BD5)](https://quarto.org/)
[![Dataset](https://img.shields.io/badge/Dataset-MovieLens%20100K-FF6B35)](https://grouplens.org/datasets/movielens/100k/)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

---
visita el proyecto en este link : https://alej2andro.github.io/association-rules-movielens/

---
## 📌 Descripción

Este proyecto implementa un **sistema de recomendación de películas** basado íntegramente en **reglas de asociación**, comparando tres algoritmos clásicos de minería de patrones frecuentes:

| Algoritmo | Estrategia |
|-----------|-----------|
| **Apriori** | Generación candidata nivel a nivel |
| **FP-Growth** | Árbol FP-tree comprimido, sin candidatos |
| **ECLAT** | Intersección de tidsets verticales |

El objetivo principal fue **aprender y aplicar** estos algoritmos en profundidad —desde sus fundamentos matemáticos hasta su comparativa empírica— construyendo un motor de recomendación funcional sobre datos reales de comportamiento cinematográfico.

---

## 📦 Dataset

**MovieLens 100K** — GroupLens Research, Universidad de Minnesota

| Dimensión | Detalle |
|-----------|---------|
| Usuarios | 943 (mínimo 20 ratings cada uno) |
| Películas | 1 682 únicas |
| Ratings | 100 000 en escala 1–5 |
| Géneros | 19 (Action, Drama, Comedy, Horror, Sci-Fi, Thriller…) |
| Sparsity | 96.3 % de celdas sin interacción |

🔗 **Fuente oficial:** https://grouplens.org/datasets/movielens/100k/  
🔗 **Kaggle mirror:** https://www.kaggle.com/datasets/prajitdatta/movielens-100k-dataset

> Harper, F. M., & Konstan, J. A. (2015). The MovieLens datasets: History and context. *ACM Transactions on Interactive Intelligent Systems*, 5(4), 1–19.

---

## 🗂️ Estructura del Proyecto

```
association-rules-movielens/
│
├── ReglaAsociacion.qmd       # Notebook principal (Quarto/R)
├── ReglaAsociacion.html      # Reporte renderizado
├── data/
│   └── ml-100k/              # Dataset MovieLens 100K (u.data, u.item, u.user)
└── README.md
```

---

## 🔬 Pipeline Metodológico

```
Carga MovieLens 100K
        ↓
EDA + Diagnóstico de calidad (sparsity, distribuciones, géneros)
        ↓
Binarización: rating ≥ 4 → transacción positiva
        ↓
Clean Algorithm
  ├─ Paso 4a: eliminar ítems con soporte < 5 %
  └─ Paso 4b: eliminar correlaciones iterativas ≥ 0.90 (Pearson)
        ↓
┌─────────────┬──────────────┬─────────┐
│   Apriori   │  FP-Growth   │  ECLAT  │
└─────────────┴──────────────┴─────────┘
        ↓
Comparativa: N reglas · Lift · Confianza · Conviction · Leverage · Tiempo CPU
        ↓
Motor de recomendación por perfil de género (Drama, Acción, Comedia)
```

---

## 📊 Principales Resultados

- **443 975 reglas** generadas por los tres algoritmos con parámetros equivalentes.
- **74 % de las reglas** superan `lift > 2` y `conf > 0.5` → calidad suficiente para producción.
- Los tres algoritmos producen **exactamente el mismo conjunto de reglas**; la diferencia es puramente computacional: FP-Growth y ECLAT son sistemáticamente más rápidos que Apriori.
- Las mejores reglas se concentran en **soporte bajo, confianza alta**: asociaciones entre películas de nicho, poco frecuentes pero muy predictivas.

---

## 🔭 Proyección y Oportunidad de Mejora

Este proyecto es un **precursor deliberado**. Su propósito va más allá del sistema de recomendación en sí: establecer una base sólida sobre reglas de asociación para proyectos futuros de mayor complejidad y aplicabilidad real.

Las líneas de desarrollo proyectadas incluyen:

- **Accionabilidad de resultados:** traducir las reglas de asociación en decisiones de negocio concretas —cross-selling, segmentación de clientes, alertas tempranas— aplicables directamente en roles de **Business Intelligence**.
- **Integración con filtrado colaborativo:** combinar reglas de asociación con SVD, ALS o embeddings para sistemas híbridos más robustos.
- **Extensión a otros dominios:** retail, e-commerce, comportamiento de clientes en plataformas digitales.
- **Automatización del pipeline:** despliegue como API o dashboard interactivo con reglas actualizables.
- **Profundización en ML e IA:** cada proyecto en este portafolio es un peldaño en un trayecto hacia Data Engineering, Magíster en IA y aplicación profesional de machine learning avanzado.

> *"Aprender haciendo, construir para entender, aplicar para crear valor."*

---

## 🛠️ Stack Tecnológico

```r
# Paquetes principales
recommenderlab · arules · arulesViz
ggplot2 · dplyr · tidyr · knitr · kableExtra
patchwork · viridis · ggrepel · corrplot
```

**Entorno:** R + Quarto · RStudio · TinyTeX (renderizado PDF/HTML)

---

## 📚 Referencias

- Agrawal, R., & Srikant, R. (1994). Fast algorithms for mining association rules. *VLDB*, 487–499.
- Han, J., Pei, J., & Yin, Y. (2000). Mining frequent patterns without candidate generation. *ACM SIGMOD*, 29(2), 1–12.
- Zaki, M. J. (2000). Scalable algorithms for association mining. *IEEE TKDE*, 12(3), 372–390.
- Hahsler, M., Grün, B., & Hornik, K. (2005). arules: A computational environment. *JSS*, 14(15), 1–25.
- Ricci, F., Rokach, L., & Shapira, B. (2015). *Recommender Systems Handbook* (2nd ed.). Springer.

---

## 📬 Contacto

¿Tienes feedback, ideas de colaboración o quieres discutir aplicaciones de BI y machine learning?

- ✉️ **Email:** alejandro.figueroa.rojas@gmail.com
- 🐙 **GitHub:** [github.com/Alej2andro](https://github.com/Alej2andro)

---

*Desarrollado por **Alejandro Figueroa Rojas** · Ingeniero Comercial — Data Science & Business Intelligence*
