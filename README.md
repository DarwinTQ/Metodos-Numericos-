# Resolución de Ejercicios Numéricos en MATLAB

**Introducción**

Este documento presenta la resolución de diversos ejercicios mediante la aplicación de métodos numéricos en MATLAB, como los métodos de Newton, Secante, Bisección, Regla Falsa, Punto Fijo, Eliminación Gaussiana, Factorización LU, Jacobi, y Gauss-Seidel. Estas técnicas son esenciales en ingeniería y ciencias aplicadas, ya que permiten encontrar raíces de funciones no lineales, resolver sistemas de ecuaciones y aproximar soluciones con gran precisión.

<details>
<summary>🔍 Descripción de los Métodos</summary>

1. **Método de Newton**  
   Un algoritmo iterativo que converge rápidamente para aproximarse a las raíces de funciones, especialmente útil cuando la solución inicial está cercana a la raíz.

2. **Método de la Secante**  
   Variante del Método de Newton que no requiere la derivada de la función, útil cuando la derivada no está disponible o es difícil de obtener.

3. **Método de Bisección**  
   Técnica de búsqueda de raíces que garantiza la convergencia, adecuada para funciones continuas y bien definidas en un intervalo.

4. **Método de Regla Falsa**  
   Alternativa a la Bisección que suele converger más rápidamente al usar una interpolación lineal.

5. **Punto Fijo**  
   Método que encuentra puntos invariantes en funciones; útil para algunos sistemas no lineales.

6. **Eliminación Gaussiana y Factorización LU**  
   Métodos para resolver sistemas de ecuaciones lineales.

7. **Métodos Iterativos (Jacobi y Gauss-Seidel)**  
   Técnicas usadas en sistemas grandes y dispersos, comunes en aplicaciones de ingeniería.

</details>

### 🔧 Ejemplo de Aplicación en Telecomunicaciones

En telecomunicaciones, calcular la **atenuación óptima** en una fibra óptica es crucial para minimizar la pérdida de señal. Por ejemplo, con el Método de Bisección, podemos encontrar el valor óptimo de potencia de señal en una sección de fibra óptica, minimizando las pérdidas según una función de pérdida dada.

<details>
<summary>💻 Código de Ejemplo en MATLAB</summary>

```matlab
% Valores de ejemplo
a = input("Ingrese el valor de a= ");
b = input("Ingrese el valor de b= ");
tol = input("Ingrese el valor de tol= ");
f = input("Ingrese la función f= ", 's');
f = inline(f);
k = 1;
m = (a + b) / 2;

fprintf('k\tak\t\tbk\t\tmk\t\terror\n');

fa = f(a);
fm = f(m);

while (b - a) / 2 > tol
    fprintf('%d\t%f\t%f\t%f\t%f\n', k, a, b, m, (b - a) / 2);
    
    if fa * fm < 0  
        b = m;      
    else
        a = m;      
        fa = fm;    
    end
    
    m = (a + b) / 2;
    fm = f(m); 
    k = k + 1;  
end
fprintf('La raíz aproximada es m = %f\n', m);
