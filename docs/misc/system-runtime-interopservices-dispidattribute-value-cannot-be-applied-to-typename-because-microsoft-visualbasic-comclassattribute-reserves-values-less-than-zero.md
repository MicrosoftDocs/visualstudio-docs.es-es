---
title: "No se puede aplicar el valor de &#39;System.Runtime.InteropServices.DispIdAttribute&#39; a &#39;&lt;typename&gt;&#39; porque &#39;Microsoft.VisualBasic.ComClassAttribute&#39; reserva valores inferiores a cero | Microsoft Docs"
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
  - "bc32506"
  - "vbc32506"
helpviewer_keywords: 
  - "BC32506"
ms.assetid: c6f52e1d-45d8-45cb-9ecb-a2f23b3ca779
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede aplicar el valor de &#39;System.Runtime.InteropServices.DispIdAttribute&#39; a &#39;&lt;typename&gt;&#39; porque &#39;Microsoft.VisualBasic.ComClassAttribute&#39; reserva valores inferiores a cero
Un bloque de atributos <xref:System.Runtime.InteropServices.DispIdAttribute> especifica un valor de DISPID menor que 0, que `COMClassAttribute` ha reservado para funciones especiales de la clase a la que se aplica.  
  
 El identificador de envío \(DISPID\) se utiliza en COM como argumento para que el método `IDispatch:Invoke` acceda a las propiedades y los métodos que expone un objeto COM.  
  
 **Id. de error:** BC32506  
  
### Para corregir este error  
  
-   Especifique un valor de DISPID mayor que cero en `DispIdAttribute`.  
  
## Vea también  
 <xref:System.Runtime.InteropServices.DispIdAttribute>   
 [NO ESTÁ EN LA COMPILACIÓN: Atributos usados en Visual Basic](http://msdn.microsoft.com/es-es/22231318-8a40-49af-9245-e0aab723563b)   
 [NO ESTÁ EN LA COMPILACIÓN: Aplicación de atributos](http://msdn.microsoft.com/es-es/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Clase ComClassAttribute](http://msdn.microsoft.com/es-es/5c2f0835-9210-47dc-bc59-5c1769953574)