#include <stdio.h>

float calcularACD()
{
  int trabajo, k;
  float nota, total, acumulador = 0; 

  do
  {
    printf("Cantidad de trabajos ACD:\n");
    scanf("%i", &trabajo);
 
  } while (trabajo < 1);

  for (k = 1; k <= trabajo; k++)
  {
    do
    {
      printf("Nota de tus trabajos de ACD\n");
      scanf("%f", &nota);
    } while (nota > 10 || nota < 0);

    acumulador = acumulador + nota;
  }

  total = acumulador / trabajo;

  return total;
}

float calcularAPE()
{
  int trabajo, k;
  float nota, total, acumulador = 0;
  do
  {
    printf("Cantidad de trabajos APE:\n");
    scanf("%i", &trabajo);
  } while (trabajo < 1);

  for (k = 1; k <= trabajo; k++)
  {
    do
    {
      printf("Nota de tus trabajos de APE\n");
      scanf("%f", &nota);
    } while (nota > 10 || nota < 0);

    acumulador = acumulador + nota;
  }

  total = acumulador / trabajo;
  return total;
}

float calcularAA()
{
  int trabajo, k;
  float nota, total, acumulador = 0;
  do
  {
    printf("Cantidad de trabajos AA:\n");
    scanf("%i", &trabajo);
  } while (trabajo < 1);

  for (k = 1; k <= trabajo; k++)
  {

    do
    {
      printf("Nota de tus trabajos de AA\n");
      scanf("%f", &nota);
    } while (nota > 10 || nota < 0);
    acumulador = acumulador + nota;
  }

  total = acumulador / trabajo;

  return total;
}

 float calcularES()
{
  const float PESO_ES = 0.35;  
  float notaPortafolio, notaExamen;
  float pesoPortafolio, pesoExamen;
  float totalES;

  do{
  printf("¿Qué peso tiene el Portafolio? (ej: 0.6 para 60%%):\n");
  scanf("%f", &pesoPortafolio);
  
  printf("¿Qué peso tiene el Examen? (ej: 0.4 para 40%%):\n");
  scanf("%f", &pesoExamen);

  if (pesoPortafolio + pesoExamen != 1.0) 
    printf("Error: Los pesos deben sumar 100%%\n");
  
  
}while(pesoPortafolio + pesoExamen != 1.0);
 
  do {
    printf("Nota del Portafolio (0-10):\n");
    scanf("%f", &notaPortafolio);
  } while (notaPortafolio > 10 || notaPortafolio < 0);

  do {
    printf("Nota del Examen (0-10):\n");
    scanf("%f", &notaExamen);
  } while (notaExamen > 10 || notaExamen < 0);

  
  totalES = (notaPortafolio * pesoPortafolio) + (notaExamen * pesoExamen);

  return totalES * PESO_ES;
}

void promedioFinal(float x , float y)
{
  float totalCiclo = 0;

  totalCiclo = x / y;
  printf("El resultado de su promedio de Todo su Ciclo es: %.2f\n", totalCiclo);

  if (totalCiclo >= 7)
    printf("Aprobado\n");
  else if (totalCiclo >= 2.5)
    printf("Supletorio\n");
  else
    printf("Reprobado, estudia más\n");
}


float calcularPromedio(int s)
{

  float totalACD, totalAPE, totalAA, totalES, suma;

  printf("Promedio final de la Unidad:%i\n", s);

  totalACD = calcularACD();
  printf("=========================================\n");
  printf("El ponderado del ACD es: %.2f\n", totalACD * 0.2);
  printf("=========================================\n");

  totalAPE = calcularAPE();
  printf("=========================================\n");
  printf("El ponderado del APE es: %.2f\n", totalAPE * 0.25);
  printf("=========================================\n");

  totalAA = calcularAA();
  printf("=========================================\n");
  printf("El ponderado del AA   es: %.2f\n", totalAA * 0.2);
  printf("=========================================\n");

  totalES = calcularES();
  printf("=========================================\n");
  printf("El ponderado del ES es: %.2f\n", totalES);
  printf("=========================================\n");

  suma = totalACD * 0.2 + totalAPE * 0.25 + totalAA * 0.2 + totalES;

  printf("=========================================\n");
  printf("El resultado de sus notas es:%.2f\n", suma);
  printf("=========================================\n");

  return suma;
}


int main()
{
  float acumulador = 0, suma = 0;
  const int NUMERO = 3;
  int s;

  for (s = 1; s <= NUMERO; s++)
  {

    suma = calcularPromedio(s);

    acumulador = acumulador + suma;
  }

  promedioFinal(acumulador , NUMERO );

  return 0;
}
[notitaFinal.c](https://github.com/user-attachments/files/29686535/notitaFinal.c)

