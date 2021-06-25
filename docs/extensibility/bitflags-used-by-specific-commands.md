---
title: Bitflags Used by Specific Commands | Microsoft Docs
description: Obtenga información sobre las bandas de bits que usa la API de complemento de control de código fuente, organizadas por la función que los usa.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: be5915d96b574336d7091239275a2aaef456a7f3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899372"
---
# <a name="bitflags-used-by-specific-commands"></a>Bitflags usados por comandos específicos
El comportamiento de varias funciones de la API del complemento de control de código fuente se puede modificar estableciendo uno o varios bits en un solo valor. Estos valores se conocen como "bitflags". Aquí se detallan los distintos puntos de bits usados por la API de complemento de control de código fuente, agrupados por la función que los usa.

## <a name="checked-out-flag"></a>Marca desprote que se ha comprobado
 Esta marca se puede establecer para [SccAdd](../extensibility/sccadd-function.md) o [SccCheckin.](../extensibility/scccheckin-function.md)

|Marca|Value|Descripción|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|Mantenga el archivo desprotegiendo.|

## <a name="add-flags"></a>Agregar marcas
 SccAdd usa estas [marcas.](../extensibility/sccadd-function.md)

|Marca|Value|Descripción|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|Se espera que el complemento de control de código fuente detecte automáticamente si el archivo es texto o binario.|
|`SCC_FILETYPE_TEXT`|0x01|El tipo de archivo es texto.|
|`SCC_FILETYPE_BINARY`|0x04|El tipo de archivo es binario. **Nota:** `SCC_FILETYPE_TEXT` Las `SCC_FILETYPE_BINARY` marcas y son mutuamente excluyentes.   Establezca exactamente uno o ninguno.|
|`SCC_ADD_STORELATEST`|0x02|Almacene solo la versión más reciente (sin diferencias).|

## <a name="diff-flags"></a>Marcas de diferencias
 [SccDiff usa](../extensibility/sccdiff-function.md) estas marcas para definir el ámbito de una operación de diferencias. Las `SCC_DIFF_QD_xxx` marcas son mutuamente excluyentes. Si se especifica alguna de ellas, no se va a proporcionar ningún comentario visual. En una "diferencia rápida" (QD), el complemento no determina cómo es diferente el archivo, solo si es diferente. Si no se especifica ninguna de estas marcas, se realiza una "diferencia visual"; Se calculan y se muestran las diferencias de archivo detalladas. Si no se admite el QD solicitado, el complemento pasa al siguiente mejor. Por ejemplo, si el IDE solicita una suma de comprobación y el complemento no la admite, el complemento realiza una comprobación de contenido completo (todavía mucho más rápido que una pantalla visual).

|Marca|Value|Descripción|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|Omitir las diferencias entre mayúsculas y minúsculas.|
|`SCC_DIFF_IGNORESPACE`|0x0004|Omitir las diferencias de espacio en blanco. **Nota:**  Las `SCC_DIFF_IGNORECASE` marcas y son marcas de bits `SCC_DIFF_IGNORESPACE` opcionales.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD mediante la comparación de todo el contenido del archivo.|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD por suma de comprobación.|
|`SCC_DIFF_QD_TIME`|0x0040|QD por marca de fecha y hora de archivo.|
|`SCC_DIFF_QUICK_DIFF`|0x0070|Se trata de una máscara que se usa para comprobar todas las marcas de bits de QD. No se debe pasar a una función; los tres puntos de bits de QD son mutuamente excluyentes. QD siempre significa que no se muestra la interfaz de usuario.|

## <a name="populatelist-flag"></a>Marca PopulateList
 [SccPopulateList](../extensibility/sccpopulatelist-function.md) usa esta marca en el `fOptions` parámetro .

|Marca|Value|Descripción|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|El IDE pasa directorios, no archivos.|

## <a name="populatedirlist-flags"></a>Marcas PopulateDirList
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) usa estas marcas en el `fOptions` parámetro .

|Valor de la opción|Valor|Descripción|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|Examine solo un nivel de directorios para los directorios (este es el valor predeterminado).|
|SCC_PDL_RECURSIVE|0x0001|Examine de forma recursiva todos los directorios de cada directorio determinado.|
|SCC_PDL_INCLUDEFILES|0x0002|Incluya nombres de archivo en el proceso de examen.|

## <a name="openproject-flags"></a>Marcas openproject
 [SccOpenProject](../extensibility/sccopenproject-function.md) usa estas marcas en el `dwFlags` parámetro .

|Valor de la opción|Valor|Descripción|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|Si el proyecto no existe en el control de código fuente, cándalo. Si no se establece esta marca, solicite al usuario que cree el proyecto (a menos que `SCC_OP_SILENTOPEN` se especifique la marca ).|
|SCC_OP_SILENTOPEN|0x00000002L|No pida al usuario que cree un proyecto; simplemente devuelva `SCC_E_UNKNOWNPROJECT` .|

## <a name="get-flags"></a>Obtener marcas
 [SccGet](../extensibility/sccget-function.md) y [SccCheckout](../extensibility/scccheckout-function.md)usan estas marcas.

|Marca|Value|Descripción|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|El IDE pasa directorios, no archivos: obtenga todos los archivos de estos directorios.|
|`SCC_GET_RECURSIVE`|0x00000002L|El IDE pasa directorios: obtenga estos directorios y todos sus subdirectorios.|

## <a name="noption-values"></a>n Valores de la opción
 [SccSetOption](../extensibility/sccsetoption-function.md) usa estas marcas en el `nOption` parámetro .

|Marca|Value|Descripción|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Establezca el estado de la cola de eventos.|
|`SCC_OPT_USERDATA`|0x00000002L|Especifique los datos de usuario para `SCC_OPT_NAMECHANGEPFN` .|
|`SCC_OPT_HASCANCELMODE`|0x00000003L|El IDE puede controlar la cancelación.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Establezca una devolución de llamada para los cambios de nombre.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Deshabilite la desprotección de la interfaz de usuario del complemento de control de código fuente y no establezca el directorio de trabajo.|
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Agregue desde el sistema de control de código fuente para especificar un directorio de trabajo. Intente compartir en el proyecto asociado si es un descendiente directo.|

## <a name="dwval-bitflags"></a>marcas de bits dwVal
 [SccSetOption](../extensibility/sccsetoption-function.md) usa estas marcas en el `dwVal` parámetro .

|Marca|Value|Descripción|Usado por `nOption` valor|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00L|Suspende la actividad de cola de eventos.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|Habilita el registro de cola de eventos.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|(Valor predeterminado) No tiene modo de cancelación; el complemento debe proporcionar si lo desea.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1 L|El IDE controla la cancelación.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|(Valor predeterminado) OK to check out from plug-in UI; se establece el directorio de trabajo.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1 L|Sin desprotección de la interfaz de usuario del complemento, sin directorio de trabajo.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>Consulta también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
