---
title: "Expresi&#243;n de llamada o de &#237;ndice no v&#225;lida | Microsoft Docs"
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
  - "vbc32303"
  - "bc32303"
helpviewer_keywords: 
  - "BC32303"
ms.assetid: eed6a16e-4a44-4f72-b1de-d4212940da37
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Expresi&#243;n de llamada o de &#237;ndice no v&#225;lida
Un valor entre paréntesis sigue a una expresión que no es un procedimiento, una propiedad ni una matriz.  
  
 El código siguiente pueden generar este error.  
  
 `Dim testVariable As Object = Nothing(1)`  
  
 Dado que `Nothing` no toma argumentos ni índices, no se puede usar con paréntesis.  
  
 **Identificador de error:** BC32303  
  
### Para corregir este error  
  
-   Quite los paréntesis y cualquier valor que contengan.  
  
## Vea también  
 [Cómo: Llamar a un procedimiento que devuelve un valor](../Topic/How%20to:%20Call%20a%20Procedure%20That%20Returns%20a%20Value%20\(Visual%20Basic\).md)   
 [Cómo: Llamar a un procedimiento que no devuelve un valor](../Topic/How%20to:%20Call%20a%20Procedure%20that%20Does%20Not%20Return%20a%20Value%20\(Visual%20Basic\).md)   
 [NO ESTÁ EN LA COMPILACIÓN Cómo: Establecer un valor en una matriz](http://msdn.microsoft.com/es-es/6dddc79c-cf60-41c2-b572-8bfa49b4fe7e)   
 [NO ESTÁ EN LA COMPILACIÓN Cómo: Obtener un valor a partir de una matriz](http://msdn.microsoft.com/es-es/202a6468-8ccb-4864-bd8b-eab3b42d4288)   
 [Cómo: Establecer un valor en una propiedad](../Topic/How%20to:%20Put%20a%20Value%20in%20a%20Property%20\(Visual%20Basic\).md)   
 [Cómo: Obtener un valor de una propiedad](../Topic/How%20to:%20Get%20a%20Value%20from%20a%20Property%20\(Visual%20Basic\).md)