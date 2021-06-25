---
title: Códigos de error | Microsoft Docs
description: Este artículo contiene una lista de códigos de error, valores y descripciones para las funciones de la API del complemento de control de código fuente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eedc9311bcafdd4241e065b40079abed3977dcef
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898310"
---
# <a name="error-codes"></a>Códigos de error
Cuando una función de la API del complemento de control de código fuente devuelve un error, se espera que sea uno de los siguientes códigos de error. Todos los errores son negativos, las advertencias o los códigos de error informativos son positivos y el correcto es 0.

|Código de error|Valor|Descripción|
|----------------|-----------|-----------------|
|`SCC_I_SHARESUBPROJOK`|7|El complemento admite la adición de archivos desde el control de código fuente en dos pasos. Para obtener más información, [vea SccSetOption](../extensibility/sccsetoption-function.md).|
|`SCC_I_FILEDIFFERS`|6|El archivo local es diferente del archivo de la base de datos de control de código fuente (por ejemplo, [SccDiff](../extensibility/sccdiff-function.md) puede devolver este valor).|
|`SCC_I_RELOADFILE`|5|El archivo local se cambió durante la operación de control de código fuente; El IDE debe volver a cargar el archivo si es posible.|
|`SCC_I_FILENOTAFFECTED`|4|El archivo no se ve afectado.|
|`SCC_I_PROJECTCREATED`|3|El proyecto se creó durante la operación de control de código fuente (por ejemplo, durante una llamada a [SccOpenProject](../extensibility/sccopenproject-function.md) cuando `SCC_OP_CREATEIFNEW` se especifica la marca ).|
|`SCC_I_OPERATIONCANCELED`|2|La operación se canceló.|
|`SCC_I_ADV_SUPPORT`|1|El complemento admite opciones avanzadas para el comando especificado. Para obtener más información, [vea SccGetCommandOptions.](../extensibility/sccgetcommandoptions-function.md)|
|`SCC_OK`|0|Correcto.|
|`SCC_E_INITIALIZEFAILED`|-1|Error: error de inicialización.|
|`SCC_E_UNKNOWNPROJECT`|-2|Error: el proyecto es desconocido.|
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Error: no se pudo crear el proyecto.|
|`SCC_E_NOTCHECKEDOUT`|-4|Error: el archivo no está desprotegiendo.|
|`SCC_E_ALREADYCHECKEDOUT`|-5|Error: el archivo ya está desprotegiendo.|
|`SCC_E_FILEISLOCKED`|-6|Error: el archivo está bloqueado.|
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Error: el archivo se desprotegía exclusivamente.|
|`SCC_E_ACCESSFAILURE`|-8|Hubo un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|`SCC_E_CHECKINCONFLICT`|-9|Error: se produjo un conflicto durante la comprobación.|
|`SCC_E_FILEALREADYEXISTS`|-10|Error: el archivo ya existe.|
|`SCC_E_FILENOTCONTROLLED`|-11|Error: el archivo no está bajo control de código fuente.|
|`SCC_E_FILEISCHECKEDOUT`|-12|Error: el archivo está desprotegiendo.|
|`SCC_E_NOSPECIFIEDVERSION`|-13|Error: no hay ninguna versión especificada.|
|`SCC_E_OPNOTSUPPORTED`|-14|Error: no se admite la operación.|
|`SCC_E_NONSPECIFICERROR`|-15|Error no específico.|
|`SCC_E_OPNOTPERFORMED`|-16|Error, la operación no se realizó.|
|`SCC_E_TYPENOTSUPPORTED`|-17|Error: el tipo del archivo, por ejemplo, binario, no es compatible con el sistema de control de código fuente.|
|`SCC_E_VERIFYMERGE`|-18|El archivo se ha combinado automáticamente, pero no se ha comprobado porque está pendiente de comprobación del usuario.|
|`SCC_E_FIXMERGE`|-19|El archivo se ha combinado automáticamente, pero no se ha registrado debido a un conflicto de combinación que se debe resolver manualmente.|
|`SCC_E_SHELLFAILURE`|-20|Error debido a un error del shell.|
|`SCC_E_INVALIDUSER`|-21|Error: el usuario no es válido.|
|`SCC_E_PROJECTALREADYOPEN`|-22|Error: el proyecto ya está abierto.|
|`SCC_E_PROJSYNTAXERR`|-23|Error de sintaxis del proyecto.|
|`SCC_E_INVALIDFILEPATH`|-24|Error: la ruta de acceso del archivo no es válida.|
|`SCC_E_PROJNOTOPEN`|-25|Error: el proyecto no está abierto.|
|`SCC_E_NOTAUTHORIZED`|-26|Error: el usuario no está autorizado para realizar esta operación.|
|`SCC_E_FILESYNTAXERR`|-27|Error de sintaxis de archivo.|
|`SCC_E_FILENOTEXIST`|-28|Error, el archivo local no existe.|
|`SCC_E_CONNECTIONFAILURE`|-29|Error: se produjo un error de conexión.|
|`SCC_E_UNKNOWNERROR`|-30|Error desconocido.|
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|La operación de obtener en segundo plano está actualmente en curso.|

## <a name="macros-provided-for-quick-checking"></a>Macros proporcionadas para la comprobación rápida

```cpp
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)
```

## <a name="remarks"></a>Observaciones
 Se espera que todas las funciones de la API del complemento de control de código fuente (excepto [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md)y [SccDiff)](../extensibility/sccdiff-function.md)se realicen correctamente cuando los archivos locales que se pasan como argumentos no existen en la carpeta de trabajo. Por ejemplo, el IDE puede emitir una llamada a [SccCheckout](../extensibility/scccheckout-function.md) o [SccUncheckout](../extensibility/sccuncheckout-function.md) en un archivo que no existe en la carpeta de trabajo, pero que existe en el sistema de control de código fuente. Esta llamada se realiza correctamente. Solo cuando no hay ningún archivo en la carpeta de trabajo o en el sistema de control de código fuente, se espera que se producirá un error en la función.

 Determinadas funciones, como y , deben devolver específicamente cuando el archivo de la carpeta de trabajo `SccAdd` `SccCheckin` no `SCC_E_FILENOTEXIST` existe. Se espera que otras funciones se tengan éxito cuando el archivo de trabajo no exista, si las funciones funcionan con un nombre de archivo válido en el sistema de control de código fuente.

 El complemento de control de código fuente no debe realizar suposiciones con respecto a los privilegios en un archivo de la carpeta de trabajo, incluso si el complemento había marcado el archivo como de solo lectura durante alguna operación. Un archivo de la carpeta de trabajo se puede mover, eliminar y cambiar fuera del control del complemento.

## <a name="see-also"></a>Consulta también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
