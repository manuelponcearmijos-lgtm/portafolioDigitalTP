```c
#include <stdio.h>

// Calcula el promedio de las notas del componente ACD (Actividades de Comunicación Docente)
// Pide primero la cantidad de trabajos y luego valida cada nota ingresada (rango 0-10) 
float calcularACD()
{
  int trabajo, k;
  float nota, total, acumulador = 0;

  
  // Valida que la cantidad de trabajos sea al menos 1
  do
  {
    printf("Cantidad de trabajos ACD:\n");
    scanf("%i", &trabajo);
 
  } while (trabajo < 1);
  
  // Recorre cada trabajo pidiendo su nota
  for (k = 1; k <= trabajo; k++)
  {
  // Valida que la nota esté en el rango permitido (0 a 10)
    do
    {
      printf("Nota de tus trabajos de ACD\n");
      scanf("%f", &nota);
    } while (nota > 10 || nota < 0);

    acumulador = acumulador + nota; // Suma acumulada de las notas
  }

  total = acumulador / trabajo; // Promedio simple de las notas ingresadas

  return total;
}

// Calcula el promedio de las notas del componente APE (Actividades Prácticas de Evaluación)
float calcularAPE()
{
  int trabajo, k;
  float nota, total, acumulador = 0;

  // Valida que la cantidad de trabajos sea al menos 1
  do
  {
    printf("Cantidad de trabajos APE:\n");
    scanf("%i", &trabajo);
  } while (trabajo < 1);

  // Recorre cada trabajo pidiendo su nota
  for (k = 1; k <= trabajo; k++)
  {
    // Valida que la nota esté en el rango permitido (0 a 10)
    do
    {
      printf("Nota de tus trabajos de APE\n");
      scanf("%f", &nota);
    } while (nota > 10 || nota < 0);

    acumulador = acumulador + nota; // Suma acumulada de las notas
  }

  total = acumulador / trabajo; // Promedio simple de las notas ingresadas
  return total;
}

// Calcula el promedio de las notas del componente AA (Aprendizaje Autónomo)
float calcularAA()
{
  int trabajo, k;
  float nota, total, acumulador = 0;

  // Valida que la cantidad de trabajos sea al menos 1
  do
  {
    printf("Cantidad de trabajos AA:\n");
    scanf("%i", &trabajo);
  } while (trabajo < 1);

  // Recorre cada trabajo pidiendo su nota
  for (k = 1; k <= trabajo; k++)
  {
    // Valida que la nota esté en el rango permitido (0 a 10)

    do
    {
      printf("Nota de tus trabajos de AA\n");
      scanf("%f", &nota);
    } while (nota > 10 || nota < 0);
    acumulador = acumulador + nota; // Suma acumulada de las notas
  }

  total = acumulador / trabajo; // Promedio simple de las notas ingresadas

  return total;
}

// Calcula la nota final del componente ES (Evaluación Sumativa),
// que combina Portafolio y Examen según un peso porcentual definido por el usuario
 float calcularES()
{
  const float PESO_ES = 0.35; // Peso del componente ES dentro de la nota final del ciclo (35%)
  float notaPortafolio, notaExamen;
  float pesoPortafolio, pesoExamen;
  float totalES;
  
  // Valida que el porcentaje del portafolio esté entre 1 y 100
  do{
    printf("Ingrese el porcentaje del Portafolio (0-100): ");
    scanf("%f", &pesoPortafolio);
   
  if (pesoPortafolio >100 || pesoPortafolio <1) 
    printf("Error: El peso del portafolio debe estar entre 1 y 100.\n");
  
  
}while(pesoPortafolio >100 || pesoPortafolio <1);
 
  // Valida que la nota del portafolio esté en el rango permitido (0 a 10)
  do {
    printf("Nota del Portafolio (0-10):\n");
    scanf("%f", &notaPortafolio);
  } while (notaPortafolio > 10 || notaPortafolio < 0);

  // Valida que la nota del examen esté en el rango permitido (0 a 10)
  do {
    printf("Nota del Examen (0-10):\n");
    scanf("%f", &notaExamen);
  } while (notaExamen > 10 || notaExamen < 0);

 pesoExamen= 100 - pesoPortafolio; // El peso del examen es el complemento del peso del portafolio
 
 // Nota ponderada de ES: combina portafolio y examen según sus pesos respectivos 
 totalES = (notaPortafolio * (pesoPortafolio / 100)) + (notaExamen * (pesoExamen / 100));

  // Se aplica el peso del componente ES (35%) sobre la nota final del ciclo
  return totalES * PESO_ES;
}

// Calcula y muestra el promedio final de todo el ciclo académico
// x: suma acumulada de los promedios de las unidades, y: número de unidades
void promedioFinal(float x , float y)
{
  float totalCiclo = 0;

  totalCiclo = x / y;// Promedio general del ciclo
  printf("El resultado de su promedio de Todo su Ciclo es: %.2f\n", totalCiclo);
  
  // Determina el estado académico final según el promedio obtenido
  if (totalCiclo >= 7)
    printf("Aprobado\n");
  else if (totalCiclo >= 2.5)
    printf("Supletorio\n");
  else
    printf("Reprobado, estudia más\n");
}

// Calcula el promedio ponderado de una unidad (s = número de unidad)
// combinando los cuatro componentes: ACD (20%), APE (25%), AA (20%) y ES (35)
float calcularPromedio(int s)
{

  float totalACD, totalAPE, totalAA, totalES, suma;

  printf("Promedio final de la Unidad:%i\n", s);
  
  // Componente ACD, ponderado al 20%
  totalACD = calcularACD();
  printf("=========================================\n");
  printf("El ponderado del ACD es: %.2f\n", totalACD * 0.2);
  printf("=========================================\n");

  // Componente APE, ponderado al 25%
  totalAPE = calcularAPE();
  printf("=========================================\n");
  printf("El ponderado del APE es: %.2f\n", totalAPE * 0.25);
  printf("=========================================\n");

  // Componente AA, ponderado al 20%
  totalAA = calcularAA();
  printf("=========================================\n");
  printf("El ponderado del AA   es: %.2f\n", totalAA * 0.2);
  printf("=========================================\n");

  // Componente ES, ya viene ponderado al 35% desde calcularES()
  totalES = calcularES();
  printf("=========================================\n");
  printf("El ponderado del ES es: %.2f\n", totalES);
  printf("=========================================\n");
  
  // Suma de los cuatro componentes ponderados = nota final de la unidad
  suma = totalACD * 0.2 + totalAPE * 0.25 + totalAA * 0.2 + totalES;

  printf("=========================================\n");
  printf("El resultado de sus notas es:%.2f\n", suma);
  printf("=========================================\n");

  return suma;
}


int main()
{
  float acumulador = 0, suma = 0;
  const int NUMERO = 3; // Número total de unidades del ciclo
  int s;

  // Recorre las 3 unidades del ciclo, calculando y acumulando el promedio de cada una
  for (s = 1; s <= NUMERO; s++)
  {

    suma = calcularPromedio(s);

    acumulador = acumulador + suma;
  }

  // Calcula y muestra el promedio final del ciclo con base en las 3 unidades
  promedioFinal(acumulador , NUMERO );

  return 0;
}

```
[notitaFinal.c](https://github.com/user-attachments/files/29686535/notitaFinal.c)
