---
title: "No se puede aplicar el valor &#39;System.Runtime.InteropServices.DispIdAttribute&#39; a &#39;&lt;typename&gt;&#39; porque &#39;Microsoft.VisualBasic.ComClassAttribute&#39; reserva cero para la propiedad predeterminada. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32505"
  - "bc32505"
helpviewer_keywords: 
  - "BC32505"
ms.assetid: a7d5b948-2d72-48b1-8baf-bfaae36b0128
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede aplicar el valor &#39;System.Runtime.InteropServices.DispIdAttribute&#39; a &#39;&lt;typename&gt;&#39; porque &#39;Microsoft.VisualBasic.ComClassAttribute&#39; reserva cero para la propiedad predeterminada.
Un bloque de atributos <xref:System.Runtime.InteropServices.DispIdAttribute> especifica un valor de DISPID menor que 0, que `COMClassAttribute` ha reservado para representar la propiedad predeterminada de la clase a la que se aplica.  
  
 El identificador de envío \(DISPID\) se usa en COM como argumento para que el método `IDispatch:Invoke` tenga acceso a las propiedades y los métodos que expone un objeto COM.  
  
 **Identificador de error:** BC32505  
  
### Para corregir este error  
  
-   Especifique un valor de DISPID mayor que cero en <xref:System.Runtime.InteropServices.DispIdAttribute>.  
  
## Vea también  
 <xref:System.Runtime.InteropServices.DispIdAttribute>   
 [NO ESTÁ EN LA COMPILACIÓN: Atributos usados en Visual Basic](http://msdn.microsoft.com/es-es/22231318-8a40-49af-9245-e0aab723563b)   
 [NO ESTÁ EN LA COMPILACIÓN: Aplicación de atributos](http://msdn.microsoft.com/es-es/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Clase ComClassAttribute](http://msdn.microsoft.com/es-es/5c2f0835-9210-47dc-bc59-5c1769953574)