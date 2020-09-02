---
title: Marcadores usado por comandos específicos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffa1fd8bf025d665977e87dc8b88da724ade5a8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80740012"
---
# <a name="bitflags-used-by-specific-commands"></a>Marcadores usado por comandos específicos
El comportamiento de una serie de funciones de la API del complemento de control de código fuente se puede modificar estableciendo uno o varios bits en un solo valor. Estos valores se conocen como marcadores. Los distintos marcadores que usa la API del complemento de control de código fuente se detallan aquí, agrupados por la función que los utiliza.

## <a name="checked-out-flag"></a>Marca de desprotección
 Esta marca se puede establecer para [SccAdd](../extensibility/sccadd-function.md) o [SccCheckin](../extensibility/scccheckin-function.md).

|Marca|Value|Descripción|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|Mantenga el archivo desprotegido.|

## <a name="add-flags"></a>Agregar marcas
 Estas marcas las usa [SccAdd](../extensibility/sccadd-function.md).

|Marca|Value|Descripción|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|Se espera que el complemento de control de código fuente detecte automáticamente si el archivo es de texto o binario.|
|`SCC_FILETYPE_TEXT`|0x01|El tipo de archivo es texto.|
|`SCC_FILETYPE_BINARY`|0x04|El tipo de archivo es binario. **Nota:** `SCC_FILETYPE_TEXT` las `SCC_FILETYPE_BINARY` marcas y se excluyen mutuamente.   Establezca exactamente uno o ninguno.|
|`SCC_ADD_STORELATEST`|0x02|Almacenar solo la versión más reciente (sin diferencias).|

## <a name="diff-flags"></a>Marcas de diferencia
 [SccDiff](../extensibility/sccdiff-function.md) usa estas marcas para definir el ámbito de una operación de comparación. Las `SCC_DIFF_QD_xxx` marcas son mutuamente excluyentes. Si se especifica cualquiera de ellos, no se proporcionará ningún comentario visual. En una "diferencia rápida" (PC), el complemento no determina cómo es diferente el archivo, solo si es diferente. Si no se especifica ninguna de estas marcas, se realiza una "diferencia visual"; se calculan y se muestran las diferencias de archivo detalladas. Si no se admite el PC solicitado, el complemento se mueve al siguiente mejor. Por ejemplo, si el IDE solicita una suma de comprobación y el complemento no la admite, el complemento realiza una comprobación de contenido completo (aún mucho más rápido que una presentación visual).

|Marca|Value|Descripción|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|Omitir diferencias entre mayúsculas y minúsculas.|
|`SCC_DIFF_IGNORESPACE`|0x0004|Omitir las diferencias de espacio en blanco. **Nota:**  Las `SCC_DIFF_IGNORECASE` `SCC_DIFF_IGNORESPACE` marcas y son opcionales marcadores.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|PC comparando todo el contenido del archivo.|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|PC por suma de comprobación.|
|`SCC_DIFF_QD_TIME`|0x0040|PC por marca de fecha y hora de archivo.|
|`SCC_DIFF_QUICK_DIFF`|0x0070|Se trata de una máscara que se usa para comprobar todos los marcadores de PC. No se debe pasar a una función; los tres PC marcadores se excluyen mutuamente. PC siempre significa que no se muestra ninguna interfaz de usuario.|

## <a name="populatelist-flag"></a>Marca PopulateList
 [SccPopulateList](../extensibility/sccpopulatelist-function.md) usa esta marca en el `fOptions` parámetro.

|Marca|Value|Descripción|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|El IDE está pasando directorios, no archivos.|

## <a name="populatedirlist-flags"></a>Marcas de PopulateDirList
 Estas marcas las usa [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) en el `fOptions` parámetro.

|Valor de la opción|Value|Descripción|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|Examine solo un nivel de directorios para directorios (este es el valor predeterminado).|
|SCC_PDL_RECURSIVE|0x0001|Examinar de forma recursiva todos los directorios de cada directorio dado.|
|SCC_PDL_INCLUDEFILES|0x0002|Incluir nombres de archivo en el proceso de examen.|

## <a name="openproject-flags"></a>Marcas de OpenProject
 Estas marcas las usa [SccOpenProject](../extensibility/sccopenproject-function.md) en el `dwFlags` parámetro.

|Valor de la opción|Value|Descripción|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|Si el proyecto no existe en el control de código fuente, créelo. Si no se establece esta marca, pida al usuario que cree el proyecto (a menos que `SCC_OP_SILENTOPEN` se especifique la marca).|
|SCC_OP_SILENTOPEN|0x00000002L|No preguntar al usuario para crear un proyecto; simplemente devuelva `SCC_E_UNKNOWNPROJECT` .|

## <a name="get-flags"></a>Obtener marcas
 Los [SccGet](../extensibility/sccget-function.md) y [SccCheckout](../extensibility/scccheckout-function.md)usan estas marcas.

|Marca|Value|Descripción|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|El IDE está pasando directorios, no archivos: obtener todos los archivos de estos directorios.|
|`SCC_GET_RECURSIVE`|0x00000002L|El IDE está pasando directorios: Obtenga estos directorios y todos sus subdirectorios.|

## <a name="noption-values"></a>valores de nOption
 Estas marcas las usa [SccSetOption](../extensibility/sccsetoption-function.md) en el `nOption` parámetro.

|Marca|Value|Descripción|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Establezca el estado de la cola de eventos.|
|`SCC_OPT_USERDATA`|0x00000002L|Especifique los datos de usuario para `SCC_OPT_NAMECHANGEPFN` .|
|`SCC_OPT_HASCANCELMODE`|0x00000003L|El IDE puede controlar la cancelación.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Establecer una devolución de llamada para los cambios de nombre.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Deshabilite la desprotección de la interfaz de usuario del complemento de control de código fuente y no establezca el directorio de trabajo.|
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Agregue desde el sistema de control de código fuente para especificar un directorio de trabajo. Intente compartir en el proyecto asociado si es un descendiente directo.|

## <a name="dwval-bitflags"></a>dwVal marcadores
 Estas marcas las usa [SccSetOption](../extensibility/sccsetoption-function.md) en el `dwVal` parámetro.

|Marca|Value|Descripción|Utilizado por `nOption` valor|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00L|Suspende la actividad de la cola de eventos.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|Habilita el registro de la cola de eventos.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|Predeterminada No tiene ningún modo de cancelación; el complemento debe proporcionar si se desea.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1 L|El IDE controla la cancelación.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|Predeterminada Aceptar para desproteger de la interfaz de usuario del complemento; el directorio de trabajo está establecido.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1 L|No hay ninguna desprotección de la interfaz de usuario del complemento, ningún directorio de trabajo.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
