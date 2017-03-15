---
title: "No se puede asignar un nombre a &#39;&lt;nombre&gt;&#39; como un par&#225;metro en un especificador de atributo porque no es un campo ni una propiedad | Microsoft Docs"
ms.custom: ""
ms.date: "10/25/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32010"
  - "bc32010"
helpviewer_keywords: 
  - "BC32010"
ms.assetid: bfa68729-71ea-410e-bef1-83a7dab44d2a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede asignar un nombre a &#39;&lt;nombre&gt;&#39; como un par&#225;metro en un especificador de atributo porque no es un campo ni una propiedad
Un bloque de atributos establece un valor para un miembro no variable del atributo. Puede asignar valores solo a miembros de variable tales como campos o propiedades.  
  
 **Identificador de error:** BC32010  
  
### Para corregir este error  
  
1.  Asegúrese de que los nombres de atributo y miembro estén escritos correctamente.  
  
2.  Quite el argumento del bloque de atributos si el miembro es no variable.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Aplicación de los atributos](http://msdn.microsoft.com/es-es/2b1703ed-4437-49b3-bc0b-568094324f47)