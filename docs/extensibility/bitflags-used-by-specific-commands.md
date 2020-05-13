---
title: Bitflags Utilizados por Comandos Específicos (Bitflags) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740012"
---
# <a name="bitflags-used-by-specific-commands"></a>Bitflags utilizados por comandos específicos
El comportamiento de varias funciones de la API de complemento de Control de código fuente se puede modificar estableciendo uno o varios bits en un único valor. Estos valores se conocen como bitflags. Los distintos bitflags utilizados por la API de complemento de Control de código fuente se detallan aquí, agrupados por la función que los utiliza.

## <a name="checked-out-flag"></a>Bandera desprotegida
 Este indicador se puede establecer para [SccAdd](../extensibility/sccadd-function.md) o [SccCheckin](../extensibility/scccheckin-function.md).

|Marca|Value|Descripción|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|Mantenga el archivo desprotegido.|

## <a name="add-flags"></a>Añadir banderas
 Estos indicadores son utilizados por el [SccAdd](../extensibility/sccadd-function.md).

|Marca|Value|Descripción|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|Se espera que el complemento de control de código fuente detecte automáticamente si el archivo es de texto o binario.|
|`SCC_FILETYPE_TEXT`|0x01|El tipo de archivo es texto.|
|`SCC_FILETYPE_BINARY`|0x04|El tipo de archivo es binario. **Nota:** `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY` y las banderas son mutuamente excluyentes.   Ajuste exactamente uno o ninguno.|
|`SCC_ADD_STORELATEST`|0x02|Almacene solo la versión más reciente (sin deltas).|

## <a name="diff-flags"></a>Banderas Diff
 [El SccDiff](../extensibility/sccdiff-function.md) utiliza estos indicadores para definir el ámbito de una operación diff. Las `SCC_DIFF_QD_xxx` banderas son mutuamente excluyentes. Si se especifica alguno de ellos, no se debe proporcionar ningún comentario visual. En un "diff rápido" (QD), el plug-in no determina cómo el archivo es diferente, sólo si es diferente. Si no se especifica ninguna de estas marcas, se realiza una "diferencia visual"; se calculan y muestran las diferencias de archivo detalladas. Si no se admite el QD solicitado, el complemento pasa al siguiente mejor. Por ejemplo, si el IDE solicita una suma de comprobación y el complemento no lo admite, el complemento realiza una comprobación de contenido completo (aún mucho más rápido que una pantalla visual).

|Marca|Value|Descripción|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|Ignore las diferencias de mayúsculas y minúsculas.|
|`SCC_DIFF_IGNORESPACE`|0x0004|Ignore las diferencias de espacio en blanco. **Nota:**  Las `SCC_DIFF_IGNORECASE` `SCC_DIFF_IGNORESPACE` marcas y son marcas de bits opcionales.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD comparando todo el contenido del archivo.|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD por suma de comprobación.|
|`SCC_DIFF_QD_TIME`|0x0040|QD por marca de fecha/hora del archivo.|
|`SCC_DIFF_QUICK_DIFF`|0x0070|Esta es una máscara usada para marcar todos los bitflags QD. No debe pasarse a una función; los tres bitflags QD son mutuamente excluyentes. QD siempre significa que no se muestra ninguna interfaz de usuario.|

## <a name="populatelist-flag"></a>Marca PopulateList
 Este indicador es utilizado por el `fOptions` [SccPopulateList](../extensibility/sccpopulatelist-function.md) en el parámetro.

|Marca|Value|Descripción|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|El IDE pasa directorios, no archivos.|

## <a name="populatedirlist-flags"></a>Marcas PopulateDirList
 Estos indicadores son utilizados por el `fOptions` [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) en el parámetro.

|Valor de la opción|Value|Descripción|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|Examine solo un nivel de directorios para directorios (este es el valor predeterminado).|
|SCC_PDL_RECURSIVE|0x0001|Examine recursivamente todos los directorios de cada directorio dado.|
|SCC_PDL_INCLUDEFILES|0x0002|Incluya los nombres de archivo en el proceso de examen.|

## <a name="openproject-flags"></a>Banderas OpenProject
 Estos indicadores son utilizados por el `dwFlags` [SccOpenProject](../extensibility/sccopenproject-function.md) en el parámetro.

|Valor de la opción|Value|Descripción|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|Si project no existe en el control de código fuente, créelo. Si no se establece esta marca, solicite `SCC_OP_SILENTOPEN` al usuario que cree el proyecto (a menos que se especifique flag).|
|SCC_OP_SILENTOPEN|0x00000002L|No pida al usuario que cree un proyecto; sólo `SCC_E_UNKNOWNPROJECT`volver .|

## <a name="get-flags"></a>Obtener banderas
 Estos indicadores los usan [SccGet](../extensibility/sccget-function.md) y [SccCheckout](../extensibility/scccheckout-function.md).

|Marca|Value|Descripción|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|El IDE pasa directorios, no archivos: obtener todos los archivos en estos directorios.|
|`SCC_GET_RECURSIVE`|0x00000002L|El IDE pasa directorios: obtenga estos directorios y todos sus subdirectorios.|

## <a name="noption-values"></a>nValores de la opción
 Estos indicadores son utilizados por el `nOption` [SccSetOption](../extensibility/sccsetoption-function.md) en el parámetro.

|Marca|Value|Descripción|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Establezca el estado de la cola de eventos.|
|`SCC_OPT_USERDATA`|0x00000002L|Especifique los `SCC_OPT_NAMECHANGEPFN`datos de usuario para .|
|`SCC_OPT_HASCANCELMODE`|0x00000003L|El IDE puede controlar la cancelación.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Establezca una devolución de llamada para los cambios de nombre.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Deshabilite la desprotección de la interfaz de usuario del complemento de control de código fuente y no establezca el directorio de trabajo.|
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Agregar desde el sistema de control de código fuente para especificar un directorio de trabajo. Intente compartir en el proyecto asociado si es un descendiente directo.|

## <a name="dwval-bitflags"></a>dwVal bitflags
 Estos indicadores son utilizados por el `dwVal` [SccSetOption](../extensibility/sccsetoption-function.md) en el parámetro.

|Marca|Value|Descripción|Utilizado `nOption` por valor|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00L|Suspende la actividad de la cola de eventos.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|Habilita el registro de la cola de eventos.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|(Predeterminado) No tiene modo de cancelación; plug-in debe suministrarse si lo desea.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1 L|IDE controla la cancelación.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|(Predeterminado) Ok para desproteger desde la interfaz de usuario del complemento; directorio de trabajo.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1 L|Sin desprotección de la interfaz de usuario del plug-in, sin directorio de trabajo.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
