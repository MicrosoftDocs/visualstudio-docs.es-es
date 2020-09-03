---
title: Códigos de error | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fef596fdfa9bb29fac38c72890392c33a86b31d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204557"
---
# <a name="error-codes"></a>Códigos de error
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando una función de la API del complemento de control de código fuente devuelve un error, se espera que sea uno de los siguientes códigos de error. Todos los errores son negativos, las advertencias o los códigos de error informativos son positivos y el éxito es 0.  
  
|Código de error|Value|Descripción|  
|----------------|-----------|-----------------|  
|`SCC_I_SHARESUBPROJOK`|7|El complemento admite la adición de archivos del control de código fuente en dos pasos. Para obtener más información, vea [SccSetOption](../extensibility/sccsetoption-function.md).|  
|`SCC_I_FILEDIFFERS`|6|El archivo local es diferente del archivo de la base de datos de control de código fuente (por ejemplo, [SccDiff](../extensibility/sccdiff-function.md) puede devolver este valor).|  
|`SCC_I_RELOADFILE`|5|El archivo local se modificó durante la operación de control de código fuente. el IDE debe volver a cargar el archivo si es posible.|  
|`SCC_I_FILENOTAFFECTED`|4|El archivo no se ve afectado.|  
|`SCC_I_PROJECTCREATED`|3|El proyecto se creó durante la operación de control de código fuente (por ejemplo, durante una llamada a [SccOpenProject](../extensibility/sccopenproject-function.md) cuando `SCC_OP_CREATEIFNEW` se especifica flag).|  
|`SCC_I_OPERATIONCANCELED`|2|La operación se canceló.|  
|`SCC_I_ADV_SUPPORT`|1|El complemento admite opciones avanzadas para el comando especificado. Para obtener más información, vea [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|  
|`SCC_OK`|0|Correcto.|  
|`SCC_E_INITIALIZEFAILED`|-1|Error: error de inicialización.|  
|`SCC_E_UNKNOWNPROJECT`|-2|Error: no se conoce el proyecto.|  
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Error: no se pudo crear el proyecto.|  
|`SCC_E_NOTCHECKEDOUT`|-4|Error: el archivo no está desprotegido.|  
|`SCC_E_ALREADYCHECKEDOUT`|-5|Error: el archivo ya está desprotegido.|  
|`SCC_E_FILEISLOCKED`|-6|Error: el archivo está bloqueado.|  
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Error: el archivo está desprotegido en exclusiva.|  
|`SCC_E_ACCESSFAILURE`|-8|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|`SCC_E_CHECKINCONFLICT`|-9|Error: se produjo un conflicto durante la inserción en el repositorio.|  
|`SCC_E_FILEALREADYEXISTS`|-10|Error: el archivo ya existe.|  
|`SCC_E_FILENOTCONTROLLED`|-11|Error: el archivo no está bajo control de código fuente.|  
|`SCC_E_FILEISCHECKEDOUT`|-12|Error: el archivo está desprotegido.|  
|`SCC_E_NOSPECIFIEDVERSION`|-13|Error: no hay ninguna versión especificada.|  
|`SCC_E_OPNOTSUPPORTED`|-14|Error: no se admite la operación.|  
|`SCC_E_NONSPECIFICERROR`|errores|Error no específico.|  
|`SCC_E_OPNOTPERFORMED`|-16|Error, la operación no se realizó.|  
|`SCC_E_TYPENOTSUPPORTED`|-17|Error: el tipo de archivo, por ejemplo, Binary, no es compatible con el sistema de control de código fuente.|  
|`SCC_E_VERIFYMERGE`|-18|El archivo se combinó automáticamente, pero no se ha comprobado porque está pendiente de comprobación del usuario.|  
|`SCC_E_FIXMERGE`|-19|El archivo se ha fusionado mediante combinación automática, pero no se ha protegido debido a un conflicto de fusión mediante combinación que se debe resolver manualmente.|  
|`SCC_E_SHELLFAILURE`|-20|Error debido a un error de Shell.|  
|`SCC_E_INVALIDUSER`|-21|Error: el usuario no es válido.|  
|`SCC_E_PROJECTALREADYOPEN`|-22|Error: el proyecto ya está abierto.|  
|`SCC_E_PROJSYNTAXERR`|-23|Error de sintaxis del proyecto.|  
|`SCC_E_INVALIDFILEPATH`|-24|Error: la ruta de acceso del archivo no es válida.|  
|`SCC_E_PROJNOTOPEN`|-25|Error: el proyecto no está abierto.|  
|`SCC_E_NOTAUTHORIZED`|-26|Error: el usuario no está autorizado para realizar esta operación.|  
|`SCC_E_FILESYNTAXERR`|-27|Error de sintaxis de archivo.|  
|`SCC_E_FILENOTEXIST`|-28|Error, el archivo local no existe.|  
|`SCC_E_CONNECTIONFAILURE`|-29|Error: error de conexión.|  
|`SCC_E_UNKNOWNERROR`|-30|Error desconocido.|  
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|La operación de obtención de fondo está actualmente en curso.|  
  
## <a name="macros-provided-for-quick-checking"></a>Macros proporcionadas para la comprobación rápida  
  
```cpp#  
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)  
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)  
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)  
```  
  
## <a name="remarks"></a>Comentarios  
 Se espera que todas las funciones de la API del complemento de control de código fuente (excepto [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md)y [SccDiff](../extensibility/sccdiff-function.md)) se realicen correctamente cuando los archivos locales que se pasan como argumentos no existen en la carpeta de trabajo. Por ejemplo, el IDE puede emitir una llamada a [SccCheckout](../extensibility/scccheckout-function.md) o [SccUncheckout](../extensibility/sccuncheckout-function.md) en un archivo que no existe en la carpeta de trabajo, pero existe en el sistema de control de código fuente. Esta llamada se realizará correctamente. Solo cuando no hay ningún archivo en la carpeta de trabajo o en el sistema de control de código fuente, la función espera que se produzca un error.  
  
 Ciertas funciones, como `SccAdd` y `SccCheckin` , deben devolver específicamente `SCC_E_FILENOTEXIST` cuando el archivo de la carpeta de trabajo no existe. Se espera que otras funciones se realicen correctamente cuando no existe el archivo de trabajo, si las funciones operan en un nombre de archivo válido en el sistema de control de código fuente.  
  
 El complemento de control de código fuente no debe hacer ninguna suposición con respecto a los privilegios en un archivo de la carpeta de trabajo, aunque el complemento hubiera marcado el archivo como de solo lectura durante alguna operación. Un archivo de la carpeta de trabajo puede moverse, eliminarse y cambiarse fuera del control del complemento.  
  
## <a name="see-also"></a>Consulte también  
 [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
