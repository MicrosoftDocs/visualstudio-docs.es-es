---
title: Funciones de API de plug-in de control de código fuente ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce685729dda8750d772e244398b736cff4951b72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699924"
---
# <a name="source-control-plug-in-api-functions"></a>Funciones de API de complemento de control de código fuente
La API de complemento de Control de código fuente proporciona las siguientes funciones, que debe implementar el complemento de control de código fuente de acuerdo con esta API. Las firmas de cada función y la semántica asociada con los indicadores de bits y otros parámetros se describen en detalle en esta referencia.

## <a name="initialization-and-housekeeping-functions"></a>Funciones de inicialización y limpieza

|Función|Descripción|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Cierra un proyecto.|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Solicita al usuario opciones avanzadas para el comando dado.|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Devuelve la versión del complemento de control de código fuente.|
|[SccInitialize](../extensibility/sccinitialize-function.md)|Inicializa el complemento de control de código fuente. Se llama una vez para cada instancia del plug-in.|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Abre un proyecto.|
|[SccSetOption](../extensibility/sccsetoption-function.md)|Una función genérica utilizada para establecer una amplia variedad de opciones. Cada opción `SCC_OPT_xxx` comienza con y tiene su propio conjunto definido de valores.|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Se llama una vez cuando es necesario desconectar un complemento de control de código fuente.|

## <a name="core-source-control-functions"></a>Funciones de control de código fuente principales

|Función|Descripción|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|Agrega una matriz de archivos especificados por nombres de ruta de acceso completos al sistema de control de código fuente.|
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Permite al usuario buscar archivos que ya están en el sistema de control de código fuente y, a continuación, hacer que esos archivos formen parte del proyecto actual.|
|[SccCheckin](../extensibility/scccheckin-function.md)|Comprueba una matriz de archivos.|
|[SccCheckout](../extensibility/scccheckout-function.md)|Desprotege una matriz de archivos.|
|[SccDiff](../extensibility/sccdiff-function.md)|Muestra las diferencias entre el archivo del usuario local especificado por un nombre de ruta de acceso completo y la versión bajo control de código fuente.|
|[SccGet](../extensibility/sccget-function.md)|Recupera una copia de solo lectura de un conjunto de archivos.|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Comprueba el estado de los archivos que `SccQueryInfo`el autor de la llamada ha preguntado (a través de ).|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Hace que el complemento de control de código fuente solicite al usuario una ruta de acceso del proyecto que sea significativa para el complemento.|
|[SccHistory](../extensibility/scchistory-function.md)|Muestra el historial de una matriz de nombres de archivo locales completos.|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Examina la lista de archivos para su estado actual. Además, `pfnPopulate` utiliza la función para notificar al autor `nCommand`de la llamada cuando un archivo no coincide con los criterios para el archivo .|
|[SccProperties](../extensibility/sccproperties-function.md)|Muestra las propiedades de un archivo completo.|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Examina una lista de archivos completos para su estado actual.|
|[SccRemove](../extensibility/sccremove-function.md)|Quita la matriz de archivos completos del sistema de control de código fuente.|
|[SccRename](../extensibility/sccrename-function.md)|Cambia el nombre del archivo dado a un nuevo nombre en el sistema de control de código fuente.|
|[SccRunScc](../extensibility/sccrunscc-function.md)|Tiene acceso a toda la gama de características del sistema de control de código fuente.|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Deshace una desprotección de una matriz de archivos.|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Funciones que admiten capacidad adicional (versión 1.2 de la API de complemento de Control de código fuente)
 Este grupo de funciones define la funcionalidad adicional incluida en la versión 1.2 de la API de complemento de Control de código fuente. Proporcionan acceso a funciones y características de control de código fuente más avanzadas.

|Función|Descripción|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Inicia una operación por lotes.|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Crea un subproyecto con el nombre especificado en un proyecto primario existente.|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Muestra las diferencias entre el directorio del usuario local especificado por un nombre de ruta de acceso completo y la ubicación de la base de datos de control de código fuente.|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Examina una lista de directorios completos para su estado actual.|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Finaliza una operación por lotes.|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Devuelve la ruta de acceso primaria del proyecto dado (el proyecto debe existir).|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Comprueba si se permiten varias desprotecciones en un archivo.|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Comprueba si el plug-in creará MSSCCPRJ. SCC.|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Funciones que admiten la capacidad avanzada (versión 1.3 de la API de complemento de Control de código fuente)
 Este grupo de funciones define la funcionalidad adicional incluida en la versión 1.3 de la API de complemento de Control de código fuente. Proporcionan acceso a funciones y características de control de código fuente más avanzadas.

|Función|Descripción|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Agrega una lista de archivos del control de código fuente al proyecto actual.|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Recupera una lista de archivos del control de código fuente sin una interfaz de usuario.|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Recupera una lista de archivos en el control de código fuente que son diferentes de los archivos locales.|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Recupera indicadores que especifican capacidades extendidas admitidas por el complemento de control de código fuente.|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Recupera opciones específicas del usuario.|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Examina una lista de directorios y archivos de un proyecto o proyectos que están bajo control de código fuente. Cada directorio y nombre de archivo encontrados se pasa a una función de devolución de llamada.|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Examina los cambios de nombre realizados en una lista de archivos. Cada nombre de archivo se pasa a una función de devolución de llamada con su estado de cambio.|

## <a name="requirements"></a>Requisitos
 Encabezado: scc.h

 (Suministrado en el SDK de entorno común incluye carpeta, de forma predeterminada *[unidad]*. *[drive]*

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [Creación de un complemento de control de código fuente](../extensibility/internals/creating-a-source-control-plug-in.md)
