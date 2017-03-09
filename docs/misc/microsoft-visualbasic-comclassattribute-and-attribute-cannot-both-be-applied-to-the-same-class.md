---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; y &#39;&lt;attribute&gt;&#39; no se pueden aplicar a la vez a la misma clase. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32501"
  - "bc32501"
helpviewer_keywords: 
  - "BC32501"
ms.assetid: dc1bf4f1-f030-4df3-aae8-524af9c2fda7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; y &#39;&lt;attribute&gt;&#39; no se pueden aplicar a la vez a la misma clase.
Un bloque de atributos `COMClassAttribute` se usa junto con un atributo que no se aplica a objetos COM. Una posible causa es una combinación de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] y atributos COM.  
  
 **Identificador de error:** BC32501  
  
### Para corregir este error  
  
-   Quite el bloque de atributos `COMClassAttribute` o el atributo que no sea aplicable a COM.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Atributos usados en Visual Basic](http://msdn.microsoft.com/es-es/22231318-8a40-49af-9245-e0aab723563b)   
 [NO ESTÁ EN LA COMPILACIÓN: Aplicación de atributos](http://msdn.microsoft.com/es-es/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Clase ComClassAttribute](http://msdn.microsoft.com/es-es/5c2f0835-9210-47dc-bc59-5c1769953574)