---
title: Advertencias de análisis de código de método anónimo
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a10c5baaed3a98e44d581b6ddb8d6e3a1883d079
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62560240"
---
# <a name="anonymous-methods-and-code-analysis"></a>Métodos anónimos y análisis de código

Un *método anónimo* es un método que no tiene nombre. Métodos anónimos se utilizan con más frecuencia para pasar un bloque de código como parámetro delegado. Este artículo explica cómo el análisis de código controla las advertencias y las métricas para los métodos anónimos.

## <a name="anonymous-methods-declared-in-a-member"></a>Métodos anónimos declarados en un miembro

Las advertencias y las métricas para un método anónimo que se declara en un miembro, como un método o el descriptor de acceso, se asocian con el miembro que declara el método. No se asocian con el miembro que llama al método.

Por ejemplo, en la clase siguiente, cualquier advertencia que se encuentran en la declaración de **anonymousMethod** debe emitirse contra **Method1** y no **método2**.

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean

Class AClass
    Sub Method1()
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5
        Method2(anonymousMethod)
    End Sub
    Sub Method2(ByVal anonymousMethod As ADelegate)
        anonymousMethod(10)
    End Sub
End Class
```

```csharp
delegate void Delegate();

class Class
{
    void Method1()
    {
        Delegate anonymousMethod = delegate()
        {
          Console.WriteLine("");
        }
        Method2(anonymousMethod);
    }

    void Method2(Delegate anonymousMethod)
    {
        anonymousMethod();
    }
}
```

## <a name="inline-anonymous-methods"></a>Métodos anónimos insertados

Las advertencias y las métricas para un método anónimo que se declara como una asignación insertada en un campo están asociadas con el constructor. Si el campo se declara como `static` (`Shared` en Visual Basic), las advertencias y las métricas asociadas con el constructor de clase. En caso contrario, que están asociados con el constructor de instancia.

Por ejemplo, en la clase siguiente, cualquier advertencia que se encuentran en la declaración de **anonymousMethod1** se generarán para el constructor predeterminado generado implícitamente de **clase**. Las advertencias que se encuentran en **anonymousMethod2** se aplicará en el constructor de clase generado implícitamente.

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean
Class AClass
    Dim anonymousMethod1 As ADelegate = Function(ByVal value As Integer) value > 5
    Shared anonymousMethod2 As ADelegate = Function(ByVal value As Integer) value > 5

    Sub Method1()
        anonymousMethod1(10)
        anonymousMethod2(10)
    End Sub
End Class
```

```csharp
delegate void Delegate();

class Class
{
    Delegate anonymousMethod1 = delegate()
    {
       Console.WriteLine("");
    }

    static Delegate anonymousMethod2 = delegate()
    {
       Console.WriteLine("");
    }

    void Method()
    {
       anonymousMethod1();
       anonymousMethod2();
    }
}
```

Una clase podría contener un método anónimo insertado que asigna un valor a un campo que tiene varios constructores. En este caso, las advertencias y métricas están asociados con todos los constructores a menos que el constructor se encadena a otro constructor en la misma clase.

Por ejemplo, en la siguiente clase, las advertencias que se encuentran en la declaración de **anonymousMethod** debe emitirse contra **Class (int)** y **Class (String)**, pero no contra **Class()**.

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean

Class AClass

    Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5

    SubNew()
        New(CStr(Nothing))
    End Sub

    Sub New(ByVal a As Integer)
    End Sub

    Sub New(ByVal a As String)
    End Sub
End Class
```

```csharp
delegate void Delegate();

class Class
{
    Delegate anonymousMethod = delegate()
    {
       Console.WriteLine("");
    }

    Class() : this((string)null)
    {
    }

    Class(int a)
    {
    }

    Class(string a)
    {
    }
}
```

Las advertencias se producen en los constructores ya que el compilador genera un método único para cada constructor que no está vinculado a otro constructor. Debido a este comportamiento, cualquier infracción que se produce en **anonymousMethod** debe suprimirse por separado. Esto también significa que si es un nuevo constructor introducido, las advertencias previamente suprimidas contra **Class (int)** y **Class (String)** para el nuevo constructor también debe suprimirse.

Puede solucionar este problema en uno de dos maneras:

- Declarar **anonymousMethod** en un constructor común que encadenen todos los constructores.
- Declarar **anonymousMethod** en un método de inicialización que se llama a todos los constructores.

## <a name="see-also"></a>Vea también

- [Analizar la calidad del código administrado](../code-quality/code-analysis-for-managed-code-overview.md)