---
title: "SccEndBatch (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccEndBatch"
helpviewer_keywords: 
  - "SccEndBatch (función)"
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccEndBatch (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función finaliza un lote de operaciones de control de código fuente. Estos lotes no pueden estar anidados.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccEndBatch(void);  
```  
  
#### Parámetros  
 Ninguno.  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Lote de operaciones concluido correctamente.|  
|SCC\_E\_UNKNOWNERROR|Error no específico.|  
  
## Comentarios  
 Lotes de control de código fuente se usan para ejecutar las mismas operaciones de control de código fuente en varios proyectos o varios contextos. Los lotes se pueden utilizar para eliminar los cuadros de diálogo redundantes de la experiencia del usuario durante una operación por lotes. El [SccBeginBatch](../extensibility/sccbeginbatch-function.md) y `SccEndBatch` \(función\) se utilizan como un par para indicar el principio y el final de una operación. No se pueden anidar.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)