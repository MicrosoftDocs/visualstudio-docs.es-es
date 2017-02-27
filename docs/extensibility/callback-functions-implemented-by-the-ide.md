---
title: "Funciones de devoluci&#243;n de llamada implementadas por el IDE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "origen control complementos, las funciones de devolución de llamada"
  - "funciones de devolución de llamada, los complementos de control de código fuente"
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# Funciones de devoluci&#243;n de llamada implementadas por el IDE
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para realizar la integración con el entorno de desarrollo integrado \(IDE\) como transparente como sea posible y para proporcionar una experiencia unificada para el usuario final, el complemento de control de código fuente puede utilizar las funciones de devolución de llamada que se implementan mediante el IDE. El complemento puede llamar a estas funciones en los momentos adecuados durante una operación de control de código fuente para pasar información al IDE; el IDE puede mostrar esta información como elementos incrustados en su interfaz de usuario nativa. El usuario tiene una experiencia menos fragmentada en este escenario que si el complemento emplea su propia interfaz de usuario.  
  
 El archivo de encabezado necesario es scc.h. La ubicación predeterminada es \\Program Files\\VSIP 8.0\\EnvSDK\\common\\inc\\. También es la carpeta VSIP que tiene el ejemplo de complemento de control de código fuente en \\Program Files\\VSIP 8.0\\MSSCCI\\.  
  
## En esta sección  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Describe la función de devolución de llamada que usa [SccOpenProject](../extensibility/sccopenproject-function.md) para mostrar mensajes desde el control de código fuente mediante el IDE.  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 Describe la función de devolución de llamada que usa [SccPopulateList](../extensibility/sccpopulatelist-function.md) cuando el IDE no tiene acceso completo a la información que solo está disponible para el control de código fuente, como una lista completa de los archivos bajo control de versiones.  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 Describe la función de devolución de llamada que usa el [SccQueryChanges](../extensibility/sccquerychanges-function.md) operación.  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 Describe la función de devolución de llamada que usa el [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) operación.  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 Describe la función de devolución de llamada definida por una llamada a la [SccSetOption](../extensibility/sccsetoption-function.md) que permite el control de código fuente para comunicar los cambios de nombre de nuevo en el IDE.  
  
## Secciones relacionadas  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 Abre un proyecto.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Examina la lista de archivos de su estado actual. Además, utiliza el `pfnPopulate` función para notificar al llamador cuando un archivo no coincide con los criterios para la `nCommand`.  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 Examina una lista de directorios y archivos en un proyecto o proyectos que están bajo control de código fuente. Cada nombre de archivo y directorio encontrado se pasa a una función de devolución de llamada.  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 Examina los cambios en el nombre que se realizaron en una lista de archivos. Cada nombre de archivo se pasa a una función de devolución de llamada junto con su estado de cambio.  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 Establece una amplia variedad de opciones. Cada opción comienza con `SCC_OPT_xxx` y tiene su propio conjunto definido de valores.  
  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)  
 Describe el contenido de la sección de referencia del SDK de complemento de Control de origen.