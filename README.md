## 💻 Proyecto de Simulación de Fabricación de Computadoras

[cite_start]Este proyecto desarrolla una **simulación de eventos discretos** para modelar una línea de producción de computadoras[cite: 9, 11]. [cite_start]Utiliza la librería **SimPy** para simular la fabricación, el transporte y el ensamblaje final de los componentes principales de un equipo[cite: 10, 11]. [cite_start]El sistema incluye la gestión de recursos limitados, fallos probabilísticos con reintentos automáticos [cite: 13, 45][cite_start], y tiempos de ensamblaje dinámicos calculados mediante **Lógica Difusa (Fuzzy Logic)**[cite: 31, 50].

---

### ⚙️ Estructura y Funcionamiento del Sistema

[cite_start]El proyecto sigue un enfoque **modular y orientado a procesos** en Python, utilizando SimPy para gestionar los flujos[cite: 58, 59].

#### 1. Módulos Principales

| Módulo | Directorio | Descripción |
| :--- | :--- | :--- |
| `main_fabric.py` | `Trabajo/` | Es el **punto de entrada** y orquestador. [cite_start]Inicializa el entorno SimPy, define los recursos y coordina el flujo general de la simulación[cite: 65, 67, 69]. |
| `components/` | `components/` | Contiene los procesos para la producción de cada componente (e.g., `processor`, `RAM`). [cite_start]Gestiona tiempos de producción variables y el mecanismo de reintento de fallos[cite: 71, 72]. |
| `final_assembly.py` | `core/` | [cite_start]Gestiona el **ensamblaje final** del producto (la computadora) una vez que todos los componentes requeridos han llegado al almacén[cite: 79, 80]. |
| `fuzzy_logic.py` | `logic/` | Implementa el sistema de **Lógica Difusa** usando `scikit-fuzzy` para la toma de decisiones y el cálculo de tiempos[cite: 82, 84]. |
| `transport.py` | `Trabajo/` | [cite_start]Modela el **transporte** de los componentes desde las subfábricas hasta la fábrica principal, incluyendo **retrasos aleatorios**[cite: 20, 54, 75, 76]. |

#### 2. Mecanismos Clave

* [cite_start]**Tiempos Dinámicos (Fuzzy Logic):** El tiempo de ensamblaje principal (`Main_Assembly_Time`) se calcula dinámicamente utilizando lógica difusa[cite: 50, 51]. [cite_start]La entrada se basa en la **dificultad** del componente y la **carga del sistema** (`system_load`) para mejorar el realismo[cite: 52].
* [cite_start]**Tolerancia a Fallos y Reintentos:** Cada proceso de fabricación de componente tiene una **probabilidad de fallo del 10%**[cite: 13]. [cite_start]Si ocurre un fallo, el proceso se reinicia automáticamente, permitiendo hasta un máximo de **3 reintentos** (`max_retries = 3`) antes de declarar un fallo crítico[cite: 13, 45].
* [cite_start]**Ensamblaje Final:** El proceso final verifica la disponibilidad de los 8 componentes requeridos: `Processor`, `GraphicsCard`, `Storage`, `Box`, `PowerSupply`, `RAM`, `Motherboard`, `CoolingSystem`[cite: 46, 47].

---

### 📂 Estructura de Directorios
Trabajo/ ├── main_fabric.py # Fábrica principal, ejecuta la simulación general 
├── transport.py # Transporte de componentes 
├── components/ # Procesos individuales para cada componente │ 
├── box.py # Fabricación del Case/Caja │ 
├── cooling_system.py # Fabricación del Sistema de Refrigeración │ 
├── graphics_card.py # Fabricación de la Tarjeta Gráfica │ 
├── mother_board.py # Fabricación de la Placa Base │ 
├── power_supply.py # Fabricación de la Fuente de Poder │ 
├── processor.py # Fabricación del Procesador │ 
├── ram.py # Fabricación de la Memoria RAM │ 
└── storage.py # Fabricación de la Unidad de Almacenamiento 
├── core/ # Procesos adicionales del sistema │ 
└── final_assembly.py # Ensamblaje final en la fábrica principal ├
── logic/ # Lógica y procesos de toma de decisiones │ 
└── fuzzy_logic.py # Sistema de lógica difusa ├
── simulation_results.csv # Archivo de salida de los resultados de la simulación  
└── doc/ 
└── Computer_Manufacturing_Simulation.pdf # Documentación (Memoria)
---

### 🛠️ Librerías de Python Utilizadas

El proyecto utiliza las siguientes librerías[cite: 85]:

* **SimPy**: Framework de simulación de eventos discretos[cite: 86].
* **scikit-fuzzy (`skfuzzy`)**: Implementa la lógica difusa[cite: 93].
* **random**: Se utiliza para generar retrasos y simular fallos[cite: 87].
* **pandas**: Utilizado para procesar y exportar los resultados de la simulación[cite: 88].
* **numpy / itertools**: Proporcionan soporte numérico[cite: 91, 92].
* **GitHub**: Utilizado para el control de versiones[cite: 14, 95].

---

### 📖 Documentación Adicional

Para una explicación **más detallada** del diseño del código, la implementación de la lógica difusa, los escenarios simulados y el análisis de los resultados, consulte la memoria completa del proyecto:

* **`doc/Computer_Manufacturing_Simulation.pdf`**
