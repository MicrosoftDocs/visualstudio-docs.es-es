---
title: "Error de MSBuild MSB3142 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.CopyError"
helpviewer_keywords: 
  - "MSB3142"
ms.assetid: acca7437-6c72-446c-a6b5-a1c051b6855f
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3142
**MSB3142: Error al intentar copiar '\<archivo\>' en' \<carpeta\>': '\<error\>'**  
  
 Se genera este error al copiar setup.bin en el directorio de resultados de la compilación.  Las causas posibles de este error son:  
  
-   No tiene permiso para copiar en el directorio de resultados.  
  
-   El disco está lleno.  
  
 Estas son la mismas posibles razones que provocan el error de file.copy o directory.createdirectory.  
  
## Vea también  
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)