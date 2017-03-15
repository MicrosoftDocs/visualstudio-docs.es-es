---
title: "Todos los anchos de campo, excepto el &#250;ltimo elemento, deben ser mayores que cero. | Microsoft Docs"
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
  - "vbrTextFieldParser_FieldWidthsMustPositive"
ms.assetid: 41d8c661-a749-4c89-be56-905c6e7c3c9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Todos los anchos de campo, excepto el &#250;ltimo elemento, deben ser mayores que cero.
Todos los anchos de campo, excepto el último elemento, deben ser mayores que cero. Un ancho de campo menor o igual que cero en el último elemento indica que el último campo es de longitud variable.  
  
 Error en la operación porque un ancho de campo distinto del último elemento está establecido en cero o menos. Un ancho de campo menor o igual que cero se puede usar como último elemento para indicar que el último campo es de longitud variable, pero no se puede usar como cualquier otro elemento.  
  
### Para corregir este error  
  
-   Establezca el ancho de campo en la longitud correcta.  
  
## Vea también  
 [Método TextFieldParser.SetFieldWidths](http://msdn.microsoft.com/es-es/958fed9f-e0f3-4fc5-83b4-386156bdf036)   
 [Propiedad TextFieldParser.FieldWidths](http://msdn.microsoft.com/es-es/c6985360-60c6-494e-89e7-43b6b73f2597)   
 [Cómo: Leer archivos de texto de ancho fijo](../Topic/How%20to:%20Read%20From%20Fixed-width%20Text%20Files%20in%20Visual%20Basic.md)   
 [TextFieldParser \(Objeto\)](/dotnet/visual-basic/language-reference/objects/textfieldparser-object)