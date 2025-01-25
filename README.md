# ViajeTuristicoOptimo
Generación de ruta optima de viaje a lugares turísticos en Nayarit por medio de la programación lineal en Python.

\documentclass{article}
\usepackage{amsmath}
\usepackage{hyperref}

\title{Resolución de Problema de Programación Lineal con Python y PuLP: TSP (Traveling Salesman Problem)}
\author{}
\date{}

\begin{document}

\maketitle

\section*{Enfoque}

\subsection*{1. Modelado del Problema}
El TSP fue formulado como un problema de programación lineal (PL). Para ello, se construyó una \textbf{matriz de costos} que representa la distancia o el costo entre cada par de ciudades. La matriz fue creada de manera que cada entrada $C_{ij}$ representa el costo de viajar de la ciudad $i$ a la ciudad $j$.

\subsection*{2. Uso de la librería PuLP}
Se utilizó la librería \textbf{PuLP} para definir y resolver el problema de programación lineal. PuLP permite la formulación de problemas de optimización de manera sencilla y eficiente. En este caso, el objetivo es minimizar el costo total del recorrido, sujeto a ciertas restricciones que aseguran la validez de la solución.

\subsection*{3. Restricciones}
Las restricciones del modelo fueron las siguientes:

\begin{itemize}
    \item \textbf{Restricción de un solo recorrido por ciudad:} Cada ciudad debe ser visitada exactamente una vez. Esto se logra con la restricción de que para cada ciudad, solo puede existir una salida y una entrada.
    
    \[
    \sum_{j \neq i} x_{ij} = 1 \quad \text{para cada ciudad } i
    \]
    \[
    \sum_{i \neq j} x_{ij} = 1 \quad \text{para cada ciudad } j
    \]
    
    \item \textbf{Restricción de ciclo:} Para evitar que la solución contenga ciclos subóptimos (por ejemplo, un ciclo que no visite todas las ciudades), se agregó una restricción basada en variables adicionales (subtour elimination). Esta restricción garantiza que no se formen ciclos menores a la ruta completa.
    
    \[
    u_i - u_j + n \cdot x_{ij} \leq n - 1 \quad \text{para todas las ciudades } i \neq j
    \]
    donde $u_i$ es una variable que representa el ``número de orden" de la ciudad $i$ en el recorrido.
\end{itemize}

\subsection*{4. Solución}
Una vez formulado el problema, se resolvió utilizando el solver de PuLP. El resultado es la ruta óptima, que minimiza el costo total del recorrido. El modelo también devuelve la secuencia de ciudades que debe seguir el vendedor para lograr la mínima distancia total.

\section*{Requisitos}

\begin{itemize}
    \item Python 3.x
    \item PuLP: \texttt{pip install pulp}
\end{itemize}

\section*{Ejecución}

\begin{enumerate}
    \item Clona este repositorio:
    \begin{verbatim}
    git clone https://github.com/tu_usuario/tu_repositorio.git
    \end{verbatim}
    
    \item Instala las dependencias necesarias:
    \begin{verbatim}
    pip install pulp
    \end{verbatim}
    
    \item Ejecuta el script principal:
    \begin{verbatim}
    python tsp_solver.py
    \end{verbatim}
    
    \item El programa resolverá el problema y mostrará la ruta óptima, así como el costo total del recorrido.
\end{enumerate}

\end{document}
