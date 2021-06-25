---
title: Marcas de funcionalidad | Microsoft Docs
description: Obtenga información sobre las SCC_CAP_xxx que indican las funcionalidades de un complemento de control de código fuente y las marcas de SCC_EXCAP_xxx que indican las funcionalidades extendidas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3fdb660fd4e7c595f522686280f8bec6c0acae81
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905103"
---
# <a name="capability-flags"></a>Marcas de funcionalidad
Las SCC_CAP_ *xxx* son marcas de bits que se usan para indicar las funciones de un complemento de control de código fuente. Las SCC_EXCAP_ *xxx* son marcas incrementales que indican funcionalidades extendidas y se resuelven en valores enteros.

|Código de funcionalidad|Valor|Descripción|
|---------------------|-----------|-----------------|
|`SCC_CAP_REMOVE`|0x00000001L|Admite el [comando SccRemove](../extensibility/sccremove-function.md) y .|
|`SCC_CAP_RENAME`|0x00000002L|Admite el [comando SccRename](../extensibility/sccrename-function.md) y .|
|`SCC_CAP_DIFF`|0x00000004L|Admite [SccDiff](../extensibility/sccdiff-function.md) y el comando .|
|`SCC_CAP_HISTORY`|0x00000008L|Admite [SccHistory y](../extensibility/scchistory-function.md) el comando .|
|`SCC_CAP_PROPERTIES`|0x00000010L|Admite el [comando SccProperties](../extensibility/sccproperties-function.md) y .|
|`SCC_CAP_RUNSCC`|0x00000020L|Admite el [comando SccRunScc](../extensibility/sccrunscc-function.md) y .|
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Admite el [comando y SccGetCommandOptions.](../extensibility/sccgetcommandoptions-function.md)|
|`SCC_CAP_QUERYINFO`|0x00000080L|Admite el [comando SccQueryInfo](../extensibility/sccqueryinfo-function.md) y .|
|`SCC_CAP_GETEVENTS`|0x00000100L|Admite [SccGetEvents](../extensibility/sccgetevents-function.md) y el comando .|
|`SCC_CAP_GETPROJPATH`|0x00000200L|Admite el [comando SccGetProjPath](../extensibility/sccgetprojpath-function.md) y .|
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Admite el [comando SccAddFromScc](../extensibility/sccaddfromscc-function.md) y .|
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Admite un comentario sobre la desprotección.|
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Admite un comentario en checkin.|
|`SCC_CAP_COMMENTADD`|0x00002000L|Admite un comentario en Agregar.|
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Admite un comentario en Quitar.|
|`SCC_CAP_TEXTOUT`|0x00008000L|Escribe texto en una función de salida proporcionada por ide.|
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Admite el almacenamiento de archivos sin diferencias.|
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Admite varios historiales de archivos.|
|`SCC_CAP_IGNORECASE`|0x00800000L|Admite la comparación de archivos sin mayúsculas y minúsculas.|
|`SCC_CAP_IGNORESPACE`|0x01000000L|Admite la comparación de archivos que omite los espacios en blanco.|
|`SCC_CAP_POPULATELIST`|0x02000000L|Admite la búsqueda de archivos adicionales.|
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Admite comentarios al crear un proyecto.|
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Admite la diferencia en todos los estados si está bajo control.|
|`SCC_CAP_GET_NOUI`|0x20000000L|El complemento no admite una interfaz de usuario para Get, pero el IDE todavía puede llamar a [SccGet](../extensibility/sccget-function.md).|
|`SCC_CAP_REENTRANT`|0x40000000L|El complemento es reentrante y seguro para subprocesos. En la versión 1.0, no se supone que ningún complemento sea reentrante y seguro para subprocesos. Si un complemento 1.1 establece este bit, el host puede abrir varios proyectos en paralelo.|

## <a name="capability-bits-added-in-version-12"></a>Bits de funcionalidad agregados en la versión 1.2

|Código de funcionalidad|Valor|Descripción|
|---------------------|-----------|-----------------|
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Admite [SccCreateSubProject](../extensibility/scccreatesubproject-function.md).|
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Admite [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).|
|`SCC_CAP_BATCH`|0x00040000L|Admite [SccBeginBatch](../extensibility/sccbeginbatch-function.md) y [SccEndBatch.](../extensibility/sccendbatch-function.md)|
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Admite [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md).|
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Admite [SccDirDiff](../extensibility/sccdirdiff-function.md).|
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Admite varias desprotecciones en un archivo y [SccIsMultiCheckoutEnabled.](../extensibility/sccismulticheckoutenabled-function.md)|
|`SCC_CAP_SCCFILE`|0x80000000L|Admite el *archivo MSSCCPRJ.SCC* (sujeto a la invalidación de usuario/administrador) y [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md).|

## <a name="capability-bits-added-in-version-13"></a>Bits de funcionalidad agregados en la versión 1.3
 Estas marcas se pasan de una en una a la función [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) para determinar si se admite la funcionalidad.

|Código de funcionalidad extendida|Valor|Descripción|
|------------------------------|-----------|-----------------|
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Admite la `SCC_CHECKOUT_LOCALVER` opción para las desprotecciones.|
|`SCC_EXCAP_BACKGROUND_GET`|2|Admite [SccBackgroundGet.](../extensibility/sccbackgroundget-function.md)|
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Admite [SccEnumChangedFiles.](../extensibility/sccenumchangedfiles-function.md)|
|`SCC_EXCAP_POPULATELIST_DIR`|4|Admite la búsqueda de directorios adicionales.|
|`SCC_EXCAP_QUERYCHANGES`|5|Admite la enumeración de cambios de archivo.|
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Admite [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md).|
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Admite [SccGetUserOption.](../extensibility/sccgetuseroption-function.md)|
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Admite la llamada a SccQueryInfo en varios subprocesos.|
|`SCC_EXCAP_REMOVE_DIR`|9|Admite la función SccRemoveDir.|
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Puede eliminar archivos desprotegiendo.|
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Puede cambiar el nombre de los archivos desprotegiendo.|

## <a name="see-also"></a>Consulta también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
