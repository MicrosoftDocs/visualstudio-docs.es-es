---
title: "C&#243;digos de error | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "códigos de error, los complementos de control de código fuente"
  - "origen control plug-ins, códigos de error"
  - "errores [Visual Studio SDK]"
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# C&#243;digos de error
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando una función de la API de complementos de Control de código fuente, devuelve un error, se espera a ser uno de los siguientes códigos de error. Todos los errores son negativos, códigos de error informativos o advertencias son positivos, y éxito es 0.  
  
|Código de error|Valor|Descripción|  
|---------------------|-----------|-----------------|  
|`SCC_I_SHARESUBPROJOK`|7|Complemento admite la adición de archivos desde el control de código fuente en dos pasos. Para obtener más información, consulta [SccSetOption](../extensibility/sccsetoption-function.md).|  
|`SCC_I_FILEDIFFERS`|6|El archivo local es diferente del archivo en la base de datos de control de código fuente \(por ejemplo, [SccDiff](../extensibility/sccdiff-function.md) puede devolver este valor\).|  
|`SCC_I_RELOADFILE`|5|Archivo local se cambió durante la operación de control de código fuente; el IDE debe recargar el archivo si es posible.|  
|`SCC_I_FILENOTAFFECTED`|4|El archivo no se ve afectado.|  
|`SCC_I_PROJECTCREATED`|3|El proyecto se creó durante la operación de control de código fuente \(por ejemplo, durante una llamada a [SccOpenProject](../extensibility/sccopenproject-function.md) cuando `SCC_OP_CREATEIFNEW` se especifica la marca\).|  
|`SCC_I_OPERATIONCANCELED`|2|Se canceló la operación.|  
|`SCC_I_ADV_SUPPORT`|1|Complemento admite opciones avanzadas para el comando especificado. Para obtener más información, consulta [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|  
|`SCC_OK`|0|Correcto.|  
|`SCC_E_INITIALIZEFAILED`|\-1|Error: error de inicialización.|  
|`SCC_E_UNKNOWNPROJECT`|\-2|Error: el proyecto es desconocido.|  
|`SCC_E_COULDNOTCREATEPROJECT`|\-3|Error: no se pudo crear el proyecto.|  
|`SCC_E_NOTCHECKEDOUT`|\-4|Error: el archivo no está desprotegido.|  
|`SCC_E_ALREADYCHECKEDOUT`|\-5|Error: el archivo ya está desprotegido.|  
|`SCC_E_FILEISLOCKED`|\-6|Error: el archivo está bloqueado.|  
|`SCC_E_FILEOUTEXCLUSIVE`|\-7|Error: el archivo se desprotege exclusivamente.|  
|`SCC_E_ACCESSFAILURE`|\-8|Hubo un problema al obtener acceso al sistema de control de origen, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|`SCC_E_CHECKINCONFLICT`|\-9|Error: se produjo un conflicto durante la protección.|  
|`SCC_E_FILEALREADYEXISTS`|\-10|Error: el archivo ya existe.|  
|`SCC_E_FILENOTCONTROLLED`|\-11|Error: el archivo no está bajo control de código fuente.|  
|`SCC_E_FILEISCHECKEDOUT`|\-12|Error: el archivo está desprotegido.|  
|`SCC_E_NOSPECIFIEDVERSION`|\-13|Error: no hay ninguna versión especificada.|  
|`SCC_E_OPNOTSUPPORTED`|\-14|Error: no se admite la operación.|  
|`SCC_E_NONSPECIFICERROR`|\-15|Error no específico.|  
|`SCC_E_OPNOTPERFORMED`|\-16|Error, la operación no se realizó.|  
|`SCC_E_TYPENOTSUPPORTED`|\-17|Error: no se admite el tipo de archivo, por ejemplo, binario, por el sistema de control de código fuente.|  
|`SCC_E_VERIFYMERGE`|\-18|Archivo ha sido combinan automáticamente, pero no se ha protegido porque es la comprobación de usuario pendientes.|  
|`SCC_E_FIXMERGE`|\-19|Archivo ha sido combinan automáticamente, pero no se han protegido debido a un conflicto de combinación que debe resolverse manualmente.|  
|`SCC_E_SHELLFAILURE`|\-20|Error debido a un error de shell.|  
|`SCC_E_INVALIDUSER`|\-21|Error: el usuario no es válido.|  
|`SCC_E_PROJECTALREADYOPEN`|\-22|Error: el proyecto ya está abierto.|  
|`SCC_E_PROJSYNTAXERR`|\-23|Error de sintaxis del proyecto.|  
|`SCC_E_INVALIDFILEPATH`|\-24|Error: la ruta de acceso de archivo no es válido.|  
|`SCC_E_PROJNOTOPEN`|\-25|Error: el proyecto no está abierto.|  
|`SCC_E_NOTAUTHORIZED`|\-26|Error: el usuario no está autorizado para realizar esta operación.|  
|`SCC_E_FILESYNTAXERR`|\-27|Error de sintaxis del archivo.|  
|`SCC_E_FILENOTEXIST`|\-28|Error, no existe el archivo local.|  
|`SCC_E_CONNECTIONFAILURE`|\-29|Error: se produjo un error de conexión.|  
|`SCC_E_UNKNOWNERROR`|\-30|Error desconocido.|  
|`SCC_E_BACKGROUNDGETINPROGRESS`|\-31|Operación get en segundo plano está en curso.|  
  
## Macros que se proporcionan para la comprobación rápida  
  
```cpp#  
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE) IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE) IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)  
```  
  
## Comentarios  
 Todas las funciones de API de complementos de Control de código fuente \(excepto la [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md), y [SccDiff](../extensibility/sccdiff-function.md)\) se espera que tengan éxito cuando no existen los archivos locales que se pasan como argumentos en la carpeta de trabajo. Por ejemplo, el IDE puede emitir una llamada a la [SccCheckout](../extensibility/scccheckout-function.md) o [SccUncheckout](../extensibility/sccuncheckout-function.md) en un archivo que no existe en la carpeta de trabajo, pero existe en el sistema de control de código fuente. Esta llamada se realizará correctamente. Sólo cuando no hay ningún archivo en la carpeta de trabajo o en el sistema de control de código fuente se la función espera un error.  
  
 Ciertas funciones, como `SccAdd` y `SccCheckin`, debería devolver específicamente `SCC_E_FILENOTEXIST` cuando no existe el archivo en la carpeta de trabajo. Se espera que otras funciones correctamente cuando no existe el archivo de trabajo, si las funciones operan en un nombre de archivo válido en el sistema de control de código fuente.  
  
 El complemento de control de código fuente debe hacer ninguna suposición sobre privilegios en un archivo en la carpeta de trabajo, incluso si el complemento tenía el archivo de sólo lectura durante alguna operación. Un archivo en la carpeta de trabajo se puede mover, eliminar y modificado fuera de control del complemento.  
  
## Vea también  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)