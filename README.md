# Taller 1: Repaso Scripting

## Integrntes: 
Sofía Caraballo, Jacobo Rodríguez, Nicole Livingston

## 1. Escoja 7 enunciados: 

➨ 2 sobre uso de funciones

➨ 1 sobre arreglos o matrices

➨ 1 sobre cadenas

➨ 1 sobre condiciones o ciclos

➨ 2 preguntas de teoría

## Funciones (2)
• 11. Cree un menú infinito con 3 opciones para realizar operaciones sencillas. 
```c#
namespace Application
{
    class Program
    {
       static void Main(string[] args)
        {
            
            bool bandera = true;
            while (bandera){
                Console.Clear();
                bandera = false;
            Console.WriteLine("Bienvenido a la mini calculadora selecciona una de las 3 operaciones que desees realizar");
            Console.WriteLine("1. Suma ");
            Console.WriteLine("2. Resta ");
            Console.WriteLine("3. Multiplicación ");
            Console.WriteLine("0. Salir ");
              Console.Write("Selecciona una opción: ");
            int input = int.Parse(Console.ReadLine());
           if(input > 3 || input < 0){
            Console.WriteLine("Selecciona una opcion válida");
            bandera = true;
           }
           switch(input){
        case 1:
            Console.Clear();
            Console.WriteLine("A sumar! ingresa el primer numero");
            double numero1 = double.Parse(Console.ReadLine());
            Console.WriteLine("Ingresa el segundo numero");
            double numero2 = double.Parse(Console.ReadLine());
            double resultado = Suma(numero1, numero2);
            Console.WriteLine("El resultado es " + resultado);
            break;
            
        case 2:
        Console.Clear();
            Console.WriteLine("A restar! ingresa el primer numero");
            numero1 = double.Parse(Console.ReadLine());
            Console.WriteLine("Ingresa el segundo numero");
            numero2 = double.Parse(Console.ReadLine());
            resultado = Resta(numero1, numero2);
            Console.WriteLine("El resultado es " + resultado);
            break;

        case 3:
            Console.Clear();
            Console.WriteLine("A multiplicar! ingresa el primer numero");
            numero1 = double.Parse(Console.ReadLine());
            Console.WriteLine("Ingresa el segundo numero");
            numero2 = double.Parse(Console.ReadLine());
            resultado = Multiplicacion(numero1, numero2);
            Console.WriteLine("El resultado es " + resultado);
            break;

        case 0:
            bandera = false;
            break;
    }
    if (input != 0) {
    Console.WriteLine("Presiona cualquier tecla para volver al menú...");
    Console.ReadKey();
    bandera = true;
}
            }
           
    }
    static double Suma(double a, double b){
        return a+b;
    }
   static double Resta(double a, double b){
        return a-b;
    }
 static   double Multiplicacion(double a, double b){
        return a*b;
    }
    }
}
```
• 18. Realice una función, que lea un número de máximo 8 cifras y luego sume cada dígito hasta obtener un valor de un solo dígito.

### Solución 
```c#
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Ingresa un número de hasta 8 cifras:");
            decimal numero = decimal.Parse(Console.ReadLine()); 

            int suma = SumarDigitos(numero); 
            Console.WriteLine("El resultado es: " + suma); 
        }

        static int SumarDigitos(decimal numero)
        {
            int suma = 0;

            while (numero > 0)
            {
                suma += (int)(numero % 10); 
                numero /= 10; 
            }

            while (suma >= 10)
            {
                int tempSuma = 0;
                while (suma > 0)
                {
                    tempSuma += suma % 10; 
                    suma /= 10; 
                }
                suma = tempSuma; 
            }

            return suma; 
        }
    }
}
```

## Arreglos o matrices (1)
• 10. Lea una matriz 3D, luego cree 3 arreglos a partir de la matriz leída

### Solución 
```c#
    internal class Program
    {
        static void Main(string[] args)
        {
            int columnas = 0;


            Console.WriteLine("Bienvenido al creador de matrices 3xn, cuantas columnas le quieres dar a la matriz?");
            columnas = int.Parse(Console.ReadLine());
            int[,] matriz = new int[3, columnas];
            Console.WriteLine("LLenemos esa matriz " + 3 + "x" + columnas);
            for (int i = 0; i < matriz.GetLength(0); i++)
            {
                for (int j = 0; j < matriz.GetLength(1); j++)
                {
                    Console.WriteLine("Ingrese el numero para la fila " + (i + 1) + " y la columna " + (j + 1));
                    int numero = int.Parse(Console.ReadLine());
                    matriz[i, j] = numero;
                }
            }
            Console.WriteLine("Ahora vamos a mostrar 3 arreglos con los numeros que llenaste, el arreglo serán las filas de esta matriz:");
            for (int i = 0; i < matriz.GetLength(0); i++)
            {
                Console.WriteLine();
                Console.WriteLine("Fila numero " + (i + 1));
                for (int j = 0; j < matriz.GetLength(1); j++)
                {
                    Console.Write(matriz[i, j] + " | ");
                }
            }
        }
    }
}
```


## Cadenas (1)
• 7. Lea una cadena de números enteros positivos y luego cree un array con los números de la cadena, se debe validar que la cadena obtenga números.
```c#
namespace Application
{
    class Program
    {
        static int tamanocadena = 0;
        static bool positivo = true;
        static void Main(string[] args)
        {
            
            Console.WriteLine("Por favor ingrese el tamaño que quiere para su cadena de números");
            int respuesta = int.Parse(Console.ReadLine());
            tamanocadena = respuesta;
            int[] cadena = new int[respuesta];
            Console.WriteLine("Creaste una cadena de " + tamanocadena + " numeros ahora llenemosla");
            for (int i = 0; i < cadena.Length; i++)
            {
                positivo=true;
                Console.WriteLine("Ingrese el numero " + (i+1) + " De la cadena: ");
                while (positivo){
                int numero = int.Parse(Console.ReadLine());
                if (numero <=0){
                    Console.WriteLine("por favor ingresa un número entero positivo");

                }
                else{
                    cadena[i] = numero;
                    positivo=false;
                }
                }
              
                
            }
            Console.WriteLine("A continuación la cadena que ingresaste");
            for (int i = 0; i < cadena.Length; i++)
            {
                Console.Write(cadena[i] + " | ");
            }
        }
    
    }
}
```

## Condiciones o Ciclos (1)
• 29. Usando un ciclo for, calcule el factorial de un número n, tenga en cuenta validar los casos especiales.
```c#
class Program
    {
        static void Main()
        {
            Console.Write("Ingrese un número para calcular su factorial: ");
            int n = int.Parse(Console.ReadLine());

            if (n < 0)
            {
                Console.WriteLine("El factorial no está definido para números negativos.");
                return;
            }

            long factorial = 1;

            for (int i = 1; i <= n; i++)
            {
                factorial *= i;
            }

            Console.WriteLine("El factorial de " + n + " es " + factorial + ".");
          
        }
    }
}
```
    
## Teoría (2)
• 12. Realice 5 condicionales usando los diferentes operadores.

### Solución 

#### Operador == (igualdad)
Compara si dos valores son exactamente iguales.

```c#
    internal class Program
    {
        static void Main(string[] args)
        {
            //Operador ==
            Console.Write("Ingresa tu salario: ");
            decimal salario = Convert.ToDecimal(Console.ReadLine());

            decimal salarioMinimo = 1423500;

            if (salario == salarioMinimo)
            {
                Console.WriteLine("Usted gana un salario mínimo legal vigente");
            }
            else
            {
                Console.WriteLine("Usted gana un valor diferente al salario mínimo legal vigente");
            }
        }
    }
}
```
#### Operador && (y lógico)
Evalúa si ambas condiciones son verdaderas para ejecutar un bloque de código.

```c#
internal class Program
    {
        static void Main(string[] args)
        {
            //Operador &&
            Console.Write("Ingresa la hora formato 24h (sin minutos): ");
            int hora = Convert.ToInt32(Console.ReadLine());

            Console.Write("Ingresa el día de la semana: ");
            string dia = Console.ReadLine();

            if (hora >= 10 && hora <= 14 && dia == "Viernes" || dia == "viernes")
            {
                Console.WriteLine("Debes estar en clase de Scripting");
            }
            else
            {
                Console.WriteLine("No estás en clase de Scripting");
            }
        }
    }
}
```
#### Operador >= o < (Mayor o igual que - Menor)
Verifica si un valor es mayor o igual a otro o compara si un valor es estrictamente menor que otro.

```c#
internal class Program
    {
        static void Main(string[] args)
        {
            //Operador >= o <
            int semestre = 0;
 
            Console.WriteLine("¿Cuál semestre estas cursando actualmente? (1-8)");
            semestre = int.Parse(Console.ReadLine());
 
            if (semestre >= 1 && semestre < 4)
            {
                Console.WriteLine("Estás cursando los primeros semestres de tu carrera, apenas estas iniciando");
            }
            if (semestre >= 4 && semestre < 7)
            {
                Console.WriteLine("Estás en la mitad de la carrera, ya has avanzado un poco");
            }
            if (semestre >= 7)
            {
                Console.WriteLine("Pronto terminarás la carrera, no te rindas");
            }
        }
    }
}
```
#### Operador != (Diferente de)
Compara si un valor es diferente de otro.

```c#
internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Ingresa las siglas de tu carrera:");
            string palabra = Console.ReadLine();

            if (palabra != "ided" && palabra != "IDED")
            {
                Console.WriteLine("Estudias una carrera distinta a IDED");
            }
            else
            {
                Console.WriteLine("Estudias IDED, eres lo máximo");
            }
        }
    }
}
```


#### Operador || (OR lógico)
Evalúa si al menos una de dos condiciones es verdadera.
```c#
internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Ingresa un número:");
            int numero = int.Parse(Console.ReadLine());

            // Verificar si el número es negativo o igual a cero
            if (numero < 0 || numero == 0)
            {
                Console.WriteLine("El número es negativo o igual a cero.");
            }
            else
            {
                Console.WriteLine("El número es positivo.");
            }
        }
    }
}

```
• 7. Escriba 10 palabras reservadas

### Solución 

1- int: Define variables de tipo entero.

2- if: Establece una condición.

3- else: Define qué hacer si la condición no se cumple.

4- for: Crea un bucle controlado por un contador.

5- while: Crea un bucle basado en una condición.

6- return: Devuelve un valor desde una función.

7- float: Define variables de tipo decimal o punto flotante.

8- public: Define acceso libre para clases, métodos o variables.

9- private: Limita el acceso a elementos dentro de una clase.

10- static: Declara elementos que pertenecen a la clase, no a sus instancias.

#### ¿Por qué son palabras reservadas?

✦ Estas palabras son llamadas así porque tienen funciones específicas que el lenguaje interpreta para estructurar y ejecutar el código. No pueden usarse como nombres de variables u otros elementos, ya que el compilador las reconoce como comandos específicos asignadas a su propósito definido en el lenguaje.

## Firmas 
### 1- Sin parámetros y sin retorno

Descripción:
Esta función simplemente muestra un mensaje en la consola

#### Firma:
```c#
public static void SaludarAlumnos()
```
#### Invocación:
```c#
SaludarAlumnos();
```
### 2- Con parámetros y con retorno

Descripción:
Suma dos números enteros y devuelve el resultado.

#### Firma:
```c#
public static int Sumar(int a, int b)
```
#### Invocación:
```c#
int resultado = Sumar(5, 7);
```
### 3- Con parámetros y sin retorno
Descripción:
Recibe un nombre y lo imprime en pantalla.

#### Firma:
```c#
public static void MostrarNombre(string nombre)
```
#### Invocación:
```c#
MostrarNombre("Marco Solis");
```
### 4- Devuelve un arreglo
Descripción:
Genera un arreglo con los primeros n números pares.

#### Firma:
```c#
public static int[] GenerarNumerosPares(int cantidad)
```
#### Invocación:
```c#
int[] pares = GenerarNumerosPares(5);
```

### 5- Sin retorno que imprime la fecha y hora actual
Descripción:
Imprime la fecha y hora actual en la consola.

#### Firma:
```c#
public static void MostrarFechaHoraActual()
```
#### Invocación:
```c#
MostrarFechaHoraActual();
```

### 6- Invierte una cadena de texto
Descripción:
Recibe un texto y devuelve el mismo texto pero al revés.

#### Firma:
```c#
static string InvertirCadena(string texto)
```
#### Invocación:
```c#
string invertido = InvertirCadena("Scripting");
```
### 7- Cuenta los elementos de un array
Descripción:
Recibe un array de enteros y devuelve la cantidad de elementos en él.

#### Firma:
```c#
private static int ContarElementosArray(int[] array)
```
#### Invocación:
```c#
int cantidad = ContarElementosArray(new int[] { 1, 2, 3, 4, 5 });
```

### 8- Concatena dos cadenas
Descripción:
Une dos cadenas de texto en una sola y la retorna.

#### Firma:
```c#
protected static string ConcatenarTexto(string texto1, string texto2)
```
#### Invocación:
```c#
string resultado = ConcatenarTexto("Taller", "Repaso");
```

### 9- Valida si un string es un número entero
Descripción:
Devuelve true si el string es un número entero válido.

#### Firma:
```c#
protected static bool EsNumeroEntero(string texto)
```
#### Invocación:
```c#
bool valido = EsNumeroEntero("1234");
```

### 10- Muestra los elementos de una lista
Descripción:
Este método recibe un arreglo de cadenas e imprime cada elemento en una nueva línea.

#### Firma:
```c#
public static void MostrarLista(string[] elementos)
```
#### Invocación:
```c#
MostrarLista(new string[] { "Sofía", "Nicole", "Jacobo" });
```

### 11- Dibujar un cuadrado de asteriscos
Descripción:
Este método imprime en pantalla un cuadrado de asteriscos con el tamaño dado.

#### Firma:
```c#
static void DibujarCuadrado(int tamaño)
```
#### Invocación:
```c#
DibujarCuadrado(5);
```

### 12- Eliminar espacios de una cadena
Descripción:
Devuelve una cadena sin espacios en blanco.

#### Firma:
```c#
public static string EliminarEspacios(string texto)
```
#### Invocación:
```c#
string resultado = EliminarEspacios("Quiero Dormir");
```

### 13- Calcular la hipotenusa de un triángulo
Descripción:
Calcula la hipotenusa de un triángulo usando el Teorema de Pitágoras

#### Firma:
```c#
protected static double CalcularHipotenusa(double cateto1, double cateto2)
```
#### Invocación:
```c#
double hipotenusa = CalcularHipotenusa(3.0, 4.0);
```

### 14- Verificar si un número es primo
Descripción:
Devuelve true si el número es primo, false en caso contrario.

#### Firma:
```c#
private static bool EsPrimo(int numero)
```
#### Invocación:
```c#
bool esPrimo = EsPrimo(7);
```

### 15- Crear una matriz de números aleatorios
Descripción:
Genera una matriz de enteros con valores aleatorios.

#### Firma:
```c#
public static int[,] GenerarMatrizAleatoria(int filas, int columnas)
```
#### Invocación:
```c#
int[,] matriz = GenerarMatrizAleatoria(3, 3);
```

### 16- Simular el lanzamiento de un dado
Descripción:
Genera un número aleatorio entre 1 y 6

#### Firma:
```c#
private static int LanzarDado()
```
#### Invocación:
```c#
int resultado = LanzarDado();
```

### 17- Simular el lanzamiento de un dado
Descripción:
Genera un número aleatorio entre 1 y 6

#### Firma:
```c#
private static int LanzarDado()
```
#### Invocación:
```c#
int resultado = LanzarDado();
```
