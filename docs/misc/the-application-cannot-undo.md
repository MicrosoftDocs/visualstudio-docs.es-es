---
title: "The application cannot undo. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_MULTIDOCUNDO_BLOCKED"
  - "vs.message.0x800A00AB"
ms.assetid: c2b5e2af-0e64-4cff-9814-b80e26cd240e
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The application cannot undo.
Este error ocurre normalmente cuando se intenta realizar una operación de deshacer para un elemento que posee una fase de reversión vinculada a otro archivo.  Si tras la la modificación vinculada se realiza alguna acción, Visual Studio no podrá deshacer el cambio.  
  
### Para corregir este error  
  
1.  Deshaga manualmente el cambio.  
  
## Vea también  
 [Buscar y reemplazar texto](../ide/finding-and-replacing-text.md)