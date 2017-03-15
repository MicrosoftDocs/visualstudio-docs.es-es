---
title: "&#39;&lt;membername&gt;&#39; no es un miembro de &#39;&lt;contextname&gt;&#39;; no existe en el contexto actual. | Microsoft Docs"
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
  - "vbc36557"
  - "bc36557"
helpviewer_keywords: 
  - "BC36557"
ms.assetid: d8671f1c-d545-44da-89b3-7d892e01e8be
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;membername&gt;&#39; no es un miembro de &#39;&lt;contextname&gt;&#39;; no existe en el contexto actual.
Se asignó un nombre de miembro inexistente a una propiedad en una declaración de tipo anónimo. En el ejemplo siguiente, los nombres de las propiedades del tipo anónimo son `.Prop1` y `.Prop2`. El intento de asignar `.Prop3` a `.Prop2` provoca el error.  
  
```vb#  
' Not valid.  
Dim anon1 = New With {.Prop1 = 27, .Prop2 = .Prop3}  
  
' The assignment is valid if the assigned property has been declared   
' and initialized.  
Dim anon2 = New With {.Prop1 = 27, .Prop2 = .Prop1}  
```  
  
 **Identificador de error:** BC36657  
  
### Para corregir este error  
  
-   Examine el código para determinar lo que desea asignar. El nombre de la variable podría estar mal escrito o puede requerir calificación si es una propiedad de otro objeto.  
  
## Vea también  
 [Tipos anónimos](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [Cómo: Deducir tipos y nombres de propiedades en declaraciones de tipos anónimos](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)