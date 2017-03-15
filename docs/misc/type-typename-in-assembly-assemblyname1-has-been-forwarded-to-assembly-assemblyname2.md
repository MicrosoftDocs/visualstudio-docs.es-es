---
title: "El tipo &#39;&lt;typename&gt;&#39; del ensamblado &#39;&lt;assemblyname1&gt;&#39; se ha reenviado al ensamblado &#39;&lt;assemblyname2&gt;&#39; | Microsoft Docs"
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
  - "vbc31424"
  - "bc31424"
helpviewer_keywords: 
  - "BC31424"
  - "reenvío de tipos"
ms.assetid: 0f53e613-c1cb-4722-acb5-afa3091e277b
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El tipo &#39;&lt;typename&gt;&#39; del ensamblado &#39;&lt;assemblyname1&gt;&#39; se ha reenviado al ensamblado &#39;&lt;assemblyname2&gt;&#39;
El tipo '\<typename\>' del ensamblado '\<assemblyname1\>' se ha reenviado al ensamblado '\<assemblyname2\>'. Falta una referencia a '\<assemblyname2\>' en el proyecto o falta el tipo '\<typename\>' en el ensamblado '\<assemblyname2\>'.  
  
 Una expresión en el código fuente para un ensamblado hace referencia a un tipo que se ha reenviado a otro ensamblado, pero no se encuentra el tipo en el ensamblado de destino.  
  
 *Reenvío de tipos* significa reasignar la definición de una clase, estructura, interfaz, un delegado o una enumeración a un ensamblado distinto de aquél en el que se definió originalmente. A menudo se usa junto con la *refactorización de código*, mediante la cual divide un ensamblado en dos o varios ensamblados o mueve el código de un ensamblado a otro.  
  
 Aunque el tipo siga estando disponible temporalmente en el ensamblado original, es probable que quede sin definir cuando la refactorización de código quite el ensamblado original.  
  
 **Identificador de error:** BC31424  
  
### Para corregir este error  
  
-   Asegúrese de que el tipo está presente en el ensamblado de destino.  
  
-   Asegúrese de que el proyecto tiene una referencia al ensamblado de destino.  
  
## Vea también  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>   
 [Reenvío de tipos \(C\+\+\/CLI\)](/visual-cpp/windows/type-forwarding-cpp-cli)   
 [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)   
 [NO ESTÁ EN LA COMPILACIÓN: Cómo: Agregar o quitar referencias utilizando el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)