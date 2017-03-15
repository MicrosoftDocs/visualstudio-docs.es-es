---
title: "El m&#233;todo de extensi&#243;n &#39;&lt;nombreM&#233;todo&gt;&#39; definido en &#39;&lt;nombreM&#243;dulo&gt;&#39; no es gen&#233;rico (o no tiene ning&#250;n par&#225;metro de tipo libre) y, por lo tanto, no puede tener argumentos de tipo. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36907"
  - "vbc36907"
helpviewer_keywords: 
  - "BC36907"
ms.assetid: 45191e93-89d1-48ec-99a5-ff9661a2a6ee
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El m&#233;todo de extensi&#243;n &#39;&lt;nombreM&#233;todo&gt;&#39; definido en &#39;&lt;nombreM&#243;dulo&gt;&#39; no es gen&#233;rico (o no tiene ning&#250;n par&#225;metro de tipo libre) y, por lo tanto, no puede tener argumentos de tipo.
Se ha especificado un argumento de tipo en una llamada a un método de extensión que no tiene parámetros genéricos o no tiene parámetros genéricos para los que aún no se ha especificado un tipo. Por ejemplo, el código siguiente causa este error.  
  
```vb#  
' The extension method is not generic. <Extension()> _ Sub Example(ByVal str As String) ' Body of the Sub. End Sub  
```  
  
```vb#  
Dim str = "hi" '' The call to Example specifies a type argument. '' Not valid. 'str.Example(Of String)()  
```  
  
 **Identificador de error:** BC36907  
  
### Para corregir este error  
  
-   Agregue un parámetro de tipo a la definición del método de extensión.  
  
-   Quite el argumento de tipo adicional de la llamada a procedimiento.  
  
## Vea también  
 [métodos de extensión.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)