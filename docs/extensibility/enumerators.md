---
title: "Enumeradores | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "control de código fuente plug-ins, enumeradores"
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# Enumeradores
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta sección enumeran los tipos de datos del enumerador en la API de complementos de Control de código fuente que debe conocer el complemento de control de código fuente.  
  
## En esta sección  
 [Código de comando](../extensibility/command-code-enumerator.md)  
 Enumera las opciones para el [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) y [SccPopulateList](../extensibility/sccpopulatelist-function.md) funciones.  
  
 [Mensaje](../extensibility/message-enumerator.md)  
 Enumera los indicadores que se utilizan para la devolución de llamada impresión [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Código de estado de archivo](../extensibility/file-status-code-enumerator.md)  
 Contiene valores constantes con nombre que especifican el estado de un archivo bajo control de código fuente.  
  
 [Código de estado de directorio](../extensibility/directory-status-code-enumerator.md)  
 Contiene valores constantes con nombre que especifican el estado de un directorio bajo control de código fuente.  
  
## Secciones relacionadas  
 [Creación de un Control de origen de complemento](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Define el SDK de complemento de Control de origen y se describen los recursos incluidos.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Pide al usuario opciones avanzadas para el comando especificado.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Examina la lista de archivos de su estado actual. Además, utiliza el `pfnPopulate` función para notificar al llamador cuando un archivo no coincide con los criterios para la `nCommand`.  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Describe la función de devolución de llamada que usa [SccOpenProject](../extensibility/sccopenproject-function.md) para mostrar mensajes desde el control de código fuente mediante el IDE.  
  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)  
 Proporciona una lista completa de todos los elementos de la API de complementos de Control de código fuente.