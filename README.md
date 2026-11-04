# Un qubit como superposición de ondas

Widget interactivo del **Taller 1, punto 1.2** de *Introducción a la Computación Cuántica*
(Universidad Nacional de Colombia, sede Medellín).

Los estados $|0\rangle \leftrightarrow \cos t$ y $|1\rangle \leftrightarrow \cos 2t$, con la
multiplicación $(Ae^{ix})\cdot\cos nt = A\cos(nt-x)$, forman el espacio de estados de un qubit.
El widget muestra un mismo estado $|\psi\rangle = \alpha|0\rangle + \beta|1\rangle$ en tres paneles
enlazados:

- **(a) Plano complejo**, donde se eligen $\alpha$ y $\beta$.
- **(b) Ondas** $\alpha|0\rangle$, $\beta|1\rangle$ y su superposición $\psi(t)$.
- **(c) Esfera de Bloch**, con el punto que corresponde a $|\psi\rangle$.

![Los tres paneles del widget](figuras/widget_punto_1_2.png)

## Cómo usarlo

**En el navegador (sin instalar nada):** abrir la página publicada con GitHub Pages,
<https://mariasaurius.github.io/taller1-computacion-cuantica/>. La página también muestra un
resumen de las fórmulas para pasar de cada panel a los demás.

**En Python (Jupyter):** abrir `notebooks/punto_1_2_widget.ipynb`. Requiere

```bash
pip install numpy matplotlib ipympl ipywidgets
```

El notebook es la versión de referencia: define las fórmulas como funciones reutilizables
(para los puntos siguientes del taller) y verifica numéricamente que todas son consistentes.

## Punto 1.5: implementación en Qiskit

El notebook `notebooks/punto_1_5_qiskit.ipynb` implementa en Qiskit los puntos 1.3 y 1.4 para un
estado $|\psi\rangle=\alpha|0\rangle+\beta|1\rangle$ cualquiera:

- **(a)** construye las soluciones $|\psi'\rangle$ del punto 1.3 y comprueba que tienen las mismas
  probabilidades que $|\psi\rangle$ y que la suma $|\psi\rangle+e^{i\eta}|\psi'\rangle$ es $|1\rangle$ salvo fase global;
- **(b)** construye los estados mixtos $p\rho+(1-p)\rho'$ del punto 1.4 y comprueba que tienen las
  mismas probabilidades de medición;
- **(c)** calcula los vectores de Bloch de todos esos estados y los compara con el widget.

Las probabilidades exactas se comparan con las frecuencias de mediciones simuladas (4000 por estado),
y al final todas las comprobaciones se repiten con 200 estados elegidos al azar. Requiere

```bash
pip install qiskit matplotlib pandas pylatexenc sympy
```

![Esfera de Bloch del punto 1.5](figuras/punto_1_5_bloch_qiskit.png)

## Estructura

| Archivo | Contenido |
|---|---|
| `index.html` | Página web: el widget en JavaScript y el resumen de fórmulas (KaTeX). |
| `notebooks/punto_1_2_widget.ipynb` | El mismo widget en Python con `ipywidgets` e `ipympl`, más las verificaciones. |
| `notebooks/punto_1_5_qiskit.ipynb` | Solución del punto 1.5: los puntos 1.3 y 1.4 implementados en Qiskit. |
| `figuras/` | Captura de los tres paneles y la esfera de Bloch del punto 1.5. |

Las dos versiones implementan las mismas fórmulas; la de JavaScript existe para que el widget
funcione en GitHub Pages, que solo sirve archivos estáticos y no puede ejecutar Python.
