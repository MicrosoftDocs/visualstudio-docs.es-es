---
title: "&#39;ParamArray&#39; no se puede aplicar al primer par&#225;metro de un m&#233;todo de extensi&#243;n | Microsoft Docs"
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
  - "vbc36554"
  - "bc36554"
helpviewer_keywords: 
  - "BC36554"
ms.assetid: 0778a854-246f-4c2b-943d-ea8883b3aa6f
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ParamArray&#39; no se puede aplicar al primer par&#225;metro de un m&#233;todo de extensi&#243;n
'ParamArray' no se puede aplicar al primer parámetro de un método de extensión. El primer parámetro especifica el tipo que se debe extender.  
  
 El primer parámetro de un método de extensión especifica el tipo de datos que extiende el método. Por lo tanto, el primer parámetro es necesario y no puede ser opcional. Dado que una matriz de parámetros es opcional de manera predeterminada, no es válida como primer argumento de un método de extensión.  
  
> [!NOTE]
>  Cuando se ejecuta el método, la instancia del tipo de datos extendidos que invoca el método se convierte en el argumento del primer parámetro del método. Por ejemplo, la instancia de `greeting` en `greeting.Print()` es el argumento para el primer parámetro, `str`, en el método de extensión `Public Sub Print (ByVal str As String)`.  
  
 **Identificador de error:** BC36554  
  
### Para corregir este error  
  
-   Si la matriz de parámetros no especifica el tipo de datos que desea extender, agregue un nuevo primer parámetro que especifique este tipo.  
  
    ```  
    <Extension()> Public Sub AddTo(ByRef str As String, ByVal ParamArray addOns() As String) ' Concatenate the strings in addOns to str. End Sub  
    ```  
  
-   Si la matriz de parámetros especifica el tipo de datos que desea extender, considere la posibilidad de cambiar a una matriz normal, que requiere un argumento en lugar de una matriz de parámetros. Las matrices normales se pueden extender.  
  
    ```  
    <Extension()> Public Function Sum(ByVal ints() As Integer) As Integer Dim total As Integer = 0 For Each i As Integer In ints total = total + i Next i Return total End Function  
    ```  
  
## Vea también  
 [métodos de extensión.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Matrices de parámetros](/dotnet/visual-basic/programming-guide/language-features/procedures/parameter-arrays)   
 [Parámetros opcionales](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)