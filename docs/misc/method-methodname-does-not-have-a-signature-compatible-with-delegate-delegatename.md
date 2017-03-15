---
title: "El m&#233;todo &#39;&lt;nombreM&#233;todo&#39; no tiene una firma compatible con el delegado &lt;&#39;nombreDelegado&#39;&gt;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31143"
  - "bc31143"
helpviewer_keywords: 
  - "BC31143"
ms.assetid: 88990637-7c92-467e-a3d3-db5498dc1dce
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El m&#233;todo &#39;&lt;nombreM&#233;todo&#39; no tiene una firma compatible con el delegado &lt;&#39;nombreDelegado&#39;&gt;.
Este error se produce cuando se requiere una conversión entre un método y un delegado que no es posible. La causa del error puede ser una conversión entre parámetros o, cuando el método y el delegado son funciones, la conversión de los valores devueltos.  
  
 El código siguiente muestra el error en conversiones. El delegado es `FunDel`.  
  
```vb#  
Delegate Function FunDel(ByVal i As Integer, ByVal d As Double) As Integer  
```  
  
 Las funciones siguientes difieren de `FunDel` de manera que se producirá este error.  
  
```vb#  
Function ExampleMethod1(ByVal m As Integer, ByVal aDate As Date) As Integer End Function Function ExampleMethod2(ByVal m As Integer, ByVal aDouble As Double) As Date End Function  
```  
  
 Cada una de las siguientes instrucciones de asignación produce el error.  
  
```vb#  
Sub Main() ' The second parameters of FunDel and ExampleMethod1, Double and Date, ' are not compatible. 'Dim d1 As FunDel = AddressOf ExampleMethod1 ' The return types of FunDel and ExampleMethod2, Integer and Date, ' are not compatible. 'Dim d2 As FunDel = AddressOf ExampleMethod2 End Sub  
```  
  
 **Identificador de error:** BC31143  
  
### Para corregir este error  
  
-   Examine los parámetros correspondientes y, si están presentes, los tipos de valor devueltos para determinar qué par no es compatible.  
  
## Vea también  
 [Conversión de delegado flexible](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [NO ESTÁ EN LA COMPILACIÓN: Delegados y el operador AddressOf](http://msdn.microsoft.com/es-es/7b2ed932-8598-4355-b2f7-5cedb23ee86f)