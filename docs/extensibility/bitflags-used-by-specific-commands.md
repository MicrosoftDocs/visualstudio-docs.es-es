---
title: Marcadores de bits utilizado por determinados comandos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3bc59c79e0f047cc7880332c4c23643ab2136c86
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="bitflags-used-by-specific-commands"></a>Marcadores de bits utilizada por los comandos específicos
El comportamiento de un número de funciones de la API de complementos de Control de código fuente puede modificarse estableciendo uno o más bits en un solo valor. Estos valores se conocen como marcadores de bits. Los distintos marcadores de bits utilizadas por la API de complemento de Control de origen, que se detallan en este caso, agrupados por la función que los usa.  
  
## <a name="checked-out-flag"></a>Desprotege marca  
 Esta marca se puede establecer para cada uno el [SccAdd](../extensibility/sccadd-function.md) o [SccCheckin](../extensibility/scccheckin-function.md).  
  
|Marcar|Valor|Descripción|  
|----------|-----------|-----------------|  
|`SCC_KEEP_CHECKEDOUT`|0 x 1000|Mantener el archivo desprotegido.|  
  
## <a name="add-flags"></a>Agregar marcas  
 Estas marcas se usan por el [SccAdd](../extensibility/sccadd-function.md).  
  
|Marcar|Valor|Descripción|  
|----------|-----------|-----------------|  
|`SCC_FILETYPE_AUTO`|0 x 00|Se espera el complemento de control de código fuente para detectar automáticamente si el archivo es texto o binario.|  
|`SCC_FILETYPE_TEXT`|0 x 01|Tipo de archivo es texto.|  
|`SCC_FILETYPE_BINARY`|0x04|Tipo de archivo es binario. **Nota:** `SCC_FILETYPE_TEXT` y `SCC_FILETYPE_BINARY` marcas son mutuamente excluyentes.   Establezca exactamente una o ninguna de ellas.|  
|`SCC_ADD_STORELATEST`|0 x 02|Almacenar la versión más reciente solo (ninguna deltas).|  
  
## <a name="diff-flags"></a>Marcas de comparación  
 El [SccDiff](../extensibility/sccdiff-function.md) utiliza estas marcas para definir el ámbito de una operación de comparación. La `SCC_DIFF_QD_xxx` marcas son mutuamente excluyentes. Si se especifica cualquiera de ellas, ninguna información visual es que se proporciona. En un "rápida diff" (PC), el complemento no determina cómo el archivo es diferente, sólo si es diferente. Si ninguna de estas marcas se especificaron, que se realiza una "diferencia visual"; se calcula y se muestran las diferencias de archivo detallada. Si no se admite el PC solicitado, el complemento se mueve a la siguiente mejor. Por ejemplo, si el IDE solicita una suma de comprobación y el complemento no lo admite, el complemento no un contenido completo Compruebe (todavía mucho más rápido que una presentación visual).  
  
|Marcar|Valor|Descripción|  
|----------|-----------|-----------------|  
|`SCC_DIFF_IGNORECASE`|0x0002|Ignorar las diferencias de mayúsculas.|  
|`SCC_DIFF_IGNORESPACE`|0x0004|Omitir las diferencias de espacio en blanco. **Nota:** el `SCC_DIFF_IGNORECASE` y `SCC_DIFF_IGNORESPACE` marcas son marcadores de bits opcional.|  
|`SCC_DIFF_QD_CONTENTS`|0x0010|PC comparando el contenido completo del archivo.|  
|`SCC_DIFF_QD_CHECKSUM`|0x0020|PC por la suma de comprobación.|  
|`SCC_DIFF_QD_TIME`|0x0040|PC con la marca de fecha y hora de archivo.|  
|`SCC_DIFF_QUICK_DIFF`|0x0070|Se trata de una máscara que se utiliza para comprobar los marcadores de bits de PC. No se debe pasar a una función; los tres marcadores de bits de PC son mutuamente excluyentes. PC siempre no significa ninguna pantalla de interfaz de usuario.|  
  
## <a name="populatelist-flag"></a>Marca de PopulateList  
 Esta marca se usa por la [SccPopulateList](../extensibility/sccpopulatelist-function.md) en el `fOptions` parámetro.  
  
|Marcar|Valor|Descripción|  
|----------|-----------|-----------------|  
|`SCC_PL_DIR`|0x00000001L|El IDE está pasando directorios, no archivos.|  
  
## <a name="populatedirlist-flags"></a>Marcas de PopulateDirList  
 Estas marcas se usan por el [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) en el `fOptions` parámetro.  
  
|Valor de la opción|Valor|Descripción|  
|------------------|-----------|-----------------|  
|SCC_PDL_ONELEVEL|0x0000|Examinar un solo nivel de directorios para directorios (es decir, el valor predeterminado).|  
|SCC_PDL_RECURSIVE|0 x 0001|Recursivamente examine todos los directorios en cada directorio determinado.|  
|SCC_PDL_INCLUDEFILES|0x0002|Incluir nombres de archivo en el proceso de examen.|  
  
## <a name="openproject-flags"></a>Marcas de OpenProject  
 Estas marcas se usan por el [SccOpenProject](../extensibility/sccopenproject-function.md) en el `dwFlags` parámetro.  
  
|Valor de la opción|Valor|Descripción|  
|------------------|-----------|-----------------|  
|SCC_OP_CREATEIFNEW|0x00000001L|Si el proyecto no existe en el control de código fuente, créela. Si no se establece esta marca, pida al usuario para el proyecto para crear (a menos que `SCC_OP_SILENTOPEN` se especifica la marca).|  
|SCC_OP_SILENTOPEN|0x00000002L|No avisar al usuario para crear un proyecto; valor devuelto `SCC_E_UNKNOWNPROJECT`.|  
  
## <a name="get-flags"></a>Obtener marcas  
 Estas marcas se usan por el [SccGet](../extensibility/sccget-function.md) y [SccCheckout](../extensibility/scccheckout-function.md).  
  
|Marcar|Valor|Descripción|  
|----------|-----------|-----------------|  
|`SCC_GET_ALL`|0x00000001L|El IDE está pasando directorios, no archivos: obtener todos los archivos de estos directorios.|  
|`SCC_GET_RECURSIVE`|0x00000002L|El IDE está pasando directorios: obtener estos directorios y todos sus subdirectorios.|  
  
## <a name="noption-values"></a>Valores de nOption  
 Estas marcas se usan por el [SccSetOption](../extensibility/sccsetoption-function.md) en el `nOption` parámetro.  
  
|Marcar|Valor|Descripción|  
|----------|-----------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Establecer el estado de la cola de eventos.|  
|`SCC_OPT_USERDATA`|0x00000002L|Especificar los datos de usuario para `SCC_OPT_NAMECHANGEPFN`.|  
|`SCC_OPT_HASCANCELMODE`|0x00000003L|El IDE puede controlar la cancelación|  
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Establece una devolución de llamada para los cambios de nombre.|  
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Deshabilitar la desprotección de interfaz de usuario del complemento de control de código fuente y no se establece el directorio de trabajo.|  
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Agregar desde el sistema de control de código fuente para especificar un directorio de trabajo. Intente compartir en el proyecto asociado si es un descendiente directo.|  
  
## <a name="dwval-bitflags"></a>dwVal marcadores de bits  
 Estas marcas se usan por el [SccSetOption](../extensibility/sccsetoption-function.md) en el `dwVal` parámetro.  
  
|Marcar|Valor|Descripción|Utilizado por `nOption` valor|  
|----------|-----------|-----------------|-----------------------------|  
|`SCC_OPT_EQ_DISABLE`|0x00L|Suspende la actividad de la cola de eventos.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_EQ_ENABLE`|0x01L|Habilita el registro de cola de eventos.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_HCM_NO`|0L|(Valor predeterminado) No tiene ningún modo de cancelar; complemento debe proporcionar si lo desea.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_HCM_YES`|1L|IDE controla la cancelación.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_SCO_NO`|0L|(Valor predeterminado) ¿Confirma que desea extraer del repositorio de interfaz de usuario de complemento; se establece el directorio de trabajo.|`SCC_OPT_SCCCHECKOUTONLY`|  
|`SCC_OPT_SCO_YES`|1L|Ningún complemento desprotección de interfaz de usuario, no hay directorio de trabajo.|`SCC_OPT_SCCCHECKOUTONLY`|  
  
## <a name="see-also"></a>Vea también  
 [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)