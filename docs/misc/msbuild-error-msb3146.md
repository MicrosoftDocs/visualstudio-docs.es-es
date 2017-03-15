---
title: "Error de MSBuild MSB3146 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.MissingDependency"
helpviewer_keywords: 
  - "MSB3146"
ms.assetid: 717fd649-3024-427d-a068-cff8034ffc0a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3146
**MSB3146: El elemento '\<paquete\>' es requerido por '\<paquete\>', pero no se incluyó.**  
  
 Este error se produce cuando un paquete de arranque depende de otro, pero se ha seleccionado sólo la instalación del paquete dependiente.  Por ejemplo, el paquete B depende del paquete A, pero sólo se instala B.  
  
### Para corregir este error  
  
-   Incluya el paquete requerido.