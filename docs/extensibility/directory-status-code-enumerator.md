---
title: "Enumerador de c&#243;digo de estado de directorio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "enumerador de código de estado de directorio"
  - "origen control complementos, enumeración del estado de directorio"
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Enumerador de c&#243;digo de estado de directorio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El `SccDirStatus` enumerador contiene valores constantes con nombre que especifican el estado de un directorio en el sistema de control de código fuente. Esta enumeración la usa la clase [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Esto se introdujo en la versión 1.2 de la API de complementos de Control de código fuente.  
  
## Sintaxis  
  
```  
enum SccDirStatus {  
   SCC_DIRSTATUS_INVALID       = -1L,  
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,  
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,  
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L  
};  
```  
  
## Miembros  
 SCC\_DIRSTATUS\_INVALID  
 No se pudo obtener el estado; No confíe en él.  
  
 SCC\_DIRSTATUS\_NOTCONTROLLED  
 Directorio no está bajo control de código fuente.  
  
 SCC\_DIRSTATUS\_CONTROLLED  
 Directorio está bajo control de código fuente.  
  
 SCC\_DIRSTATUS\_EMPTYPROJ  
 Proyecto correspondiente a este directorio está vacío.  
  
## Vea también  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)