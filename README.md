# Apophis Asteroid Project

<div align="center">
  <img
    src="https://media.giphy.com/media/v1.Y2lkPWVjZjA1ZTQ3YjhzdTg4ZXducGZpZXU0aWYzc3ZtZ2lsdDM4ZTNydTI1dXg3ZWlieSZlcD12MV9naWZzX3JlbGF0ZWQmY3Q9Zw/CFONrl19EZ0s0/giphy.gif"
    alt="Apophis GIF"
    width="520"
  />
</div>

# (99942) Apophis — Aproximación a la Tierra en abril de 2029

**Soleil Dayana Niño Murcia · Universidad de Antioquia · Mecánica Celeste**

Estudio numérico del sobrevuelo de (99942) Apophis en abril de 2029, abordado como un problema de dinámica orbital jerárquica: desde una referencia kepleriana hasta un esquema completo de N-cuerpos con efemérides reales de JPL Horizons.

---

## Pregunta central

¿De qué manera la inclusión de perturbadores planetarios y el refinamiento de la resolución temporal alteran la predicción de la distancia mínima Tierra–Apophis y su interpretación energética?

---

## Estructura del repositorio

```
Apophis-Asteroid-Project/
├── main.ipynb          # Notebook principal (reporte integrado)
├── modelos/            # Rama: integrador N-cuerpos y jerarquía de modelos
└── analisis/           # Rama: análisis de cuadraturas, elementos orbitales, CRTBP
```

El desarrollo del proyecto sigue una estrategia de complejidad progresiva con cinco modelos:

| Modelo | Cuerpos incluidos |
|:--|:--|
| **SEA (3C)** | Sol – Tierra – Apophis |
| **SEMA (4C)** | + Luna |
| **SEMAJ (5C)** | + Júpiter |
| **SEMAJV (6C)** | + Venus |
| **9C** | + Mercurio, Marte, Saturno (modelo de referencia final) |

---

## Contenido del notebook principal

1. **Comparación de modelos** — convergencia de la distancia mínima al aumentar la complejidad física
2. **Refinamiento temporal** — zoom de alta resolución (±30 días, 4200 pasos) alrededor del encuentro
3. **Visualizaciones del modelo final** — curva de distancia, conservación de energía, plano eclíptico XY, animación geocéntrica, comparación 3D Tierra–Luna–Apophis
4. **Cuadraturas del problema Sol–Apophis** — verificación de la conservación del momento angular (h), energía relativa (ε) y vector de Laplace (e_L)
5. **Elementos orbitales osculatrices** — evolución de a, e, i, Ω, ω, f durante el sobrevuelo; visualizador 3D interactivo
6. **Anomalías (M, E, f)** — solución de la ecuación de Kepler vía Newton-Raphson y animación del ciclo orbital completo
7. **Hodógrafo de velocidades** — ajuste circular y análisis de la desviación perturbativa
8. **Marco CRTBP y constante de Jacobi** — curvas de velocidad cero, trayectoria en el frame rotante, puntos de Lagrange, superficie del potencial modificado
9. **Conclusiones** — síntesis de 5 hallazgos físicos y computacionales

---

## Resultados principales

| Magnitud | Valor |
|:--|:--|
| Distancia mínima (modelo 9C) | ~38 400 km (~6 R⊕) |
| Fecha del perigeo refinado | 14 de abril de 2029, ~00:10 UTC |
| Error relativo de energía | < 10⁻¹⁰ |
| Semieje mayor post-encuentro | ~1.10 AU (vs 0.92 AU previo) |
| Constante de Jacobi C_J | < C_J(L1), C_J(L2) → barreras energéticas abiertas |

---

## Dependencias

```bash
pip install pymcel scipy matplotlib pandas plotly spiceypy
```

Las condiciones iniciales se descargan automáticamente desde **JPL Horizons** (`pc.consulta_horizons`) en marco baricéntrico (`location='@0'`). Se requiere conexión a internet al ejecutar la sección de preparación del entorno.

---

## Fuente de datos

JPL Horizons System, NASA/Jet Propulsion Laboratory
[https://ssd.jpl.nasa.gov/horizons/](https://ssd.jpl.nasa.gov/horizons/)
