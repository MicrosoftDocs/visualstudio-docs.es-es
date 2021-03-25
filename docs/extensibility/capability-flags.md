---
title: Marcas de capacidad | Microsoft Docs
description: Obtenga información sobre las marcas de SCC_CAP_xxx que indican las capacidades de un complemento de control de código fuente y las marcas de SCC_EXCAP_xxx que indican funcionalidades extendidas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 12acefb99de787d55bc0f932757dde5ea928c6cb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094931"
---
# <a name="capability-flags"></a>Marcas de capacidad
Las marcas SCC_CAP_ *XXX* son marcas de bits utilizadas para indicar las capacidades de un complemento de control de código fuente. Las marcas SCC_EXCAP_ *XXX* son marcas incrementales que indican funcionalidades extendidas y se resuelven en valores enteros.

|Código de funcionalidad|Value|Descripción|
|---------------------|-----------|-----------------|
|`SCC_CAP_REMOVE`|0x00000001L|Admite [SccRemove](../extensibility/sccremove-function.md) y el comando.|
|`SCC_CAP_RENAME`|0x00000002L|Admite [SccRename](../extensibility/sccrename-function.md) y el comando.|
|`SCC_CAP_DIFF`|0x00000004L|Admite [SccDiff](../extensibility/sccdiff-function.md) y el comando.|
|`SCC_CAP_HISTORY`|0x00000008L|Admite [SccHistory](../extensibility/scchistory-function.md) y el comando.|
|`SCC_CAP_PROPERTIES`|0x00000010L|Admite [SccProperties](../extensibility/sccproperties-function.md) y el comando.|
|`SCC_CAP_RUNSCC`|0x00000020L|Admite [SccRunScc](../extensibility/sccrunscc-function.md) y el comando.|
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Admite [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) y el comando.|
|`SCC_CAP_QUERYINFO`|0x00000080L|Admite [SccQueryInfo](../extensibility/sccqueryinfo-function.md) y el comando.|
|`SCC_CAP_GETEVENTS`|0x00000100L|Admite [SccGetEvents](../extensibility/sccgetevents-function.md) y el comando.|
|`SCC_CAP_GETPROJPATH`|0x00000200L|Admite [SccGetProjPath](../extensibility/sccgetprojpath-function.md) y el comando.|
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Admite [SccAddFromScc](../extensibility/sccaddfromscc-function.md) y el comando.|
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Admite un Comentario en la desprotección.|
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Admite un Comentario en el registro.|
|`SCC_CAP_COMMENTADD`|0x00002000L|Admite un Comentario en Add.|
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Admite un Comentario en Remove.|
|`SCC_CAP_TEXTOUT`|0x00008000L|Escribe texto en una función de salida proporcionada por el IDE.|
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Admite el almacenamiento de archivos sin diferencias.|
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Admite varios historiales de archivos.|
|`SCC_CAP_IGNORECASE`|0x00800000L|Admite la comparación de archivos que no distinguen mayúsculas de minúsculas.|
|`SCC_CAP_IGNORESPACE`|0x01000000L|Admite la comparación de archivos que omite los espacios en blanco.|
|`SCC_CAP_POPULATELIST`|0x02000000L|Admite la búsqueda de archivos adicionales.|
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Admite comentarios en Create Project.|
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Admite diff en todos los Estados si está bajo control.|
|`SCC_CAP_GET_NOUI`|0x20000000L|El complemento no admite una interfaz de usuario para get, pero el IDE puede seguir llamando a [SccGet](../extensibility/sccget-function.md).|
|`SCC_CAP_REENTRANT`|0x40000000L|El complemento es reentrante y seguro para subprocesos. En la versión 1,0, no se supone que ningún complemento es reentrante y seguro para subprocesos. Si un complemento 1,1 establece este bit, el host puede abrir varios proyectos en paralelo.|

## <a name="capability-bits-added-in-version-12"></a>Bits de funcionalidad agregados en la versión 1,2

|Código de funcionalidad|Value|Descripción|
|---------------------|-----------|-----------------|
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Admite [SccCreateSubProject](../extensibility/scccreatesubproject-function.md).|
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Admite [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).|
|`SCC_CAP_BATCH`|0x00040000L|Admite [SccBeginBatch](../extensibility/sccbeginbatch-function.md) y [SccEndBatch](../extensibility/sccendbatch-function.md).|
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Admite [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md).|
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Admite [SccDirDiff](../extensibility/sccdirdiff-function.md).|
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Admite varias desprotecciones en un archivo y [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md).|
|`SCC_CAP_SCCFILE`|0x80000000L|Admite el archivo *MSSCCPRJ. SCC* (sujeto a invalidación de usuario/administrador) y [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md).|

## <a name="capability-bits-added-in-version-13"></a>Bits de funcionalidad agregados en la versión 1,3
 Estas marcas se pasan de una en una a la función [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) para determinar si se admite la funcionalidad.

|Código de funcionalidad extendida|Value|Descripción|
|------------------------------|-----------|-----------------|
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Admite la `SCC_CHECKOUT_LOCALVER` opción para las desprotecciones.|
|`SCC_EXCAP_BACKGROUND_GET`|2|Admite [SccBackgroundGet](../extensibility/sccbackgroundget-function.md).|
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Admite [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md).|
|`SCC_EXCAP_POPULATELIST_DIR`|4|Admite la búsqueda de directorios adicionales.|
|`SCC_EXCAP_QUERYCHANGES`|5|Permite enumerar los cambios de archivo.|
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Admite [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md).|
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Admite [SccGetUserOption](../extensibility/sccgetuseroption-function.md).|
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Admite la llamada a SccQueryInfo en varios subprocesos.|
|`SCC_EXCAP_REMOVE_DIR`|9|Admite la función SccRemoveDir.|
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Puede eliminar archivos desprotegidos.|
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Puede cambiar el nombre de los archivos desprotegidos.|

## <a name="see-also"></a>Consulte también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
