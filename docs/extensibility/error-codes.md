---
title: Códigos de error | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d9139ca59394c8d5de69ddf77f51bf57b8b7619
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931978"
---
# <a name="error-codes"></a>Códigos de error
Cuando una función de la API de complemento de Control de origen devuelve un error, se espera a ser uno de los siguientes códigos de error. Todos los errores son negativos, son positivos, advertencias o los códigos de error informativo y correcta es 0.  
  
|Código de error|Valor|Descripción|  
|----------------|-----------|-----------------|  
|`SCC_I_SHARESUBPROJOK`|7|Complemento admite la adición de archivos de control de código fuente en dos pasos. Para obtener más información, consulte [SccSetOption](../extensibility/sccsetoption-function.md).|  
|`SCC_I_FILEDIFFERS`|6|El archivo local es diferente del archivo en la base de datos de control de código fuente (por ejemplo, [SccDiff](../extensibility/sccdiff-function.md) pueden devolver este valor).|  
|`SCC_I_RELOADFILE`|5|Archivo local cambió durante la operación de control de código fuente; el IDE debe volver a cargar el archivo si es posible.|  
|`SCC_I_FILENOTAFFECTED`|4|El archivo no se ve afectado.|  
|`SCC_I_PROJECTCREATED`|3|El proyecto se creó durante la operación de control de código fuente (por ejemplo, durante una llamada a [SccOpenProject](../extensibility/sccopenproject-function.md) cuando `SCC_OP_CREATEIFNEW` indicador se especifica).|  
|`SCC_I_OPERATIONCANCELED`|2|Se canceló la operación.|  
|`SCC_I_ADV_SUPPORT`|1|Complemento admite las opciones avanzadas para el comando especificado. Para obtener más información, consulte [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|  
|`SCC_OK`|0|Correcto.|  
|`SCC_E_INITIALIZEFAILED`|-1|Error: error de inicialización.|  
|`SCC_E_UNKNOWNPROJECT`|-2|Error: el proyecto es desconocido.|  
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Error: no se pudo crear el proyecto.|  
|`SCC_E_NOTCHECKEDOUT`|-4|Error: el archivo no está desprotegido.|  
|`SCC_E_ALREADYCHECKEDOUT`|-5|Error: el archivo ya está desprotegido.|  
|`SCC_E_FILEISLOCKED`|-6|Error: el archivo está bloqueado.|  
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Error: el archivo está desprotegido exclusivamente.|  
|`SCC_E_ACCESSFAILURE`|-8|Hubo un problema al obtener acceso el sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|`SCC_E_CHECKINCONFLICT`|-9|Error: se produjo un conflicto durante la protección.|  
|`SCC_E_FILEALREADYEXISTS`|-10|Error: el archivo ya existe.|  
|`SCC_E_FILENOTCONTROLLED`|-11|Error: el archivo no está bajo control de código fuente.|  
|`SCC_E_FILEISCHECKEDOUT`|-12|Error: el archivo está desprotegido.|  
|`SCC_E_NOSPECIFIEDVERSION`|-13|Error: no hay ninguna versión especificada.|  
|`SCC_E_OPNOTSUPPORTED`|-14|Error: no se admite la operación.|  
|`SCC_E_NONSPECIFICERROR`|-15|Error no específico.|  
|`SCC_E_OPNOTPERFORMED`|-16|Error, la operación no se realizó.|  
|`SCC_E_TYPENOTSUPPORTED`|-17|Error: el tipo de archivo, por ejemplo, binario, no es compatible con el sistema de control de código fuente.|  
|`SCC_E_VERIFYMERGE`|-18|Archivo ha sido combinada automáticamente, pero no se ha protegido porque es comprobación de usuario pendientes.|  
|`SCC_E_FIXMERGE`|-19|Archivo ha sido combinada automática, pero no se ha comprobado debido a un conflicto de combinación que debe resolverse manualmente.|  
|`SCC_E_SHELLFAILURE`|-20|Error debido a un error de shell.|  
|`SCC_E_INVALIDUSER`|-21|Error: el usuario no es válido.|  
|`SCC_E_PROJECTALREADYOPEN`|-22|Error: el proyecto ya está abierto.|  
|`SCC_E_PROJSYNTAXERR`|-23|Error de sintaxis del proyecto.|  
|`SCC_E_INVALIDFILEPATH`|-24|Error: la ruta de acceso de archivo no es válido.|  
|`SCC_E_PROJNOTOPEN`|-25|Error: el proyecto no está abierto.|  
|`SCC_E_NOTAUTHORIZED`|-26|Error: el usuario no está autorizado para realizar esta operación.|  
|`SCC_E_FILESYNTAXERR`|-27|Error de sintaxis del archivo.|  
|`SCC_E_FILENOTEXIST`|-28|Error, no existe el archivo local.|  
|`SCC_E_CONNECTIONFAILURE`|-29|Error: se produjo un error de conexión.|  
|`SCC_E_UNKNOWNERROR`|-30|Error desconocido.|  
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|Operación get en segundo plano está en curso.|  
  
## <a name="macros-provided-for-quick-checking"></a>Macros que se proporcionan para la comprobación rápida  
  
```cpp  
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)  
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)  
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)  
```  
  
## <a name="remarks"></a>Comentarios  
 Todas las funciones de API de complemento de Control de código fuente (excepto la [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md), y [SccDiff](../extensibility/sccdiff-function.md)) se espera que se realice correctamente cuando los archivos locales que se pasan como argumentos no existe en la carpeta de trabajo. Por ejemplo, el IDE puede emitir una llamada a la [SccCheckout](../extensibility/scccheckout-function.md) o [SccUncheckout](../extensibility/sccuncheckout-function.md) en un archivo que no existe en la carpeta de trabajo, pero existe en el sistema de control de código fuente. Esta llamada se realizaría correctamente. Solo cuando no hay ningún archivo en la carpeta de trabajo o en el sistema de control de código fuente es la función espera un error.  
  
 Ciertas funciones, como `SccAdd` y `SccCheckin`, debe devolver específicamente `SCC_E_FILENOTEXIST` cuando no existe el archivo en la carpeta de trabajo. Otras funciones se esperan que tengan éxito cuando no existe el archivo de trabajo, si las funciones que operan en un nombre de archivo válido en el sistema de control de código fuente.  
  
 El complemento de control de origen debe hacer ninguna suposición sobre privilegios en un archivo en la carpeta de trabajo, incluso si el complemento tenía el archivo de sólo lectura durante alguna operación. Un archivo en la carpeta de trabajo se puede mover, eliminar y cambiado fuera de control del complemento.  
  
## <a name="see-also"></a>Vea también  
 [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)