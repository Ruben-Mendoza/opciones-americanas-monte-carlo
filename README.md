# opciones-americanas-monte-carlo
Implementación del algoritmo de Tilley para valoración de opciones americanas con Monte Carlo · FAMAF-UNC

# Algoritmo de Tilley para Valoración de Opciones Americanas mediante Simulación de Monte Carlo

> Proyecto final — **Matemática Financiera**  
> Licenciatura en Matemática Aplicada · FAMAF, Universidad Nacional de Córdoba
> 
---

## Descripción

Implementación y validación del **algoritmo de Tilley (1993)** para valuar opciones americanas mediante simulación de Monte Carlo. El método adapta las simulaciones de Monte Carlo para manejar la decisión de ejercicio anticipado mediante un esquema de **agrupamiento de trayectorias** e **inducción hacia atrás**.

El precio del activo subyacente se modela bajo un **Movimiento Geométrico Browniano** (medida de riesgo neutral):

$$S_{t+\Delta t} = S_t \exp\!\left[\left(r - \tfrac{1}{2}\sigma^2\right)\Delta t + \sigma\sqrt{\Delta t}\, Z_t\right], \quad Z_t \sim \mathcal{N}(0,1)$$

### Experimentos realizados

1. **Validación:** comparación de calls americanas vs. europeas (en ausencia de dividendos, sus precios deben coincidir). Resultado vs. Black-Scholes: diferencia por error de aproximación, con convergencia al valor teórico al aumentar R.
2. **Replicación:** valoración de una put americana con los parámetros de Tilley (1993). Precio estimado: 7,89 vs. valor de referencia (árbol binomial, 1200 pasos): 7,94.
3. **Efecto del límite nítido de ejercicio (subpaso 6):** ejecutar el subpaso de determinación del límite nítido reduce el rango de variación de la prima a la mitad.
4. **Convergencia con R:** al aumentar el número de trayectorias, la varianza disminuye sistemáticamente y la estimación converge.

---

## Tecnologías y herramientas

- **Lenguaje:** Python 3
- **Bibliotecas:** `numpy`, `matplotlib`
- **Documentación:** LaTeX

---

## Parámetros del experimento principal (replicación de Tilley)

| Parámetro | Valor |
|-----------|-------|
| Precio inicial S₀ | 40 |
| Strike K | 45 |
| Vencimiento T | 3 años |
| Tasa libre de riesgo r | 7% |
| Volatilidad σ | 30% |
| Pasos de ejercicio N | 12 (trimestral) |
| Trayectorias R | 5040 |
