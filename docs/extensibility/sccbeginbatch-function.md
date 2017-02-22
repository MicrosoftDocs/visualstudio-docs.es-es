---
title: "SccBeginBatch (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccBeginBatch"
helpviewer_keywords: 
  - "SccBeginBatch (función)"
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# SccBeginBatch (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función inicia una secuencia por lotes de las operaciones de control de código fuente. El [SccEndBatch](../extensibility/sccendbatch-function.md) se llamará para finalizar el lote. Estos lotes no pueden estar anidados.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccBeginBatch(void);  
```  
  
#### Parámetros  
 Ninguno.  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Lote de operaciones se inició correctamente.|  
|SCC\_E\_UNKNOWNERROR|Error no específico.|  
  
## Comentarios  
 Lotes de control de código fuente se usan para ejecutar las mismas operaciones en varios proyectos o varios contextos. Los lotes se pueden utilizar para eliminar los cuadros de diálogo de proyecto por redundantes de la experiencia del usuario durante una operación por lotes. El `SccBeginBatch` \(función\) y [SccEndBatch](../extensibility/sccendbatch-function.md) se utilizan como un par de funciones para indicar el comienzo y el final de una operación. No se pueden anidar.`SccBeginBatch` establece una marca que indica que una operación por lotes está en curso.  
  
 Mientras una operación por lotes está activada, el complemento de control de código fuente debe presentar a lo sumo un cuadro de diálogo para cualquier pregunta al usuario y la respuesta de ese cuadro de diálogo se aplican en todas las operaciones subsiguientes.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)