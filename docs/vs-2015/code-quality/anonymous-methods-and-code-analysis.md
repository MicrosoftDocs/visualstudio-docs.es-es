---
title: Métodos anónimos y análisis de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 49da7d5e7f6a7731a708accb3d52fb6383ff1017
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652223"
---
# <a name="anonymous-methods-and-code-analysis"></a>Métodos anónimos y análisis de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un *método anónimo* es un método que no tiene nombre. Los métodos anónimos se utilizan con más frecuencia para pasar un bloque de código como un parámetro de delegado.

 En este tema se explica cómo el análisis de código controla las advertencias y las métricas asociadas a métodos anónimos.

## <a name="anonymous-methods-declared-in-a-member"></a>Métodos anónimos declarados en un miembro
 Las advertencias y las métricas de un método anónimo que se declara en un miembro, como un método o un descriptor de acceso, están asociadas al miembro que declara el método. No están asociados al miembro que llama al método.

 Por ejemplo, en la siguiente clase, cualquier advertencia que se encuentre en la declaración de **anonymousMethod** debe generarse en **method1** y no en **Method2**.

```vb

      Delegate Function ADelegate(ByVal value As Integer) As Boolean
Class AClass

    Sub Method1()
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5
        Method2(anonymousMethod)
    End SubSub Method2(ByVal anonymousMethod As ADelegate)
        anonymousMethod(10)
    End SubEnd Class
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

## <a name="inline-anonymous-methods"></a>Métodos anónimos alineados
 Las advertencias y métricas de un método anónimo que se declara como una asignación insertada en un campo se asocian con el constructor. Si el campo se declara como `static` ( `Shared` en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ), las advertencias y las métricas están asociadas al constructor de clase; de lo contrario, se asocian al constructor de instancia.

 Por ejemplo, en la siguiente clase, cualquier advertencia que se encuentre en la declaración de **anonymousMethod1** se generará en el constructor predeterminado generado implícitamente de la **clase**. Mientras que los que se encuentran en **anonymousMethod2** se aplicarán al constructor de clase generado implícitamente.

```vb

  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass
Dim anonymousMethod1 As ADelegate = Function(ByVal value As    Integer) value > 5
Shared anonymousMethod2 As ADelegate = Function(ByVal value As     Integer) value > 5

Sub Method1()
    anonymousMethod1(10)
    anonymousMethod2(10)
End SubEnd Class
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

 Una clase puede contener un método anónimo insertado que asigna un valor a un campo que tiene varios constructores. En este caso, las advertencias y las métricas están asociadas a todos los constructores a menos que el constructor se encadene a otro constructor de la misma clase.

 Por ejemplo, en la siguiente clase, cualquier advertencia que se encuentre en la declaración de **anonymousMethod** debe generarse en la **clase (int)** y en la **clase (cadena)** pero no en la **clase ()**.

```vb

  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass

Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)
value > 5

SubNew()
    New(CStr(Nothing))
End SubSub New(ByVal a As Integer)
End SubSub New(ByVal a As String)
End SubEnd Class
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

 Aunque esto podría parecer inesperado, esto se debe a que el compilador genera un método único para cada constructor que no se encadena a otro constructor. Debido a este comportamiento, cualquier infracción que se produzca en **anonymousMethod** debe suprimirse por separado. Esto también significa que, si se introduce un nuevo constructor, las advertencias que se suprimieron previamente en la **clase (int)** y la **clase (cadena)** también se deben suprimir en el nuevo constructor.

 Puede solucionar este problema de una de las dos maneras siguientes. Podría declarar **anonymousMethod** en un constructor común que todos los constructores encadenan. O bien, puede declararlo en un método de inicialización al que llamen todos los constructores.

## <a name="see-also"></a>Consulte también
 [Analizar la calidad del código administrado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
