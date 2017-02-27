---
title: "Marcadores de capacidad | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "indicadores de control de código fuente plug-ins, capacidad"
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# Marcadores de capacidad
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El SCC\_CAP\_*xxx* marcas son marcadores de bits que se utiliza para indicar las capacidades de un complemento de control de código fuente. El SCC\_EXCAP\_*xxx* marcas son incrementales marcas que indican las características extendidas y resolver en valores enteros.  
  
|Código de capacidad|Valor|Descripción|  
|-------------------------|-----------|-----------------|  
|`SCC_CAP_REMOVE`|0x00000001L|Admite la [SccRemove](../extensibility/sccremove-function.md) y comando.|  
|`SCC_CAP_RENAME`|0x00000002L|Admite la [SccRename](../extensibility/sccrename-function.md) y comando.|  
|`SCC_CAP_DIFF`|0x00000004L|Admite la [SccDiff](../extensibility/sccdiff-function.md) y comando.|  
|`SCC_CAP_HISTORY`|0x00000008L|Admite la [SccHistory](../extensibility/scchistory-function.md) y comando.|  
|`SCC_CAP_PROPERTIES`|0x00000010L|Admite la [SccProperties](../extensibility/sccproperties-function.md) y comando.|  
|`SCC_CAP_RUNSCC`|0x00000020L|Admite la [SccRunScc](../extensibility/sccrunscc-function.md) y comando.|  
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Admite la [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) y comando.|  
|`SCC_CAP_QUERYINFO`|0x00000080L|Admite la [SccQueryInfo](../extensibility/sccqueryinfo-function.md) y comando.|  
|`SCC_CAP_GETEVENTS`|0x00000100L|Admite la [SccGetEvents](../extensibility/sccgetevents-function.md) y comando.|  
|`SCC_CAP_GETPROJPATH`|0x00000200L|Admite la [SccGetProjPath](../extensibility/sccgetprojpath-function.md) y comando.|  
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Admite la [SccAddFromScc](../extensibility/sccaddfromscc-function.md) y comando.|  
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Admite un comentario en la caja.|  
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Admite un comentario de protección.|  
|`SCC_CAP_COMMENTADD`|0x00002000L|Admite un comentario en Agregar.|  
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Admite un comentario en quitar.|  
|`SCC_CAP_TEXTOUT`|0x00008000L|Escribe texto en una función de salida proporcionado por el IDE.|  
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Admite el almacenamiento de archivos sin deltas.|  
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Admite el historial de archivos varios.|  
|`SCC_CAP_IGNORECASE`|0x00800000L|Admite la comparación de archivos entre mayúsculas y minúsculas.|  
|`SCC_CAP_IGNORESPACE`|0x01000000L|Admite archivos de comparación que omite los espacios en blanco.|  
|`SCC_CAP_POPULATELIST`|0x02000000L|Admite la búsqueda de archivos adicionales.|  
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Admite comentarios en creación proyecto.|  
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Admite diferencias en todos los Estados si bajo control.|  
|`SCC_CAP_GET_NOUI`|0x20000000L|Complemento no admite una interfaz de usuario para Get, pero todavía puede llamar IDE [SccGet](../extensibility/sccget-function.md).|  
|`SCC_CAP_REENTRANT`|0x40000000L|Complemento es reentrante y segura para subprocesos. En la versión 1.0, no hay complementos se supone reentrante y segura para subprocesos. Si un complemento de 1.1 establece este bit, el host puede abrir varios proyectos en paralelo.|  
  
## Bits de capacidad agregados en la versión 1.2  
  
|Código de capacidad|Valor|Descripción|  
|-------------------------|-----------|-----------------|  
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Admite la [SccCreateSubProject](../extensibility/scccreatesubproject-function.md).|  
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Admite la [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).|  
|`SCC_CAP_BATCH`|0x00040000L|Admite la [SccBeginBatch](../extensibility/sccbeginbatch-function.md) y [SccEndBatch](../extensibility/sccendbatch-function.md).|  
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Admite la [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md).|  
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Admite la [SccDirDiff](../extensibility/sccdirdiff-function.md).|  
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Admite varias desprotecciones en un archivo y el [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md).|  
|`SCC_CAP_SCCFILE`|0x80000000L|Admite la MSSCCPRJ. Archivo de control de código fuente \(en función de reemplazo de usuario o administrador\) y la [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md).|  
  
## Bits de capacidad que se agregó en la versión 1.3  
 Estas marcas se pasan de uno en uno para el [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) para determinar si se admite la capacidad de función.  
  
|Código de la capacidad ampliada|Valor|Descripción|  
|-------------------------------------|-----------|-----------------|  
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Admite la `SCC_CHECKOUT_LOCALVER` opción desprotecciones.|  
|`SCC_EXCAP_BACKGROUND_GET`|2|Admite la [SccBackgroundGet](../extensibility/sccbackgroundget-function.md).|  
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Admite la [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md).|  
|`SCC_EXCAP_POPULATELIST_DIR`|4|Admite la búsqueda de directorios adicionales.|  
|`SCC_EXCAP_QUERYCHANGES`|5|Admite la enumeración de cambios de archivo.|  
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Admite la [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md).|  
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Admite la [SccGetUserOption](../extensibility/sccgetuseroption-function.md).|  
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Admite la llamada a SccQueryInfo en varios subprocesos.|  
|`SCC_EXCAP_REMOVE_DIR`|9|Es compatible con la función SccRemoveDir.|  
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Puede eliminar archivos desprotegidos.|  
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Puede cambiar el nombre de los archivos protegidos.|  
  
## Vea también  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)