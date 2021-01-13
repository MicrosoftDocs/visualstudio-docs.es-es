---
title: Depuración de LINQ | Microsoft Docs
description: Depure código de Language Integrated Query (LINQ) en Visual Studio. Visualice los resultados de LINQ. Comprenda las diferencias de comportamiento al depurar paso a paso por instrucciones de código de LINQ.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, LINQ
- LINQ, viewing results in debugger
- LINQ, debugging
- LINQ, stepping
- LINQ, edit and continue
ms.assetid: dbae26cb-ac5f-4312-b474-b9f29714f4c6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 903ffb5d3187da3bda961caca42cf7436a816b6d
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728374"
---
# <a name="debugging-linq"></a>Depurar LINQ
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] admite la depuración de código de Language-Integrated Query (LINQ), con algunas limitaciones. La mayor parte de las características de depuración funcionan con instrucciones LINQ, entre ellas la ejecución paso a paso, el establecimiento de puntos de interrupción y la presentación de resultados en las ventanas del depurador. En este tema se describen las principales limitaciones de la depuración LINQ.

## <a name="viewing-linq-results"></a><a name="BKMK_ViewingLINQResults"></a> Visualización de los resultados LINQ
 Puede ver el resultado de una instrucción LINQ mediante Información sobre datos, ventana Inspección y cuadro de diálogo Inspección rápida. Al usar una ventana de código fuente, puede pausar el puntero en una consulta en la ventana de código fuente para que aparezca una información sobre datos. Puede copiar una variable LINQ y pegarla en la ventana Inspección o en el cuadro de diálogo Inspección rápida.

 En LINQ, una consulta no se evalúa cuando se crea o declara, pero únicamente cuando se usa. Por consiguiente, la consulta no tiene un valor hasta que se evalúe. Para obtener una descripción completa de la creación y evaluación de consultas, vea [Introducción a las consultas LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries) o [Escritura de la primera consulta con LINQ](/dotnet/visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query).

 Para mostrar el resultado de una consulta, el depurador debe evaluarla. Esta evaluación implícita, que se produce cuando aparece un resultado de la consulta LINQ en el depurador, tiene algunos efectos que debería considerar:

- Cada evaluación de la consulta lleva tiempo. Expandir el nodo de resultados lleva tiempo. Para algunas consultas, la evaluación repetida podría producir una reducción del rendimiento notable.

- Evaluar una consulta puede producir efectos secundarios, que son cambios en el valor de los datos o en el estado del programa. No todas las consultas tienen los efectos secundarios. Para determinar si una consulta se puede evaluar sin ningún riesgo ni efectos secundarios, debe entender el código que implementa la consulta.

## <a name="stepping-and-linq"></a><a name="BKMK_SteppingAndLinq"></a> Depuración paso a paso por instrucciones y LINQ
 Si depura código LINQ, la ejecución paso a paso presenta algunas diferencias de comportamiento que debe conocer.

### <a name="linq-to-sql"></a>LINQ to SQL
 En LINQ a consultas SQL, el código de predicado supera al control del depurador. Por consiguiente, no se puede realizar la ejecución paso a paso en el código de predicado. Cualquier consulta que compila a un árbol de expresiones genera código que supera al control del depurador.

### <a name="stepping-in-visual-basic"></a>Ejecutar paso a paso en Visual Basic
 Cuando se ejecuta paso a paso a través de un programa de Visual Basic y el depurador encuentra una declaración de consulta, no avanza en la declaración pero resalta la declaración completa como una instrucción única. Este comportamiento se produce porque la consulta no se evalúa hasta que se llama. Para más información, vea [Introducción a LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq).

 Si recorre el código de ejemplo siguiente, el depurador resalta la declaración de consulta, o creación de consulta, como una instrucción única.

```vb
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

```vb
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

' Get the even numbers
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt

For each item in query
      Console.WriteLine(item)
Next
```

 Puede mover el código de predicado a una nueva función, denominada `IsEven`:

```vb
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

## <a name="edit-and-continue-not-supported-for-linq"></a><a name="BKMK_EditandContinueNotSupportedforLINQ"></a> Función Editar y Continuar no admitida en LINQ
 Editar y continuar admite cambios en las consultas LINQ con limitaciones. Para más información, vea [Cambios admitidos en EnC](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md).

## <a name="see-also"></a>Vea también

- [Depuración de SQL](/previous-versions/visualstudio/visual-studio-2010/zefbf0t6\(v\=vs.100\))
- [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md)
- [Introducción a las consultas LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
- [Introducción a LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
