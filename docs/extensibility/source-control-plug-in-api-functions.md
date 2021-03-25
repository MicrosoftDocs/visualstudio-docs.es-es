---
title: Funciones de la API del complemento de control de código fuente | Microsoft Docs
description: Obtenga información sobre las funciones que proporciona la API del complemento de control de código fuente, que debe ser implementada por el complemento de control de código fuente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c28c175d53fb37cf890dad4240a84fb132f6af35
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090127"
---
# <a name="source-control-plug-in-api-functions"></a>Funciones de API de complemento de control de código fuente
La API del complemento de control de código fuente proporciona las siguientes funciones, que debe implementar el complemento de control de código fuente de acuerdo con esta API. Las firmas de cada función y la semántica asociada a las marcas de bits y otros parámetros se describen en detalle en esta referencia.

## <a name="initialization-and-housekeeping-functions"></a>Funciones de inicialización y mantenimiento

|Función|Descripción|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Cierra un proyecto.|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Solicita al usuario opciones avanzadas para el comando especificado.|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Devuelve la versión del complemento de control de código fuente.|
|[SccInitialize](../extensibility/sccinitialize-function.md)|Inicializa el complemento de control de código fuente. Se llama una vez para cada instancia del complemento.|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Abre un proyecto.|
|[SccSetOption](../extensibility/sccsetoption-function.md)|Función genérica que se usa para establecer una amplia variedad de opciones. Cada opción comienza con `SCC_OPT_xxx` y tiene su propio conjunto de valores definido.|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Se le llama una vez cuando es necesario desenchufar un complemento de control de código fuente.|

## <a name="core-source-control-functions"></a>Funciones de control de código fuente principales

|Función|Descripción|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|Agrega una matriz de archivos especificados por nombres de ruta de acceso completos al sistema de control de código fuente.|
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Permite al usuario buscar archivos que ya están en el sistema de control de código fuente y, a continuación, convertirlos en parte del proyecto actual.|
|[SccCheckin](../extensibility/scccheckin-function.md)|Protege una matriz de archivos.|
|[SccCheckout](../extensibility/scccheckout-function.md)|Desprotege una matriz de archivos.|
|[SccDiff](../extensibility/sccdiff-function.md)|Muestra las diferencias entre el archivo del usuario local especificado por un nombre de ruta de acceso completo y la versión bajo control de código fuente.|
|[SccGet](../extensibility/sccget-function.md)|Recupera una copia de solo lectura de un conjunto de archivos.|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Comprueba el estado de los archivos que el autor de la llamada ha solicitado (a través de `SccQueryInfo` ).|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Hace que el complemento de control de código fuente solicite al usuario una ruta de acceso del proyecto que sea significativa para el complemento.|
|[SccHistory](../extensibility/scchistory-function.md)|Muestra el historial de una matriz de nombres de archivo locales completos.|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Examina la lista de archivos en busca de su estado actual. Además, utiliza la `pfnPopulate` función para notificar al llamador cuando un archivo no coincide con los criterios de `nCommand` .|
|[SccProperties](../extensibility/sccproperties-function.md)|Muestra las propiedades de un archivo completo.|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Examina una lista de archivos completos para su estado actual.|
|[SccRemove](../extensibility/sccremove-function.md)|Quita la matriz de archivos completos del sistema de control de código fuente.|
|[SccRename](../extensibility/sccrename-function.md)|Cambia el nombre del archivo dado a un nuevo nombre en el sistema de control de código fuente.|
|[SccRunScc](../extensibility/sccrunscc-function.md)|Obtiene acceso a toda la gama de características del sistema de control de código fuente.|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Deshace la desprotección de una matriz de archivos.|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Funciones que admiten funcionalidad adicional (versión 1,2 de la API del complemento de control de código fuente)
 Este grupo de funciones define la funcionalidad adicional incluida en la versión 1,2 de la API del complemento de control de código fuente. Proporcionan acceso a características y funciones de control de código fuente más avanzadas.

|Función|Descripción|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Inicia una operación por lotes.|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Crea un subproyecto con el nombre especificado en un proyecto primario existente.|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Muestra las diferencias entre el directorio del usuario local especificado por un nombre de ruta de acceso completo y la ubicación de la base de datos de control de código fuente.|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Examina una lista de directorios completos para su estado actual.|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Finaliza una operación por lotes.|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Devuelve la ruta de acceso primaria del proyecto dado (el proyecto debe existir).|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Comprueba si se permiten varias desprotecciones en un archivo.|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Comprueba si el complemento creará MSSCCPRJ. Archivos SCC.|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Funciones que admiten la funcionalidad avanzada (versión 1,3 de la API del complemento de control de código fuente)
 Este grupo de funciones define la funcionalidad adicional incluida en la versión 1,3 de la API del complemento de control de código fuente. Proporcionan acceso a características y funciones de control de código fuente más avanzadas.

|Función|Descripción|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Agrega una lista de archivos del control de código fuente al proyecto actual.|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Recupera una lista de archivos del control de código fuente sin una interfaz de usuario.|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Recupera una lista de archivos en el control de código fuente que son diferentes de los archivos locales.|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Recupera las marcas que especifican funciones extendidas admitidas por el complemento de control de código fuente.|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Recupera opciones específicas del usuario.|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Examina una lista de directorios y archivos de un proyecto o proyectos que están bajo control de código fuente. Cada nombre de archivo y directorio encontrado se pasa a una función de devolución de llamada.|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Examina los cambios de nombre realizados en una lista de archivos. Cada nombre de archivo se pasa a una función de devolución de llamada con su estado de cambio.|

## <a name="requirements"></a>Requisitos
 Encabezado: SCC. h

 (Se proporciona en la carpeta Common includes del SDK de entorno, de forma predeterminada *[unidad]* \Archivos de Files\VSIP 8.0 \ EnvSDK\common\inc; también se proporciona en la carpeta VSIP con el ejemplo MSSCCI, *[unidad]* \Archivos de Files\VSIP 8.0 \ MSSCCI).

## <a name="see-also"></a>Consulte también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [Creación de un complemento de control de código fuente](../extensibility/internals/creating-a-source-control-plug-in.md)
