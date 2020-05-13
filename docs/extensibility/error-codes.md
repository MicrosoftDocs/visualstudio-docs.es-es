---
title: Códigos de error ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34072f6ddbd632f83dd308c6cb63427e02bb110b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711840"
---
# <a name="error-codes"></a>Códigos de error
Cuando una función de API de complemento de Control de código fuente devuelve un error, se espera que sea uno de los siguientes códigos de error. Todos los errores son negativos, las advertencias o los códigos de error informativos son positivos y el éxito es 0.

|Código de error|Value|Descripción|
|----------------|-----------|-----------------|
|`SCC_I_SHARESUBPROJOK`|7|El complemento admite la adición de archivos desde el control de código fuente en dos pasos. Para obtener más información, vea [SccSetOption](../extensibility/sccsetoption-function.md).|
|`SCC_I_FILEDIFFERS`|6|El archivo local es diferente del archivo de la base de datos de control de código fuente (por ejemplo, [SccDiff](../extensibility/sccdiff-function.md) puede devolver este valor).|
|`SCC_I_RELOADFILE`|5|El archivo local se cambió durante la operación de control de código fuente; el IDE debe volver a cargar el archivo si es posible.|
|`SCC_I_FILENOTAFFECTED`|4|El archivo no se ve afectado.|
|`SCC_I_PROJECTCREATED`|3|El proyecto se creó durante la operación de control de `SCC_OP_CREATEIFNEW` código fuente (por ejemplo, durante una llamada a [SccOpenProject](../extensibility/sccopenproject-function.md) cuando se especifica flag).|
|`SCC_I_OPERATIONCANCELED`|2|La operación se canceló.|
|`SCC_I_ADV_SUPPORT`|1|El complemento admite opciones avanzadas para el comando especificado. Para obtener más información, vea [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|
|`SCC_OK`|0|Correcto.|
|`SCC_E_INITIALIZEFAILED`|-1|Error: error de inicialización.|
|`SCC_E_UNKNOWNPROJECT`|-2|Error: proyecto es desconocido.|
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Error: no se pudo crear el proyecto.|
|`SCC_E_NOTCHECKEDOUT`|-4|Error: el archivo no está desprotegido.|
|`SCC_E_ALREADYCHECKEDOUT`|-5|Error: el archivo ya está desprotegido.|
|`SCC_E_FILEISLOCKED`|-6|Error: el archivo está bloqueado.|
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Error: el archivo está desprotegido exclusivamente.|
|`SCC_E_ACCESSFAILURE`|-8|Se ha producido un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|`SCC_E_CHECKINCONFLICT`|-9|Error: hubo un conflicto durante el check-in.|
|`SCC_E_FILEALREADYEXISTS`|-10|Error: el archivo ya existe.|
|`SCC_E_FILENOTCONTROLLED`|-11|Error: el archivo no está bajo control de código fuente.|
|`SCC_E_FILEISCHECKEDOUT`|-12|Error: el archivo está desprotegido.|
|`SCC_E_NOSPECIFIEDVERSION`|-13|Error: no hay ninguna versión especificada.|
|`SCC_E_OPNOTSUPPORTED`|-14|Error: la operación no es compatible.|
|`SCC_E_NONSPECIFICERROR`|-15|Error inespecífico.|
|`SCC_E_OPNOTPERFORMED`|-16|Error, la operación no se realizó.|
|`SCC_E_TYPENOTSUPPORTED`|-17|Error: el tipo del archivo, por ejemplo, binario, no es compatible con el sistema de control de código fuente.|
|`SCC_E_VERIFYMERGE`|-18|El archivo se ha fusionado automáticamente, pero no se ha comprobado porque está pendiente de verificación del usuario.|
|`SCC_E_FIXMERGE`|-19|El archivo se ha fusionado automáticamente, pero no se ha registrado debido a un conflicto de combinación que debe resolverse manualmente.|
|`SCC_E_SHELLFAILURE`|-20|Error debido a un error de shell.|
|`SCC_E_INVALIDUSER`|-21|Error: el usuario no es válido.|
|`SCC_E_PROJECTALREADYOPEN`|-22|Error: el proyecto ya está abierto.|
|`SCC_E_PROJSYNTAXERR`|-23|Error de sintaxis del proyecto.|
|`SCC_E_INVALIDFILEPATH`|-24|Error: la ruta del archivo no es válida.|
|`SCC_E_PROJNOTOPEN`|-25|Error: el proyecto no está abierto.|
|`SCC_E_NOTAUTHORIZED`|-26|Error: el usuario no está autorizado para realizar esta operación.|
|`SCC_E_FILESYNTAXERR`|-27|Error de sintaxis de archivo.|
|`SCC_E_FILENOTEXIST`|-28|Error, el archivo local no existe.|
|`SCC_E_CONNECTIONFAILURE`|-29|Error: se ha producido un error de conexión.|
|`SCC_E_UNKNOWNERROR`|-30|Error desconocido.|
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|La operación de obtención en segundo plano está actualmente en curso.|

## <a name="macros-provided-for-quick-checking"></a>Macros proporcionadas para la comprobación rápida

```cpp
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)
```

## <a name="remarks"></a>Observaciones
 Se espera que todas las funciones de API de complemento de Control de código fuente (excepto [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md)y [SccDiff)](../extensibility/sccdiff-function.md)se realicen correctamente cuando los archivos locales que se pasan como argumentos no existan en la carpeta de trabajo. Por ejemplo, el IDE puede emitir una llamada a [SccCheckout](../extensibility/scccheckout-function.md) o [SccUncheckout](../extensibility/sccuncheckout-function.md) en un archivo que no existe en la carpeta de trabajo, pero que existe en el sistema de control de código fuente. Esta llamada tendría éxito. Solo cuando no hay ningún archivo en la carpeta de trabajo o en el sistema de control de código fuente se espera que la función falle.

 Ciertas funciones, como `SccAdd` y `SccCheckin` `SCC_E_FILENOTEXIST` , deben devolverse específicamente cuando el archivo de la carpeta de trabajo no existe. Se espera que otras funciones se realicen correctamente cuando el archivo de trabajo no existe, si las funciones funcionan con un nombre de archivo válido en el sistema de control de código fuente.

 El complemento de control de código fuente no debe realizar ninguna suposición con respecto a los privilegios de un archivo en la carpeta de trabajo, incluso si el complemento había marcado el archivo de solo lectura durante alguna operación. Un archivo de la carpeta de trabajo se puede mover, eliminar y cambiar fuera del control del complemento.

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
