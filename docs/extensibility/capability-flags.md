---
title: Banderas de la capacidad ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9660cbe5a18e82974858fa4d923a38fc73e773f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739872"
---
# <a name="capability-flags"></a>Banderas de capacidad
Las SCC_CAP_ marcas*xxx* son indicadores de bits que se utilizan para indicar las capacidades de un complemento de control de código fuente. Los SCC_EXCAP_ los indicadores*xxx* son indicadores incrementales que indican capacidades extendidas y se resuelven en valores enteros.

|Código de capacidad|Value|Descripción|
|---------------------|-----------|-----------------|
|`SCC_CAP_REMOVE`|0x00000001L|Admite el [comando SccRemove](../extensibility/sccremove-function.md) y.|
|`SCC_CAP_RENAME`|0x00000002L|Admite [el comando SccRename](../extensibility/sccrename-function.md) y el comando.|
|`SCC_CAP_DIFF`|0x00000004L|Admite [el comando SccDiff](../extensibility/sccdiff-function.md) y.|
|`SCC_CAP_HISTORY`|0x00000008L|Admite [sccHistory](../extensibility/scchistory-function.md) y el comando.|
|`SCC_CAP_PROPERTIES`|0x00000010L|Admite [SccProperties](../extensibility/sccproperties-function.md) y el comando.|
|`SCC_CAP_RUNSCC`|0x00000020L|Admite [el comando SccRunScc](../extensibility/sccrunscc-function.md) y.|
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Admite el [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) y el comando.|
|`SCC_CAP_QUERYINFO`|0x00000080L|Admite [el SccQueryInfo](../extensibility/sccqueryinfo-function.md) y el comando.|
|`SCC_CAP_GETEVENTS`|0x00000100L|Admite [SccGetEvents](../extensibility/sccgetevents-function.md) y el comando.|
|`SCC_CAP_GETPROJPATH`|0x00000200L|Admite [SccGetProjPath](../extensibility/sccgetprojpath-function.md) y el comando.|
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Admite el [comando SccAddFromScc](../extensibility/sccaddfromscc-function.md) y.|
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Admite un comentario sobre el pago.|
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Admite un comentario sobre el check-in.|
|`SCC_CAP_COMMENTADD`|0x00002000L|Admite un comentario en Agregar.|
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Admite un comentario en Eliminar.|
|`SCC_CAP_TEXTOUT`|0x00008000L|Escribe texto en una función de salida proporcionada por IDE.|
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Admite el almacenamiento de archivos sin deltas.|
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Admite el historial de varios archivos.|
|`SCC_CAP_IGNORECASE`|0x00800000L|Admite la comparación de archivos que no distinguen mayúsculas de minúsculas.|
|`SCC_CAP_IGNORESPACE`|0x01000000L|Admite la comparación de archivos que omite el espacio en blanco.|
|`SCC_CAP_POPULATELIST`|0x02000000L|Admite la búsqueda de archivos adicionales.|
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Admite comentarios sobre la creación de proyectos.|
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Admite diferencias en todos los estados si están bajo control.|
|`SCC_CAP_GET_NOUI`|0x200000000L|El complemento no admite una interfaz de usuario para Get, pero el IDE puede llamar a [SccGet](../extensibility/sccget-function.md).|
|`SCC_CAP_REENTRANT`|0x40000000L|El plug-in es reentrante y seguro para subprocesos. En la versión 1.0, no se suponía que los complementos fueran reentrantes y seguros para subprocesos. Si un complemento 1.1 establece este bit, el host puede abrir varios proyectos en paralelo.|

## <a name="capability-bits-added-in-version-12"></a>Bits de capacidad añadidos en la versión 1.2

|Código de capacidad|Value|Descripción|
|---------------------|-----------|-----------------|
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Admite [SccCreateSubProject](../extensibility/scccreatesubproject-function.md).|
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Admite [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).|
|`SCC_CAP_BATCH`|0x00040000L|Admite [SccBeginBatch](../extensibility/sccbeginbatch-function.md) y [SccEndBatch](../extensibility/sccendbatch-function.md).|
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Admite [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md).|
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Soporta el [SccDirDiff](../extensibility/sccdirdiff-function.md).|
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Admite varias desprotecciones en un archivo y [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md).|
|`SCC_CAP_SCCFILE`|0x800000000L|Admite el archivo *MSSCCPRJ.SCC* (sujeto a anulación de usuario/administrador) y [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md).|

## <a name="capability-bits-added-in-version-13"></a>Bits de capacidad añadidos en la versión 1.3
 Estos indicadores se pasan de uno en uno a la función [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) para determinar si se admite la funcionalidad.

|Código de capacidad ampliada|Value|Descripción|
|------------------------------|-----------|-----------------|
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Admite `SCC_CHECKOUT_LOCALVER` la opción de desprotecciones.|
|`SCC_EXCAP_BACKGROUND_GET`|2|Admite [SccBackgroundGet](../extensibility/sccbackgroundget-function.md).|
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Admite [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md).|
|`SCC_EXCAP_POPULATELIST_DIR`|4|Admite la búsqueda de directorios adicionales.|
|`SCC_EXCAP_QUERYCHANGES`|5|Admite la enumeración de cambios de archivo.|
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Admite [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md).|
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Admite [SccGetUserOption](../extensibility/sccgetuseroption-function.md).|
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Admite la llamada a SccQueryInfo en varios subprocesos.|
|`SCC_EXCAP_REMOVE_DIR`|9|Admite la función SccRemoveDir.|
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Puede eliminar los archivos desprotegidos.|
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Puede cambiar el nombre de los archivos desprotegidos.|

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
