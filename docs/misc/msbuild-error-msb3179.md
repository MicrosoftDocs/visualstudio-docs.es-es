---
title: "Error de MSBuild MSB3179 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.ComImport"
helpviewer_keywords: 
  - "MSB3179"
ms.assetid: fa744f6c-e398-4e60-b4f7-455ace7e3bd2
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3179
**MSB3179: Existe un problema que aísla la referencia COM '\<ensamblado\>': '\<error\>'**  
  
 Se trata de un mensaje de error genérico que indica que hay un problema con la generación de las entradas COM RegFree en el manifiesto de aplicación \(tal y como especifica el parámetro de tarea `IsolatedComReferences`\).  La última parte del mensaje de error contiene más información sobre la naturaleza del problema.  Una posible causa de este error es que los componentes COM RegFree no están correctamente registrados en el equipo de compilación.  
  
### Para corregir este error  
  
-   Asegúrese de que todos los componentes COM están registrados en el equipo de compilación.  
  
## Vea también  
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)