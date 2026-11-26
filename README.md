# SolucionAutomaticaProblemas

# Buscaminas como Sistema Experto

Implementación del juego Buscaminas formulado como un entorno de razonamiento deductivo y probabilístico bajo información parcial. El proyecto compara tres estrategias desarrolladas desde cero (sin librerías externas de resolución) para inferir qué casillas ocultas contienen minas y cuáles son seguras, recurriendo únicamente a selección aleatoria pura cuando la deducción lógica no basta.

---

## Estrategias Implementadas

1. **Encadenamiento hacia Adelante (`AgenteForwardChaining`):** Estrategia guiada por los datos. Parte de los números visibles en la frontera y aplica reglas de inferencia local de forma iterativa hasta saturar la base de hechos (casillas seguras y minas). Si se atasca, selecciona una casilla oculta al azar.
2. **Encadenamiento hacia Atrás (`AgenteBackwardChaining`):** Estrategia guiada por objetivos. Formula hipótesis sobre casillas candidatas en la frontera (¿es mina? o ¿es segura) y busca recursivamente hacia atrás en las restricciones numéricas adyacentes para demostrarlas. Si ninguna hipótesis es demostrable, elige al azar.
3. **Simulación de Monte Carlo (`AgenteMonteCarlo`):** Ante bloqueos o incertidumbre en la frontera, modela el problema como un CSP (Problema de Satisfacción de Restricciones) y genera $N$ configuraciones válidas mediante *backtracking* estocástico con poda temprana. Calcula la frecuencia empírica de mina por casilla para actuar con certeza (0% o 100%) o minimizar el riesgo.

---

## Características del Entorno

* **Primera jugada siempre segura:** El mapa de minas se genera de forma diferida tras la primera selección, excluyendo la casilla inicial y su vecindad inmediata.
* **Niveles configurables y reproducibilidad:** Soporta Principiante (10x10, 10 minas), Intermedio (16x16, 40 minas), Experto (16x30, 99 minas) y semillas aleatorias fijas para comparar algoritmos en igualdad de condiciones.
* **Interfaz Visual Interactiva:** Compatible y realizado en Google Colab. Utilizable en Jupyter Notebook mediante `ipywidgets`, con ejecución automática, modo paso a paso, modo manual por clics y resaltado visual de las deducciones (verde: segura, rojo: mina, naranja: azar).

---

## Estructura del Repositorio

```text
├── Buscaminas_Sistema_Experto.ipynb   # Notebook principal (Entorno, Agentes, Benchmark e Interfaz)
├── informe_tecnico.tex                # Código fuente en LaTeX del artículo técnico
├── requirements.txt                   # Dependencias del entorno de ejecución
└── README.md                          # Documentación del proyecto
