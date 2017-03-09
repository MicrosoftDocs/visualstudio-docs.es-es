---
title: "&#39;nombreTipo&#39; del ensamblado &#39;nombreEnsamblado&#39; se ha reenviado a s&#237; mismo y, por tanto, no es un tipo admitido. | Microsoft Docs"
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
  - "bc31425"
  - "vbc31425"
helpviewer_keywords: 
  - "BC31425"
  - "reenvío de tipos"
ms.assetid: e3275d55-3f4c-4bbc-9c8f-f55c4e973063
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;nombreTipo&#39; del ensamblado &#39;nombreEnsamblado&#39; se ha reenviado a s&#237; mismo y, por tanto, no es un tipo admitido.
Un ensamblado usa <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> para reenviar uno de sus tipos a otro ensamblado, pero especifica el mismo tipo en el mismo ensamblado.  
  
 El *reenvío de tipos* significa reasignar la definición de una clase, una estructura, una interfaz, un delegado o una enumeración a un ensamblado distinto de aquél en el que se definió originalmente. A menudo se usa junto con la *refactorización de código*, mediante la cual divide un ensamblado en dos o varios ensamblados o mueve el código de un ensamblado a otro.  
  
 Reenviar un tipo a sí mismo da como resultado un reenvío circular. Si otro ensamblado intenta tener acceso al tipo reenviado, irá a través de un reenvío sin fin sin llegar nunca a un tipo que no se haya reenviado.  
  
 **Identificador de error:** BC31425  
  
### Para corregir este error  
  
-   Reenvíe el tipo a un tipo de un ensamblado diferente o no lo reenvíe en absoluto.  
  
## Vea también  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>   
 [Reenvío de tipos \(C\+\+\/CLI\)](/visual-cpp/windows/type-forwarding-cpp-cli)   
 [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)   
 [NIB: Cómo: Agregar o quitar referencias usando el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)