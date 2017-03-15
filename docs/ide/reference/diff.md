---
title: "/Diff | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# /Diff
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Compara dos archivos.  Las diferencias se muestran en una ventana especial de Visual Studio.  
  
## Sintaxis  
  
```  
devenv /Diff SourceFile, TargetFile, [SourceDisplayName],  
[TargetDisplayName]  
```  
  
## Argumentos  
 `SourceFile`  
 Requerido.  La ruta de acceso completa y el nombre del primer archivo que se va a comparar.  
  
 `TargetFile`  
 Requerido.  La ruta de acceso completa y el nombre del segundo archivo que se va a comparar  
  
 `SourceDisplayName`  
 Opcional.  El nombre para mostrar del primer archivo.  
  
 `TargetDisplayName`  
 Opcional.  El nombre para mostrar del segundo archivo.