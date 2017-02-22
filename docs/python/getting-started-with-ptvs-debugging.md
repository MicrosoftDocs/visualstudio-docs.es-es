---
title: "Introducci&#243;n a PTVS: Depurar | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-python"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 82803559-1d60-4c57-98fb-2dc1e0182b42
caps.latest.revision: 4
caps.handback.revision: 4
author: "kraigb"
ms.author: "kraigb"
manager: "ghogen"
---
# Introducci&#243;n a PTVS: Depurar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El depurador interactivo de Visual Studio facilita el proceso de diagnosticar y resolver problemas en el código Python.  
  
 Puede ver estas instrucciones en un breve [vídeo de Youtube](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4).  
  
 En el tema de introducción anterior, creó un proyecto vacío de aplicación de Python y escribió el código siguiente en PythonApplication1.py:  
  
```python  
from math import sin, cos, radians  
import sys  
  
def make_dot_string(x):  
    return ' ' * int(10 * cos(radians(x)) + 10) + 'o'  
  
assert make_dot_string(90) == "          o"  
assert make_dot_string(180) == "o"  
  
def main():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
  
if __name__ == "__main__":  
    sys.exit(int(main() or 0))  
```  
  
 Normalmente, cuando se trabaja con código en Visual Studio, comenzará a ejecutar el código presionando F5.  Este comando compila todas las partes del proyecto que deben compilarse y comienza a ejecutar el código en el depurador.  También puede presionar Ctrl\+F5 para compilar y ejecutar el código sin el depurador.  Con el depurador, el código se ejecuta un poco más lentamente, pero obtiene unas características de depuración excelentes por ese costo.  
  
 Otra manera de ejecutar el código es con el comando Entrar \(normalmente vinculado a F11\).  Es como F5, pero detiene la ejecución en cada instrucción.  Si desea interrumpir el programa en un momento determinado, puede presionar el botón izquierdo del puntero en el margen izquierdo del editor de código para establecer un punto de interrupción.  Cuando se presiona F5, la ejecución del programa se interrumpe o se detiene en la línea con el punto de interrupción.  El menú Depurar tiene más opciones para la ejecución paso a paso; por ejemplo, avanzar por las llamadas de función \(F10\), ir a las llamadas de función \(F11\) o saltar al final de una función \(MAYÚS\+F11\).  
  
 Puede hacer más cosas con las interrupciones del depurador.  La ventana Variables locales muestra los valores actuales de las variables locales.  Al ejecutar paso a paso el código, las variables locales muestran las actualizaciones automáticamente.  La ventana Automático muestra las variables cerca de la línea actual donde se detuvo la ejecución.  En la ventana Inspección, puede escribir cualquier expresión de Python que el depurador actualizará automáticamente cada vez que se detenga la ejecución.  También puede desplazar el puntero sobre las variables en las ventanas del editor para ver una pantalla emergente con los valores de la variable, y esta pantalla de sugerencia de datos le permite inspeccionar los objetos.  Algunos tipos de datos tienen visualizadores especiales a los que se puede acceder desde la pantalla de sugerencia de datos \(por ejemplo, cadenas con formato especial, como HTML, XML o JSON\).  
  
 La ventana Pila de llamadas muestra las llamadas a funciones pendientes que condujeron a la instrucción actual donde se detuvo el depurador.  Puede elegir diferentes marcos de pila \(líneas en la pila de llamadas\) para saltar adonde seguirá ejecutándose el código en cada función, buscar valores de variables, etcétera.  
  
 Puede ver estas instrucciones en un breve [vídeo de Youtube](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4).  
  
## Vea también  
 [Documentación wiki](https://github.com/Microsoft/PTVS/wiki/Debugging)   
 [Introducción a PTVS y vídeos de documentación exhaustiva](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)