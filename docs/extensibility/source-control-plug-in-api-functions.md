---
title: Funciones de la API de complemento de Control de origen | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: beaab13c76b3d50f97662e66c1f72dc83161e96d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-plug-in-api-functions"></a>Funciones de API de complemento de Control de código fuente
La API de complementos de Control de código fuente proporciona las siguientes funciones, que deben ser implementadas por el complemento con arreglo a esta API de control de código fuente. Las firmas de cada función y la semántica asociada a las marcas de bits y otros parámetros se describen detalladamente en esta referencia.  
  
## <a name="initialization-and-housekeeping-functions"></a>Inicialización y funciones de mantenimiento  
  
|Función|Descripción|  
|--------------|-----------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Cierra un proyecto.|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Pide al usuario para las opciones avanzadas para el comando determinado.|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Devuelve la versión del control de código fuente de complemento.|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|Inicializa el complemento de control de código fuente. Se llama una vez para cada instancia del complemento.|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Abre un proyecto.|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|Una función genérica que se usa para establecer una gran variedad de opciones. Cada opción empieza con `SCC_OPT_xxx` y tiene su propio conjunto definido de valores.|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Llama una vez cuando un complemento de control de origen debe ser desconectado.|  
  
## <a name="core-source-control-functions"></a>Funciones de Control de origen de núcleo  
  
|Función|Descripción|  
|--------------|-----------------|  
|[SccAdd](../extensibility/sccadd-function.md)|Agrega una matriz de archivos especificados por los nombres de ruta de acceso completa para el sistema de control de código fuente.|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Permite al usuario examinar archivos que ya están en el sistema de control de código fuente y, a continuación, que los archivos del proyecto actual.|  
|[SccCheckin](../extensibility/scccheckin-function.md)|Comprobaciones en una matriz de archivos.|  
|[SccCheckout](../extensibility/scccheckout-function.md)|Desprotege una matriz de archivos.|  
|[SccDiff](../extensibility/sccdiff-function.md)|Muestra las diferencias entre los archivos del usuario local especificado por un nombre de ruta de acceso completa y la versión bajo control de código fuente.|  
|[SccGet](../extensibility/sccget-function.md)|Recupera una copia de solo lectura de un conjunto de archivos.|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Comprueba el estado de los archivos que el llamador ha solicitado sobre (a través de `SccQueryInfo`).|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Hace que el complemento para pedir al usuario una ruta de acceso del proyecto que sea significativo para el complemento de control de código fuente.|  
|[SccHistory](../extensibility/scchistory-function.md)|Muestra el historial de una matriz de nombres de archivo local completa.|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Examina la lista de archivos para su estado actual. Además, usa el `pfnPopulate` función para notificar al llamador cuando un archivo no coincide con los criterios para la `nCommand`.|  
|[SccProperties](../extensibility/sccproperties-function.md)|Muestra las propiedades de un archivo completo.|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Examina una lista de nombres de archivo completos para su estado actual.|  
|[SccRemove](../extensibility/sccremove-function.md)|Quita la matriz de nombres de archivo completos desde el sistema de control de código fuente.|  
|[SccRename](../extensibility/sccrename-function.md)|Cambia el nombre del archivo especificado a un nuevo nombre en el sistema de control de código fuente.|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|Tiene acceso a la amplia gama de características del sistema de control de código fuente.|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Deshace una desprotección de una matriz de archivos.|  
  
## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Funciones que admiten una capacidad adicional (versión 1.2 de la API de complemento de Control de código fuente)  
 Este grupo de funciones define la funcionalidad adicional que se incluye en la versión 1.2 de la API de complemento de Control de origen. Proporcionan acceso a características de control de código fuente y capacidades más avanzadas.  
  
|Función|Descripción|  
|--------------|-----------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Inicia una operación por lotes.|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Crea un subproyecto con el nombre especificado en un proyecto existente del elemento primario.|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Muestra las diferencias entre el directorio del usuario local especificado por un nombre de ruta de acceso completa y la ubicación de base de datos de control de código fuente.|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Examina una lista de directorios completos para su estado actual.|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Finaliza una operación por lotes.|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Devuelve primarios ruta de acceso del proyecto especificado (el proyecto debe existir).|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Comprueba si se permiten varias desprotecciones en un archivo.|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Comprueba si el complemento va a crear MSSCCPRJ. Archivos de control de código fuente.|  
  
## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Funciones que admiten funcionalidad avanzada (versión 1.3 de la API de complemento de Control de código fuente)  
 Este grupo de funciones define la funcionalidad adicional que se incluye en la versión 1.3 de la API de complemento de Control de origen. Proporcionan acceso a características de control de código fuente y capacidades más avanzadas.  
  
|Función|Descripción|  
|--------------|-----------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Agrega una lista de archivos de control de código fuente al proyecto actual.|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Recupera una lista de archivos de control de código fuente sin una interfaz de usuario.|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Recupera una lista de archivos de control de código fuente que son diferentes de los archivos locales.|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Recupera las marcas que especifican las capacidades extendidas compatibles con el complemento de control de código fuente.|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Recupera las opciones específicas del usuario.|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Examina una lista de directorios y archivos en un proyecto o los proyectos que están bajo control de código fuente. Cada nombre de archivo y directorio que se encuentra se pasa a una función de devolución de llamada.|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Examina los cambios realizados en una lista de archivos en el nombre. Cada nombre de archivo se pasa a una función de devolución de llamada con su estado de cambio.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: scc.h  
  
 (Proporcionado en el SDK de entorno común incluye carpeta, de forma predeterminada *[unidad]*\Program Files\VSIP 8.0\EnvSDK\common\inc; también se proporciona en la carpeta VSIP con el ejemplo MSSCCI, *[unidad]*\Program Files\VSIP 8.0\MSSCCI).  
  
## <a name="see-also"></a>Vea también  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)   
 [Creación de un complemento de control de código fuente](../extensibility/internals/creating-a-source-control-plug-in.md)