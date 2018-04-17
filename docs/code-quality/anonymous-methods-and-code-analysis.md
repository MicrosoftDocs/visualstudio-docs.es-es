---
title: Métodos anónimos y análisis de código | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ced736f74be4216a069b27aed096989a89cf518d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="anonymous-methods-and-code-analysis"></a>Métodos anónimos y análisis de código
Un *método anónimo* es un método que no tiene ningún nombre. Métodos anónimos se utilizan con más frecuencia para pasar un bloque de código como un parámetro de delegado.  
  
 Este tema explica cómo el análisis de código controla las advertencias y las métricas que están asociadas con métodos anónimos.  
  
## <a name="anonymous-methods-declared-in-a-member"></a>Métodos anónimos declarados en un miembro  
 Las advertencias y las métricas para un método anónimo que se declara en un miembro, como un método o descriptor de acceso, se asocian al miembro que declara el método. No están asociados con el miembro que llama al método.  
  
 Por ejemplo, en la siguiente clase, las advertencias que se encuentran en la declaración de **anonymousMethod** debe generarse en **Method1** y no **Method2**.  
  
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
  
## <a name="inline-anonymous-methods"></a>Métodos anónimos insertados  
 Las advertencias y las métricas para un método anónimo que se declara como una asignación insertada en un campo están asociadas con el constructor. Si el campo se declara como `static` (`Shared` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), las advertencias y métricas están asociados con el constructor de clase; en caso contrario, están asociados con el constructor de instancia.  
  
 Por ejemplo, en la siguiente clase, las advertencias que se encuentran en la declaración de **anonymousMethod1** se provocarán en el constructor predeterminado generado implícitamente de **clase**. Mientras que las que se encuentran en **anonymousMethod2** se aplicarán en el constructor de clase generado implícitamente.  
  
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
  
 Una clase puede contener un método anónimo insertado que asigna un valor a un campo que tiene varios constructores. En este caso, las advertencias y las métricas están asociadas con todos los constructores a menos que este constructor se encadena a otro constructor de la misma clase.  
  
 Por ejemplo, en la siguiente clase, las advertencias que se encuentran en la declaración de **anonymousMethod** debe generarse en **Class (int)** y **Class (String)** pero no en **Class()**.  
  
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
  
 Aunque puede parecer inesperado, esto ocurre porque el compilador genera un método único para cada constructor que no se encadena a otro constructor. Debido a este comportamiento, cualquier infracción que se produce en **anonymousMethod** debe suprimirse por separado. Esto también significa que si es un nuevo constructor introdujo, las advertencias que se hayan suprimido anteriormente con **Class (int)** y **Class (String)** también se debe suprimir en el nuevo constructor.  
  
 Puede solucionar este problema en uno de dos maneras. Podría declarar **anonymousMethod** en un constructor común que encadenen todos los constructores. O bien puede declarar en un método de inicialización que se llama a todos los constructores.  
  
## <a name="see-also"></a>Vea también  
 [Analizar la calidad del código administrado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)