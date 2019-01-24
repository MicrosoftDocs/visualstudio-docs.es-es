---
title: Depurar LINQ | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, LINQ
- LINQ, viewing results in debugger
- LINQ, debugging
- LINQ, stepping
- LINQ, edit and continue
ms.assetid: dbae26cb-ac5f-4312-b474-b9f29714f4c6
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 081c97bffc062bf2bbc9d24feed13e5e512b8c74
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755606"
---
# <a name="debugging-linq"></a>Depurar LINQ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] admite la depuración de código de Language-Integrated Query (LINQ), con algunas limitaciones. La mayor parte de las características de depuración funcionan con instrucciones LINQ, entre ellas la ejecución paso a paso, el establecimiento de puntos de interrupción y la presentación de resultados en las ventanas del depurador. En este tema se describe las principales limitaciones de la depuración LINQ.  
  
##  <a name="BKMK_ViewingLINQResults"></a> Ver los resultados LINQ  
 Puede ver el resultado de una instrucción LINQ mediante Información sobre datos, ventana Inspección y cuadro de diálogo Inspección rápida. Al usar una ventana de código fuente, puede pausar el puntero en una consulta en la ventana de código fuente para que aparezca una información sobre datos. Puede copiar una variable LINQ y pegarla en la ventana Inspección o en el cuadro de diálogo Inspección rápida.  
  
 En LINQ, una consulta no se evalúa cuando se crea o declara, pero únicamente cuando se usa. Por consiguiente, la consulta no tiene un valor hasta que se evalúe. Para obtener una descripción completa de evaluación y creación de consultas, vea [Introducción a las consultas LINQ (C#)](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8) o [escribir su primera consulta con LINQ](http://msdn.microsoft.com/library/4affb732-3e9b-4479-aa31-1f9bd8183cbe).  
  
 Para mostrar el resultado de una consulta, el depurador debe evaluarla. Esta evaluación implícita, que se produce cuando aparece un resultado de la consulta LINQ en el depurador, tiene algunos efectos que debería considerar:  
  
-   Cada evaluación de la consulta lleva tiempo. Expandir el nodo de resultados lleva tiempo. Para algunas consultas, la evaluación repetida podría producir una reducción del rendimiento notable.  
  
-   Evaluar una consulta puede producir efectos secundarios, que son cambios en el valor de los datos o en el estado del programa. No todas las consultas tienen los efectos secundarios. Para determinar si una consulta se puede evaluar sin ningún riesgo ni efectos secundarios, debe entender el código que implementa la consulta.  
  
##  <a name="BKMK_SteppingAndLinq"></a> Ejecución paso a paso y LINQ  
 Si depura código LINQ, la ejecución paso a paso presenta algunas diferencias de comportamiento que debe conocer.  
  
### <a name="linq-to-sql"></a>LINQ to SQL  
 En LINQ a consultas SQL, el código de predicado supera al control del depurador. Por consiguiente, no se puede realizar la ejecución paso a paso en el código de predicado. Cualquier consulta que compila a un árbol de expresiones genera código que supera al control del depurador.  
  
### <a name="stepping-in-visual-basic"></a>Ejecutar paso a paso en Visual Basic  
 Cuando se ejecuta paso a paso a través de un programa de Visual Basic y el depurador encuentra una declaración de consulta, no avanza en la declaración pero resalta la declaración completa como una instrucción única. Este comportamiento se produce porque la consulta no se evalúa hasta que se llama. Para obtener más información, consulte [Introducción a LINQ en Visual Basic](http://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984).  
  
 Si recorre el código de ejemplo siguiente, el depurador resalta la declaración de consulta, o creación de consulta, como una instrucción única.  
  
```  
Function MyFunction(ByVal x As Char)  
    Return True  
End Function  
  
Sub Main()  
    'Query creation  
    Dim x = From it In "faoaoeua" _  
            Where MyFunction(it) _  
            Select New With {.a = it}  
  
    ' Query execution  
    For Each cur In x  
        Console.WriteLine(cur.ToString())  
    Next  
End Sub  
```  
  
 Al avanzar de nuevo, el depurador resalta `For Each cur In x`. En el paso siguiente, avanza hasta la función `MyFunction`. Después de recorrer paso a paso `MyFunction`, ésta retrocede a `Console.WriteLine(cur.ToSting())`. En ningún punto se recorre paso a paso el código de predicado en la declaración de consulta, aunque el depurador evalúa ese código.  
  
### <a name="replacing-a-predicate-with-a-function-to-enable-stepping-visual-basic"></a>Reemplazar un predicado con una función para habilitar la ejecución paso a paso (Visual Basic)  
 Si tiene recorrer paso a paso el código de predicado con fines de depuración, puede reemplazar el predicado con una llamada a una función que contenga el código de predicado original. Por ejemplo, supongamos este código:  
  
```  
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
```  
  
 Puede mover el código de predicado a una nueva función, denominada `IsEven`:  
  
```  
Dim items () as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where IsEven(nextInt) Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
...   
Function IsEven(item As =Integer) as Boolean  
      Return item Mod 2 = 0  
End Function  
```  
  
 La consulta revisada llama a la función `IsEven` en cada paso a través de `items`. Puede usar las ventanas del depurador para ver si cada elemento cumple la condición especificada, y puede recorrer paso a paso el código en `IsEven`. El predicado en este ejemplo es bastante simple. Sin embargo, si tiene un predicado más complejo debe realizar la depuración, esta técnica puede ser muy útil.  
  
##  <a name="BKMK_EditandContinueNotSupportedforLINQ"></a> Editar y continuar no se admite en LINQ  
 Editar y continuar no admite los cambios a las consultas LINQ. Si agrega, quita o cambia una instrucción LINQ durante una sesión de depuración, aparece un cuadro de diálogo indicando que Editar y continuar no admite el cambio. En ese momento, puede deshacer los cambios o detener la sesión de depuración y reiniciar una nueva sesión con el código revisado.  
  
 Además, Editar y continuar no permite cambiar el tipo o el valor de una variable que se usa en una instrucción LINQ. De nuevo, puede deshacer los cambios o detener y reiniciar la sesión de depuración.  
  
 En C#, no puede usar Editar y continuar en cualquier código en un método que contiene una consulta LINQ.  
  
 En Visual Basic, puede usar Editar y continuar en código sin LINQ, incluso en un método que contiene una consulta LINQ. Puede agregar o quitar el código antes de la instrucción LINQ, incluso si los cambios afectan al número de línea de la consulta LINQ. La experiencia en depuración de Visual Basic para código sin LINQ es igual que antes de incluir LINQ. No se puede cambiar, agregar o quitar una consulta LINQ, a menos que desee detener la depuración para aplicar los cambios.  
  
## <a name="see-also"></a>Vea también  
 [Depuración de SQL](http://msdn.microsoft.com/en-us/f27c17e6-1d90-49f2-9fc0-d02e6a27f109)   
 [Side Effects and Expressions](http://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e)   
 [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md)   
 [Introduction to LINQ Queries (C#)](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)  (Introducción a las consultas LINQ [C#])  
 [Introducción a LINQ en Visual Basic](http://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984)



