---
title: Los enumeradores | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0b9f71c83d70dc6daca7a3906b784d6babf8dea7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="enumerators"></a>Enumeradores
Esta sección enumeran los tipos de datos del enumerador en la API de complementos de Control de código fuente que debe conocer el complemento de control de código fuente.  
  
## <a name="in-this-section"></a>En esta sección  
 [Código de comando](../extensibility/command-code-enumerator.md)  
 Enumera las opciones para la [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) y [SccPopulateList](../extensibility/sccpopulatelist-function.md) funciones.  
  
 [Mensaje](../extensibility/message-enumerator.md)  
 Enumera las marcas que se usan para la devolución de llamada impresión [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Código de estado de archivo](../extensibility/file-status-code-enumerator.md)  
 Contiene valores constantes con nombre que especifican el estado de un archivo bajo control de código fuente.  
  
 [Código de estado de directorio](../extensibility/directory-status-code-enumerator.md)  
 Contiene valores constantes con nombre que especifican el estado de un directorio en el control de código fuente.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Creación de un complemento de control de código fuente](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Define el SDK de complemento de Control de origen y se describen los recursos incluidos.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Pide al usuario para las opciones avanzadas para el comando determinado.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Examina la lista de archivos para su estado actual. Además, usa el `pfnPopulate` función para notificar al llamador cuando un archivo no coincide con los criterios para la `nCommand`.  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Describe la función de devolución de llamada que se usa por [SccOpenProject](../extensibility/sccopenproject-function.md) para mostrar mensajes desde el complemento mediante el IDE de control de código fuente.  
  
 [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)  
 Proporciona una lista completa de todos los elementos de la API de complementos de Control de código fuente.