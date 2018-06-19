---
title: Funciones de devolución de llamada implementadas por el IDE | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ffdcc7d92770f486f9a345acf14e12e14214a2b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109693"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Funciones de devolución de llamada implementadas por el IDE
Para realizar la integración con el entorno de desarrollo integrado (IDE) como sin problemas como sea posible y para proporcionar una experiencia unificada para el usuario final, el complemento de control de código fuente puede utilizar las funciones de devolución de llamada que se implementan mediante el IDE. El complemento puede llamar a estas funciones en los momentos adecuados durante una operación de control de código fuente para pasar información al IDE; el IDE, a continuación, puede mostrar esta información como los elementos incrustados en su interfaz de usuario nativa. El usuario tiene una experiencia menos fragmentada en este escenario que si el complemento usa su propia interfaz de usuario.  
  
 El archivo de encabezado necesario es scc.h. La ubicación predeterminada es \Program Files\VSIP 8.0\EnvSDK\common\inc\\. También está en la carpeta VSIP con el ejemplo de complemento de control de código fuente en \Program Files\VSIP 8.0\MSSCCI\\.  
  
## <a name="in-this-section"></a>En esta sección  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Describe la función de devolución de llamada que se usa por [SccOpenProject](../extensibility/sccopenproject-function.md) para mostrar mensajes desde el complemento mediante el IDE de control de código fuente.  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 Describe la función de devolución de llamada que se usa por [SccPopulateList](../extensibility/sccpopulatelist-function.md) cuando el IDE no tiene acceso completo a la información que solo está disponible para el complemento, como una lista completa de los archivos bajo control de versiones de control de código fuente.  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 Describe la función de devolución de llamada que usa el [SccQueryChanges](../extensibility/sccquerychanges-function.md) operación.  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 Describe la función de devolución de llamada que usa el [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) operación.  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 Describe la función de devolución de llamada definida por una llamada a la [SccSetOption](../extensibility/sccsetoption-function.md) que permite el control de código fuente de complemento para la comunicación de cambios de nombre de nuevo con el IDE.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 Abre un proyecto.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Examina la lista de archivos para su estado actual. Además, usa el `pfnPopulate` función para notificar al llamador cuando un archivo no coincide con los criterios para la `nCommand`.  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 Examina una lista de directorios y archivos en un proyecto o los proyectos que están bajo control de código fuente. Cada nombre de archivo y directorio que se encuentra se pasa a una función de devolución de llamada.  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 Examina los cambios en el nombre que se realizaron en una lista de archivos. Cada nombre de archivo se pasa a una función de devolución de llamada junto con su estado de cambio.  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 Establece una amplia variedad de opciones. Cada opción empieza con `SCC_OPT_xxx` y tiene su propio conjunto definido de valores.  
  
 [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)  
 Describe el contenido de la sección de referencia del SDK de complemento de Control de origen.