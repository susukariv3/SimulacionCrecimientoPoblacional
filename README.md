import numpy as np
import matplotlib.pyplot as plt

def exponential_growth(initial_population, growth_rate, time_steps):
    """
    Calcula el crecimiento de la población a lo largo del tiempo utilizando el modelo de crecimiento exponencial.
    Parámetros:
    initial_population (float): Tamaño de población inicial.
    growth_rate (float): Tasa de crecimiento constante.
    time_steps (int): Número de pasos de tiempo a proyectar.
    Devuelve:
    population (np.array): Vector con los tamaños de población a lo largo del tiempo.
    """
    population = [initial_population]
    for t in range(1, time_steps):
        next_population = population[-1] * (1 + growth_rate)
        population.append(next_population)
    return np.array(population)

def plot_growth(population, time_steps):
    """
    Grafica el crecimiento de la población a lo largo del tiempo.
    Parámetros:
    population (np.array): Vector con los tamaños de población a lo largo del tiempo.
    time_steps (int): Número de pasos de tiempo.
    """
    time = np.arange(time_steps)
    plt.figure(figsize=(10, 6))
    plt.plot(time, population)
    plt.xlabel('Tiempo')
    plt.ylabel('Tamaño de Población')
    plt.title('Crecimiento Exponencial de Población')
    plt.grid()

    # Muestra la explicación de la gráfica debajo de la misma
    plt.text(0.5, -0.15, 'La gráfica muestra el crecimiento exponencial de la población a lo largo del tiempo. '
                        'El eje horizontal representa el tiempo en pasos discretos, mientras que el eje vertical '
                        'representa el tamaño de la población. La curva de crecimiento refleja la aceleración '
                        'del crecimiento de la población a medida que el tiempo avanza, característica del modelo '
                        'exponencial de crecimiento.',
             horizontalalignment='center', transform=plt.gca().transAxes, fontsize=10)
    plt.show()

# Entrada del usuario
initial_population = float(input("Ingresa el tamaño de población inicial: "))
growth_rate = float(input("Ingresa la tasa de crecimiento (ej., 0.05 para 5% de crecimiento): "))
time_steps = int(input("Ingresa el número de pasos de tiempo a proyectar: "))

# Calcular y graficar el crecimiento de la población
population = exponential_growth(initial_population, growth_rate, time_steps)
plot_growth(population, time_steps)
