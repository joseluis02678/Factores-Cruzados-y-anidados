<div align="center">

# Factores Cruzados y Anidados — Diseños Experimentales II 🧪

![R](https://img.shields.io/badge/R-276DC3?style=for-the-badge&logo=r&logoColor=white)
![Quarto](https://img.shields.io/badge/Quarto-4C78B7?style=for-the-badge&logo=quarto&logoColor=white)
![GAD](https://img.shields.io/badge/GAD_Package-006400?style=for-the-badge)

*Modelamiento de dos diseños factoriales mixtos — con estructuras de cruce y anidamiento distintas — verificando su coherencia teórica a través de los Cuadrados Medios Esperados.*

**[📄 Ver informe completo](https://joseluis02678.github.io/Factores-Cruzados-y-anidados/)** · **[💼 LinkedIn](https://www.linkedin.com/in/jose-l-garay/)**

</div>

---

## 🎯 ¿De qué trata este repositorio?

Este trabajo aborda un problema clásico y no trivial del diseño de experimentos: **cómo especificar y validar correctamente un modelo cuando los factores no están simplemente "cruzados", sino que algunos están anidados dentro de otros**. La forma en que se combinan factores fijos y aleatorios, cruzados y anidados, determina qué pruebas F son válidas y contra qué fuente de error debe contrastarse cada efecto — un error aquí invalida todo el análisis posterior, sin importar qué tan bien se ajuste el modelo en apariencia.

Se desarrollan y comparan dos casos sobre el mismo conjunto de datos experimentales (3 niveles de A × 4 niveles de B × 2 niveles de C × 3 repeticiones):

- **Caso 2 — A cruzado, B y C anidados:** `A`, `B(A)`, `C(AB)`. Sin interacciones, porque los factores anidados no interactúan con su anidador.
- **Caso 3 — A y C cruzados, B anidado en A:** `A`, `C`, `A×C`, `B(A)`, `B(A)×C`. Una estructura más compleja donde C sí cruza con A, pero B permanece anidado dentro de A.

Para cada caso se:
1. Deriva el **modelo teórico** (notación de Kempthorne) a partir de la estructura del diseño.
2. Ajusta el modelo en R respetando exactamente esa estructura, usando `lm()` con los operadores `*`, `%in%` y `:`.
3. Calcula el ANOVA con el paquete **GAD** (`gad()`), que asigna automáticamente el denominador F correcto a cada fuente de variación — algo que `anova()` base no siempre resuelve bien en diseños mixtos.
4. Verifica la coherencia del modelo contrastando los **Cuadrados Medios Esperados (CME)** reportados por `estimates()` contra la derivación teórica esperada para un diseño con A y C fijos y B aleatorio.

**Hallazgo clave:** La función `estimates()` reproduce exactamente los CME teóricos del Caso 3, confirmando que A se prueba correctamente contra B(A), mientras que C y A×C se prueban contra B(A)×C — no contra el residual, como asumiría un análisis ingenuo.

---

## 🛠️ Stack Tecnológico

| Categoría | Herramientas |
|---|---|
| Lenguaje | R |
| Diseño Mixto (Cruzado/Anidado) | `GAD` (`gad()`, `estimates()`, `as.fixed()`, `as.random()`) |
| Modelamiento | `lm()` con operadores `%in%`, `*`, `:` |
| Reportes | Quarto (`knitr`) |

---

## 📁 Estructura del Repositorio

```text
Factores-Cruzados-y-anidados/
│
├── 📖 README.md
├── 🧪 Factores_Cruzados_y_Anidados.qmd
├── 🌐 index.html
└── ⚙️ .gitignore
```

---

## 👨‍💻 Autor

**Jose Luis Garay Ramos**
Estudiante de Estadística especializado en transformar datos complejos en análisis interpretables mediante metodologías estadísticas sólidas y programación en R/Python.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/jose-l-garay/)
[![Correo](https://img.shields.io/badge/Correo-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:gaga4590joseluis@gmail.com)

---

📄 **[Ver informe completo](https://joseluis02678.github.io/Factores-Cruzados-y-anidados/)**
