---
title: "La referencia a un miembro no compartido requiere una referencia de objeto. | Microsoft Docs"
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
  - "bc30469"
  - "vbc30469"
helpviewer_keywords: 
  - "BC30469"
ms.assetid: af503e8b-2e1f-4f91-a07f-b1ddd73dd4a6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La referencia a un miembro no compartido requiere una referencia de objeto.
Ha hecho referencia a un miembro no compartido dentro del código y no ha podido proporcionar una referencia de objeto. No puede usar el nombre de la clase para calificar a un miembro no compartido. La instancia debe estar declarada como una variable de objeto y luego que el nombre de variable haga referencia a esta.  
  
 **Identificador del error:** BC30469  
  
### Para corregir este error  
  
1.  Declare la instancia como una variable de objeto.  
  
2.  Haga referencia a la instancia mediante el nombre de variable.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Introducción a las clases](http://msdn.microsoft.com/es-es/cc2355a2-cb98-4353-9440-736585aec46c)   
 [NO ESTÁ EN LA COMPILACIÓN: Miembros compartidos en Visual Basic](http://msdn.microsoft.com/es-es/dbc3783f-83a2-4225-995d-c2d6d025663d)   
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)   
 [NO ESTÁ EN LA COMPILACIÓN: Resolver una referencia cuando varias variables tienen el mismo nombre](http://msdn.microsoft.com/es-es/9601e39f-1911-44e1-ace5-3f6e090408b9)