---
title: Los enumeradores | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26631c4b6ae6d6fb8d5bd00c772cc7f11943d459
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848105"
---
# <a name="enumerators"></a>Enumeradores
Esta sección enumeran los tipos de datos del enumerador en la API de complemento de Control de origen que debe conocer el complemento de control de código fuente.  
  
## <a name="in-this-section"></a>En esta sección  
 [Código de comando](../extensibility/command-code-enumerator.md)  
 Enumera las opciones para la [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) y [SccPopulateList](../extensibility/sccpopulatelist-function.md) funciones.  
  
 [Mensaje](../extensibility/message-enumerator.md)  
 Enumera los marcadores utilizados para la devolución de llamada impresión [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Código de estado de archivo](../extensibility/file-status-code-enumerator.md)  
 Contiene valores constantes con nombre que especifican el estado de un archivo bajo control de código fuente.  
  
 [Código de estado de directorio](../extensibility/directory-status-code-enumerator.md)  
 Contiene valores constantes con nombre que especifican el estado de un directorio bajo control de código fuente.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Crear un control de código fuente complemento](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Define el SDK de complemento de Control de origen y se describen los recursos incluidos.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Pide al usuario para las opciones avanzadas para el comando especificado.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Examina la lista de archivos para su estado actual. Además, utiliza el `pfnPopulate` función para notificar al llamador cuando un archivo no coincide con los criterios para la `nCommand`.  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Describe la función de devolución de llamada que se usa por [SccOpenProject](../extensibility/sccopenproject-function.md) para mostrar mensajes desde el complemento a través del IDE de control de origen.  
  
 [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)  
 Proporciona una lista completa de todos los elementos de la API de complemento de Control de código fuente.