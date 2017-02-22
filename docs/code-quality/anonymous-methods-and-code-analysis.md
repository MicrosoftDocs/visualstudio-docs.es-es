---
title: "M&#233;todos an&#243;nimos y an&#225;lisis de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "métodos anónimos, análisis de código"
  - "análisis de código, métodos anónimos"
  - "métodos, anónimos"
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# M&#233;todos an&#243;nimos y an&#225;lisis de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un *método anónimo* es un método que no tiene nombre.  Los métodos anónimos se utilizan con más frecuencia para pasar un bloque de código como parámetro delegado.  
  
 En este tema se explica el modo en que el análisis de código controla las advertencias y las métricas que están asociadas a los métodos anónimos.  
  
## Métodos anónimos declarados dentro de un miembro  
 Las advertencias y las métricas para un método anónimo declarado en un miembro, ya sea como método o como descriptor de acceso, se asocian al miembro que declara el método.  No se asocian con el miembro que llama al método.  
  
 Por ejemplo, en la clase siguiente, las advertencias que se encuentren en la declaración de **anonymousMethod**, se deberían generar para el **Method1** y no para el **Method2**.  
  
```vb#  
  
        Delegate Function ADelegate(ByVal value As Integer) As Boolean  
Class AClass  
  
    Sub Method1()  
        Dim anonymousMethod As ADelegate = Function(ByVal value As  Integer) value > 5  
        Method2(anonymousMethod)  
    End Sub Sub Method2(ByVal anonymousMethod As ADelegate)  
        anonymousMethod(10)  
    End Sub End Class  
```  
  
```c#  
  
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
  
## Métodos anónimos insertados  
 Las advertencias y métricas de un método anónimo declaradas como una asignación insertada en un campo están asociadas al constructor.  Si el campo se declara como `static` \(`Shared` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\), las advertencias y métricas estarán asociadas al constructor de clase; de lo contrario, estarían asociados al constructor de instancia.  
  
 Por ejemplo, en la clase siguiente, cualquier advertencia hallada en la declaración de **anonymousMethod1**, se generará para el constructor predeterminado de **Class** generado implícitamente.  Mientras que aquellas halladas en **anonymousMethod2** se aplicarán al constructor de clase generado implícitamente.  
  
```vb#  
  
    Delegate Function ADelegate(ByVal value As Integer) As Boolean Class AClass  
Dim anonymousMethod1 As ADelegate = Function(ByVal value As     Integer) value > 5  
Shared anonymousMethod2 As ADelegate = Function(ByVal value As      Integer) value > 5  
  
Sub Method1()  
    anonymousMethod1(10)  
    anonymousMethod2(10)  
End Sub End Class  
```  
  
```c#  
  
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
  
 Una clase podría contener un método anónimo insertado que asigna un valor a un campo que tiene varios constructores.  En este caso, las advertencias y métricas están asociadas a todos los constructores a menos que un constructor se encadene a otro en la misma clase.  
  
 Por ejemplo, en la clase siguiente, cualquier advertencia que se encuentre en la declaración de **anonymousMethod**, se debería generar para **Class\(int\)** y **Class\(string\)**, pero no para **Class\(\)**.  
  
```vb#  
  
    Delegate Function ADelegate(ByVal value As Integer) As Boolean Class AClass  
  
Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)   
value > 5  
  
Sub New()  
    New(CStr(Nothing))  
End Sub Sub New(ByVal a As Integer)  
End Sub Sub New(ByVal a As String)  
End Sub End Class  
```  
  
```c#  
  
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
  
 A pesar de que esto puede resultar inesperado, se produce debido a que el compilador da como resultado un método único para cada constructor que no se encadena a otro constructor.  Debido a este comportamiento, cualquier infracción que se produzca en **anonymousMethod** se debe suprimir de forma independiente.  Esto también significa que si se introduce un nuevo constructor, las advertencias previamente suprimidas para **Class\(int\)** y **Class\(string\)** también se deben suprimir para el nuevo constructor.  
  
 Existen dos formas de solucionar este problema.  Podría declarar **anonymousMethod** en un constructor común con el que se encadenen todos los constructores.  O podría declararlo en un método de inicialización al que llaman todos los constructores.  
  
## Vea también  
 [Analizar la calidad del código administrado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)